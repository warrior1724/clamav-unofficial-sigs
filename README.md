# clamav-unofficial-sigs
ClamAV Unofficial Signatures Updater

Github fork of the sourceforge hosted and non maintained utility.

## Description
The clamav-unofficial-sigs script provides a simple way to download, test, and update third-party signature databases provided by Sanesecurity, FOXHOLE, OITC, Scamnailer, BOFHLAND, CRDF, Porcupine, Securiteinfo, MalwarePatrol. The package also contains cron, logrotate, and man files.

### MalwarePatrol Free/Delayed list support (as of May 2015)
Usage of MalwarePatrol 2015 free clamav signatures : https://www.malwarepatrol.net
 - 1. Sign up for a free account : https://www.malwarepatrol.net/signup-free.shtml
 - 2. You will recieve an email containing your password/receipt number
 - 3. Enter the receipt number into the config malwarepatrol_receipt_code: replacing YOUR-RECEIPT-NUMBER with your receipt number from the email

### SecuriteInfo Free/Delayed list support (as of May 2015)
Usage of SecuriteInfo 2015 free clamav signatures : https://www.securiteinfo.com
 - 1. Sign up for a free account : https://www.securiteinfo.com/clients/customers/signup
 - 2. You will recieve an email to activate your account and then a followup email with your login name
 - 3. Login and navigate to your customer account : https://www.securiteinfo.com/clients/customers/account
 - 4. Click on the Installation tab
 - 5. You will need to get your unique identifier from one of the download links for manual setup, you will need your 128 character authorisation signature.
   eg. https://www.securiteinfo.com/get/signatures/bb9ktrbv30cagin7hajfa5ft6dwpvljsv7b7yob9igpv5175dew05rirq3r5kgnhbb9ktrbv30cagin7hajfa5ft6dwpvljsv7b7yob9igpv5175dew05rirq3r5kgnh/securiteinfo.hdb
   Your 128 character authorisation signature would be : bb9ktrbv30cagin7hajfa5ft6dwpvljsv7b7yob9igpv5175dew05rirq3r5kgnhbb9ktrbv30cagin7hajfa5ft6dwpvljsv7b7yob9igpv5175dew05rirq3r5kgnh
 - 6. Enter the authorisation signature into the config securiteinfo_authorisation_signature: replacing YOUR-SIGNATURE-NUMBER with your authorisation signature from the link

### Linux Malware Detect support (as of May 2015)
Usage of free Linux Malware Detect clamav signatures: https://www.rfxn.com/projects/linux-malware-detect/
 - Enabled by default, no configuration required

### Please consider a donation to http://sanesecurity.com

## Version 4.4.4 (updated 2015-06-08)
 - eXtremeSHOK.com Maintenance
 - Committed patch-1 by SecuriteInfo (clean up of SecuriteInfo databases)
 - Fixed double $surl_insecure

## Version 4.4.3 (updated 2015-05-14)
 - eXtremeSHOK.com Maintenance
 - Bugfix for SecuriteInfo not downloading by Colin Waring
 - Default will now silence ssl errors caused by ssl certificate errors
 - Config updated to 4.6 due to new varible: silence_ssl

## Version 4.4.2
 - eXtremeSHOK.com Maintenance
 - Improved config error checking
 - Config updated to 4.5, due to invalid default dbs-si value
 - Fix debug varible being present
 - Bug fix for ubuntu 14.04 with sed being aliased
 - Explicitly set bash as the shell

## Version 4.4.1
 - eXtremeSHOK.com Maintenance
 - Added error checking to detect if the config could be broken.

## Version 4.4.0
 - eXtremeSHOK.com Maintenance
 - Code refactoring: 
 - Added full support for Linux Malware Detect clamav databases
 - Config updated to 4.4

## Version 4.3.0
 - eXtremeSHOK.com Maintenance
 - Code refactoring: group and move functions to top of script
 - Complete rewrite of securiteinfo support, full support for Free/Delayed clamav by securiteinfo.com ;-P
   Note: securite info requires you to create a free account and add your authorisation code to the config.
 - Config updated to 4.3
 - Restructured Config

## Version 4.2.0
 - eXtremeSHOK.com Maintenance
 - Replace annoying si_ , mbl_,  ss_  with actual names ie. securiteinfo_ malwarepatrol_ sanesecurity_
 - Complete rewrite of malwarepatrol support, full support for Free/Delayed clamav ;-P
   Note: malware patrol requires you to create a free account and add your "purchase" code to the config.
 - More fixes to config prasing and stripping of comments and whitespace
 - Code refactoring: remove empty commands: echo "" and comment ""
 - Config version detection and enforcing

## Version 4.1.0
   - eXtremeSHOK.com Maintenance
   - Fix on default enable of foxhole medium and High false positive sources
   - grammatical corrections to some comments and log output
   - sig-boundary patch by Alan Stern
   - create intermediate monitor-ign-old.txt to prevent reading and writing of local.ign by Alan Stern

## Version 4.0.0
   - eXtremeSHOK.com Maintenance
   - Enabled all low false positive sources by default
   - Added all Sanesecurity database files
   - Disabled all med/high false positive sources by default
   - Set default configs to work out of the box on a centos system
   - Silence cron job
   - Set correct paths throughout the script
   - Updated Installation Instructions
   - Updated Paths for removal
   - Updated Default locations to reflect installation instructions
   - Fix: correctly remove comments and blanklines from config before eval
   - Remove: invalid config values (eg. EXPORT path)
   - Fix: correctly check if rsync was successful

## ORIGINAL README CONTENTS
The clamav-unofficial-sigs script and accompanying files are provided by Bill Landry
(unofficialsigs@gmail.com) under general BSD licensing guidelines.

The clamav-unofficial-sigs.tar.gz package contains script and configuration files that
provide the capability to download, test, and update the 3rd-party signature databases
provided by Sanesecurity, SecuriteInfo, MalwarePatrol, OITC, etc.

Files contained in the clamav-unofficial-sigs.tar.gz package:

1.  README - This file.  Contains basic information about script features and capabilities.

2.  CHANGELOG - This file contains the changes that have been made between script updates.

3.  LICENSE - Open-Source license to allow packaging/porting and redistribution of scripts.

4.  INSTALL - Contains detailed instructions for configuring and using scripts.

5.  clamav-unofficial-sigs.conf - This file contains all of the user configurable variable
    setting for running the "clamav-unofficial-sigs.sh" shell script.

6.  clamav-unofficial-sigs.sh - This file contains the shell scripting code necessary for
    checking for updated 3rd party clamav signature databases, downloading of databases,
    testing for valid GPG signatures and clamscan for database integrity, and finally
    implementation of updated databases.

7.  clamav-unofficial-sigs.8 - This is the script's manual page.

8.  clamav-unofficial-sigs-cron - This is the script's cron file used to support automated
    script execution at specified time intervals.

9.  clamav-unofficial-sigs-logrotate - This is the script's logrotate file, used to rotate
    and compress log files at a specified time-interval and to keep the log archives for a
    specified time-frame.

10. clamd-status.sh - A stand-alone script that can be used to run status checks against
    clamd, and can be configured to attempt to start a non-running or crashed daemon.

Script (clamav-unofficial-sigs.sh) features & capabilities:

- Checks for updated unofficial clamav signature database files, detection and download.
- GPG signature verify and clamscan integrity test updated signature databases and implement.
- Download time randomization - this help to distribute the load more evenly for the database
  host mirror sites.
- Create signature bypass entries for temporarily resolving false-positive issues with third-
  party signatures.
- Ability to report which mirror site a download came from (good to know if there are issues).
- Reports if a downloaded database is actually different than the running copy.
- Status check to determine if clamd is running, and if enabled, ability to attemtp to start
  if detected not running.
- Ability to control script output, which is good when run via cron.
- Ability to create a backup copy of a running database before replacing it.
- Currently provides support for six different unofficial clamav database providers:
  Sanesecurity, SecuriteInfo, MalwarePatrol, OITC, etc.
- Ability to choose which database files to download and use from each provider.
- Coded to be portable across as many different OS platforms and utility versions as possible.
- Separate user configuration file, which will allow users to setup their configuration and not
  have to redo the configuration with each new script update.
- The script can hexadecimal encode (for usage) and decode (for viewing) virus signatures.
- Ability to create a hexadecimal signature database file from a clear text ascii file.
- Ability to enable scanning of a local HAM (non-spam) directory for false-positive hits from
  third-party signatures and removal of errant signatures from databases before implementing.
- Script logging can be enabled/disabled in the configuration file.
- Includes cron, manual, and logrotate files.

Script updates can be found at: https://github.com/extremeshok/clamav-unofficial-sigs

Original Script can be found at: http://sourceforge.net/projects/unofficial-sigs
