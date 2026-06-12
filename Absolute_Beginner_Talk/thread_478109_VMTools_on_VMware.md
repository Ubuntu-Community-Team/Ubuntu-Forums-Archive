---
title: "VMTools on VMware"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-19
I have NO idea how to install VMTools on VMware server.
Can someone give me a step by step on how to do this?

---

### Post by jackmc on 2007-06-19
Start up your VM, when the guest os has loaded (xp in my case)  click VM => Install VMware tools.

---

### Post by dannymichel on 2007-06-19
On this part 
```
Run the installer:

sudo vmware-install.pl


```
Of this tutorial
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)
I keep getting command not forund
```
   1.
      danny@danny-desktop:~/Desktop/vmware-server-distrib$ ls
   2.
      bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl  vmware-vix
   3.
      danny@danny-desktop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl uninstall
   4.
      VMware Server 1.0.3 build-44356 for Linux installer
   5.
      Usage: ./vmware-install.pl [[-][-]d[efault]]
   6.
      default: Automatically answer questions with the proposed answer.
   7.
       
   8.
       
   9.
      danny@danny-desktop:~/Desktop/vmware-server-distrib$ head -n 50 ./vmware-install.pl
  10.
      #!/usr/bin/perl -w
  11.
      # If your copy of perl is not in /usr/bin, please adjust the line above.
  12.
      #
  13.
      # Copyright 1998 VMware, Inc.  All rights reserved.
  14.
      #
  15.
      # Tar package manager for VMware
  16.
       
  17.
      use strict;
  18.
       
  19.
      # Needed to access $Config{...}, the Perl system configuration information.
  20.
      use Config;
  21.
       
  22.
      # Constants
  23.
      my $cInstallerFileName = 'vmware-install.pl';
  24.
      my $cModuleUpdaterFileName = 'install.pl';
  25.
      my $cInstallerDir = './installer';
  26.
      my $cStartupFileName = $cInstallerDir . '/services.sh';
  27.
      my $cRegistryDir = '/etc/vmware';
  28.
      my $cInstallerMainDB = $cRegistryDir . '/locations';
  29.
      my $cInstallerObject = $cRegistryDir . '/installer.sh';
  30.
      my $cConfFlag = $cRegistryDir . '/not_configured';
  31.
      my $gDefaultAuthdPort = 902;
  32.
      my $cServices = '/etc/services';
  33.
      my $cMarkerBegin = "# Beginning of the block added by the VMware software\n";
  34.
      my $cMarkerEnd = "# End of the block added by the VMware software\n";
  35.
       
  36.
      # External helper programs
  37.
      my %gHelper;
  38.
       
  39.
      # Has the uninstaller been installed?
  40.
      my $gIsUninstallerInstalled;
  41.
       
  42.
      # BEGINNING OF THE SECOND LIBRARY FUNCTIONS
  43.
      # Global variables
  44.
      my $gRegistryDir;
  45.
      my $gStateDir;
  46.
      my $gInstallerMainDB;
  47.
      my $gInstallerObject;
  48.
      my $gConfFlag;
  49.
      my $gUninstallerFileName;
  50.
      my $gConfigurator;
  51.
       
  52.
      my %gDBAnswer;
  53.
      my %gDBFile;
  54.
      my %gDBDir;
  55.
      my %gDBLink;
  56.
      my %gDBMove;
  57.
       
  58.
      # Load the installer database
  59.
      sub db_load {
  60.
      danny@danny-desktop:~/Desktop/vmware-server-distrib$ 
```
[http://pastebin.com/931804](http://pastebin.com/931804)

---

### Post by dannymichel on 2007-06-23
> **jackmc said:**
> Start up your VM, when the guest os has loaded (xp in my case)  click VM => Install VMware tools.
Actually. 
I found the fix.
That helped me a lot BTW.
Easy enough.
Is there a way to give my guest OS the same mac address as my comp?

---

### Post by dannymichel on 2007-06-23
You have any idea how I can give my guest OS the same MAC address as my motherboard? I am unable to connect on the internet on my Virtual Machine as my college manually accepts EVERY MAC address. I was wondering if there was a way to give my guest OS the same MAC address as my MOBO for that reason.

---

