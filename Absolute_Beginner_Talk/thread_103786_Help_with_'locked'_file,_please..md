---
title: "Help with 'locked' file, please."
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2005-12-14
I have Breezy 5.10 and I noticed that I have some files in my 'File Browser' with a padlock on them.

These were files I moved from my floppy (I think) and I would appreciate it if someone would explain how to UNlock them.

Thanks.

---

### Post by migueljacq on 2005-12-14
The padlock usually means it's a permissions problem. Like read-only file in Windows.
Now: You can usually change this easily by right clicking on the file and selecting Properties, then the 'Permissions' tab and checking the boxes under 'owner' for read/write/execute.
However: some of these files are sometimes read only deliberately. So maybe make sure you know what they are, first. Most of the files outside of your home directory are owned by 'root', for a reason. I would imagine anything inside your home folder is ok to be owned by you, but best to be careful.

Miguel

---

### Post by cstudent on 2005-12-14
Miquel's advice is good, but if they are files you transferred from a floppy then you are probably OK to change the permissions on them. 

To change the owner and group of the file enter:

**sudo chown username:usergroup filename**

You would change username and group to your user name. Your group name would be the same. Of course filename would be the name of the file.

To change the owner and group of a whole folder enter:

**sudo chown -R username:usergroup /folder_path**

---

### Post by L Campbell on 2005-12-15
[QUOTE=migueljacq]The padlock usually means it's a permissions problem. Like read-only file in Windows.
Now: You can usually change this easily by right clicking on the file and selecting Properties, then the 'Permissions' tab and checking the boxes under 'owner' for read/write/execute.
However: some of these files are sometimes read only deliberately. So maybe make sure you know what they are, first. Most of the files outside of your home directory are owned by 'root', for a reason. I would imagine anything inside your home folder is ok to be owned by you, but best to be careful.

Miguel[/QUOTE]
...............

Thanks for your help.

When I got to the Permissions tab, everything was ‘grey’ and I was unable to change anything.

At the bottom it said, ‘ You are not the owner so you can’t change permissions ‘.

I have a dual boot  PC but can’t get online with Ubuntu (yet) so I have to reboot in Win98 to send messages.

The files that are locked, are the text that I copied from my Terminal, so that I could show someone what I was doing.  I moved the files from my ‘home’ to a floppy, then rebooted in Win98, opened the files in Works and copied them into my post in the forum.

When I subsequently rebooted into Ubuntu, I moved the files back, from the floppy to ‘home’.  It seems that this was when they became ‘locked’.  (at the top of my screen the words ‘read only’ appear after the file name)

I am not on a network.  Its just me, at home, using one computer, so it seems like _I_ should own everything, all the permissions, etc.       :-)

Anyway, the latest thing I tried was to move the files back, from’home’, to the floppy and then they appeared as _not_ locked.

Kind regards.

---

### Post by L Campbell on 2005-12-15
[QUOTE=cstudent]Miquel's advice is good, but if they are files you transferred from a floppy then you are probably OK to change the permissions on them. 

To change the owner and group of the file enter:

**sudo chown username:usergroup filename**

You would change username and group to your user name. Your group name would be the same. Of course filename would be the name of the file.

To change the owner and group of a whole folder enter:

**sudo chown -R username:usergroup /folder_path**[/QUOTE]

..................

Thanks for your help.

Sorry if I’m a little ‘dense’ here but the ‘ username:usergroup ‘ confuses me.

Would username be;  /home/lcampbell  ?  for example.

Also, I’m totally lost with ‘ usergroup ‘

I have a dual boot  PC but can’t get online with Ubuntu (yet) so I have to reboot in Win98 to send messages.

The files that are locked, are the text that I copied from my Terminal, so that I could show someone what I was doing.  I moved the files from my ‘home’ to a floppy, then rebooted in Win98, opened the files in Works and copied them into my post in the forum.

When I subsequently rebooted into Ubuntu, I moved the files back, from the floppy to ‘home’.  It seems that this was when they became ‘locked’.  (at the top of my screen the words ‘read only’ appear after the file name)

I am not on a network.  Its just me, at home, using one computer, so it seems like _I_ should own everything, all the permissions, etc.       :-)

Anyway, the latest thing I tried was to move the files back, from’home’, to the floppy and then they appeared as _not_ locked.

Kind regards

---

### Post by bscbrit on 2005-12-15
No, your username is probably lcampbell, or whatever name you type in when you first log on.  So for this command to work you would type:

chown lcampbell:lcampbell filename

where 'filename' is the name of the file that you wish to change.  Using the -R option changes files recursively (i.e. if you give it a directory name, it will move through that directory and all those below it change the ownership to 'lcampbell').   Make sure that this is what you want before you use it as you can easily change the permissions of files that you did not intend to change.

Incidentally, the command 'chown lcampbell:  filename' is a shorthand version of the one given above but the first one is clearer to those who are not used to using chown.

---

### Post by bscbrit on 2005-12-15
You might think that you are the only user on your system but that is not actually the case.  There are various jobs being carried out behind the scenes that all need to belong to someone or other, and the user is not often the correct choice.  Most people have heard of 'root', which is simply another system user who has God-like powers.  He can do anything to any file.  This might sound attractive for everyday use but it is not.  The system cannot prevent root from doing something stupid, whereas it will stop 'normal' users from damaging the system although they are free to do whatever they want in their own home area.
But there are lots of other 'users'.  For example, anti-virus programs, daemons and lots of other programs often have their own user names.  To see all the users of your system, try the following:

System-Administration-Users and Groups

You will be prompted for your password, which is the same password that you used to log on in the first instance.  In the bottom left corner is an option to show all users and groups.  Clicking this will show you a list of all the essential users of your system.  Do NOT change this unless you know what you are doing.  Removing an unknown user will undoubtedly stop something from working.  

Each User can belong to one or more groups, and both groups and users can have specific priviledges.  But most standard users also belong to a group of the same name.  Hence you are lcampbell:lcampbell which shows your username:groupname (which in this case are the same)

HTH (which is an abbreviation for 'hope this helps').

---

### Post by bscbrit on 2005-12-15
Ok, you mentioned that you were having a problem with your modem.  This is not an area of my expertise (I'm not quite sure what is!) but, if you are not already trying to get help in another thread, we can always try to solve this problem here.
What kind of modem have you got?  Is it a dial-up, is it serial, USB or PCI Card, what make is it etc.  Most of the information that you need is actually already sitting in the windows OS, assuming that you have the same modem working there.  It will be worthwhile writing as much information as you can find so that you do not get caught switching back and forth to find what you need when you are trying to get it working under Ubuntu.

---

### Post by L Campbell on 2005-12-15
[QUOTE=bscbrit]Ok, you mentioned that you were having a problem with your modem.  This is not an area of my expertise (I'm not quite sure what is!) but, if you are not already trying to get help in another thread, we can always try to solve this problem here.
What kind of modem have you got?  Is it a dial-up, is it serial, USB or PCI Card, what make is it etc.  Most of the information that you need is actually already sitting in the windows OS, assuming that you have the same modem working there.  It will be worthwhile writing as much information as you can find so that you do not get caught switching back and forth to find what you need when you are trying to get it working under Ubuntu.[/QUOTE]
...........
Thank you for your interest, here.  :-)

I have used Windows  for about 10 years and am comfortable finding my way around in it.

My interest in Linux began over a year ago, during which time I have tried Suse, Knoppix, Mepis,
Kubuntu, Ubuntu and a couple of others.

Despite all these systems and about 9 different modems, the _ONLY_ successful and ongoing, online experience that I have had is with Mepis (KPPP) and a SmartLink internal modem with an SL 1900 chipset.

I have posted on this and other forums and a lot of good people have offered helpful suggestions but I’m not there yet.  Most people use cable, or some other high speed connection but I want to hook up with dial-up, so I’m sure that there are more people who are knowledgeable about high speed than dial-up.

The main hang up (no pun intended) is that, after I have done the  scanModem.gz  thing and I open ModemData.txt  I have _NO_ idea what it is telling me and, when I send that information to [email]discuu@linmodems.org[/email]  I find that they have not had time to look at it.

In the meantime, I’m taking the opportunity to familiarize myself with some of the code (or would that be ‘commands’) that I need to use in ‘Terminal’.

BTW, 
HTH, in cycling parlance, refers to Hotter ‘N Hell, a 100 mile bike ride in Texas that has been attracting about 10,00 people per year, for over 20 years and the ride is in August so the temp. is 100 degrees.

From this link you will see that most my stuff has been about trying to get online:-

[http://ubuntuforums.org/search.php?searchid=2960700](http://ubuntuforums.org/search.php?searchid=2960700)

---

### Post by bscbrit on 2005-12-15
Assuming that your quote of '9 different modems' is not an exageration, do you have any that have a serial connector, rather than USB.  I always find that the old traditional serial connector or, alternatively, an ethernet connection are the easiest to set up and configure.
Internal modems are often 'winmodems' and, although support for them is improving in linux, they can still be a bit fiddly to set up. But, if you have had your existing modem working under Mepis then it should work under any linux.  Did you make note of how you did it successfully under Mepis?  (Experts always recommend that you do such things in a technical diary, but real users like ourselves tend to be too lazy until it is too late!)
Once you have the computer talking to the modem I would have thought that the rest would fall into place, although I am also a broadband user and I haven't set up a dial-up connection for about 18months or so.

This link talks about a linux driver for your particular modem

[http://www.modemsite.com/56k/smartlink.asp](http://www.modemsite.com/56k/smartlink.asp)

It might be worth a few minutes looking if this answers any of your problems.

---

### Post by bscbrit on 2005-12-15
Can you post the contents of ModemData.txt in this thread - I might be able to explain what it means, or at least point you in the direction of some answers.

---

### Post by L Campbell on 2005-12-15
[QUOTE=bscbrit]No, your username is probably lcampbell, or whatever name you type in when you first log on.  So for this command to work you would type:

chown lcampbell:lcampbell filename

where 'filename' is the name of the file that you wish to change.  Using the -R option changes files recursively (i.e. if you give it a directory name, it will move through that directory and all those below it change the ownership to 'lcampbell').   Make sure that this is what you want before you use it as you can easily change the permissions of files that you did not intend to change.

Incidentally, the command 'chown lcampbell:  filename' is a shorthand version of the one given above but the first one is clearer to those who are not used to using chown.[/QUOTE]
...........

Thanks for your help.

Unfortunately, I did not get this to work.

>>>>
lampbell@ubuntulewis:~$ chown lcampbell:lcampbell forumo.odt
chown: clchanging ownership of `forumo.odt': Operation not permitted
lcampbell@ubuntulewis:~$
<<<<<

Am I doing something wrong?

Kind regards.

---

### Post by L Campbell on 2005-12-15
[QUOTE=bscbrit]You might think that you are the only user on your system but that is not actually the case.  There are various jobs being carried out behind the scenes that all need to belong to someone or other, and the user is not often the correct choice.  Most people have heard of 'root', which is simply another system user who has God-like powers.  He can do anything to any file.  This might sound attractive for everyday use but it is not.  The system cannot prevent root from doing something stupid, whereas it will stop 'normal' users from damaging the system although they are free to do whatever they want in their own home area.
But there are lots of other 'users'.  For example, anti-virus programs, daemons and lots of other programs often have their own user names.  To see all the users of your system, try the following:

System-Administration-Users and Groups

You will be prompted for your password, which is the same password that you used to log on in the first instance.  In the bottom left corner is an option to show all users and groups.  Clicking this will show you a list of all the essential users of your system.  Do NOT change this unless you know what you are doing.  Removing an unknown user will undoubtedly stop something from working.  

Each User can belong to one or more groups, and both groups and users can have specific priviledges.  But most standard users also belong to a group of the same name.  Hence you are lcampbell:lcampbell which shows your username:groupname (which in this case are the same)

HTH (which is an abbreviation for 'hope this helps').[/QUOTE]

>>>>>>>>

YIKES !!!

That is a long list of 'others'.

Thanks for the help.

---

### Post by L Campbell on 2005-12-15
[QUOTE=bscbrit]Can you post the contents of ModemData.txt in this thread - I might be able to explain what it means, or at least point you in the direction of some answers.[/QUOTE]
>>>>>>>>>

I appreciate your help.

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_Oct_25
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 USB modem not detected.


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling

Modem candidates are at PCI_buses:  0000:01:09.0
    
Providing detail for device at  0000:01:09.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 163c:3052   Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04) (prog-if 00 [Generic])
  SubSystem 163c:3052  Smart Link Ltd. SmartLink SmartPCI562 56K Modem
	Flags: bus master, stepping, fast Back2Back, medium devsel, latency 64, IRQ 9
 Checking for IRQ 9 sharing with modem.
      XT-PIC  acpi

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 163c:3052 163c:3052 debian 2.6.12-9-386  3.4.5     i686
      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40) ,
 with slmodem-2.9.10 and later releases only licensed for Smartlink chipsets.
 
 A series maintaining a much broader license for other chipset support,
 can be downloaded from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   slmodemd-CurrentVersion.tar.gz - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and    [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)  
   

  ======= PCI_ID checking completed ====== 
 Update=2005_Oct_25
A PCMCIA CardBus is not detected on this System.

/etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-9-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.12-9-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-9-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.12-9-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-9-386 or kernel-smp-devel-2.6.12-9-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-9-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

drwxr-xr-x  2 root root 0 2005-12-01 19:07 /dev/.udevdb
There is an active UDEV file system, creating device nodes in volatile RAM.
However information from Proprietary drivers is soon to be excluded from 
the supporting /sys/ file structure.  Thus device nodes for Proprietary modem drivers
will then have to be created by bootup scripts.

 Checking for modem symbolic link support lines within /etc/udev/ files

   
For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294668.747000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[4294668.764000] audit: initializing netlink socket (disabled)
[4294725.499000] ibm_acpi: ec object not found
[4294742.605000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294742.605000] apm: overridden by ACPI.

  Beginning with Fedora 2  kernel-2.6.6-1.427, kernel-headers needed 
  for compiling drivers are provide at: /lib/modules/kernel-version/build/
  Thus upgrading above kernel 2.6.5-1.358 to 2.6.6-* is Stongly Recommended
  
  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by cstudent on 2005-12-15
[QUOTE=L Campbell]...........

Thanks for your help.

Unfortunately, I did not get this to work.

>>>>
lampbell@ubuntulewis:~$ chown lcampbell:lcampbell forumo.odt
chown: clchanging ownership of `forumo.odt': Operation not permitted
lcampbell@ubuntulewis:~$
<<<<<

Am I doing something wrong?

Kind regards.[/QUOTE]

Try it with sudo in front of the command line. Also make sure you are in the same directory as the file or you need to add the path. (ie: /home/lcampbell/downloads/forumo.opt)

**sudo chown lcampbell:lcampbell forumo.opt**

---

### Post by bscbrit on 2005-12-15
It looks like cstudent beat me to it!  However, he is correct with his advice - the omission was my mistake.  Sorry.

---

### Post by L Campbell on 2005-12-15
[QUOTE=cstudent]Try it with sudo in front of the command line. Also make sure you are in the same directory as the file or you need to add the path. (ie: /home/lcampbell/downloads/forumo.opt)

**sudo chown lcampbell:lcampbell forumo.opt**[/QUOTE]

OK, I'm on a roll here, many thanks.      :-)  :-)


lcampbell@ubuntulewis:~$ sudo mount /media/floppy
Password:
lcampbell@ubuntulewis:~$ sudo chown lcampbell:lcampbell forumt.odt
lcampbell@ubuntulewis:~$ sudo chown lcampbell:lcampbell forumo.odt
lcampbell@ubuntulewis:~$


Kind regards.

---

### Post by L Campbell on 2005-12-15
[QUOTE=bscbrit]Assuming that your quote of '9 different modems' is not an exageration, do you have any that have a serial connector, rather than USB.  I always find that the old traditional serial connector or, alternatively, an ethernet connection are the easiest to set up and configure.
Internal modems are often 'winmodems' and, although support for them is improving in linux, they can still be a bit fiddly to set up. But, if you have had your existing modem working under Mepis then it should work under any linux.  Did you make note of how you did it successfully under Mepis?  (Experts always recommend that you do such things in a technical diary, but real users like ourselves tend to be too lazy until it is too late!)
Once you have the computer talking to the modem I would have thought that the rest would fall into place, although I am also a broadband user and I haven't set up a dial-up connection for about 18months or so.

This link talks about a linux driver for your particular modem

[http://www.modemsite.com/56k/smartlink.asp](http://www.modemsite.com/56k/smartlink.asp)

It might be worth a few minutes looking if this answers any of your problems.[/QUOTE]

Hi, thanks for taking time to help here.

I’m a little surprised that you think I would need to exaggerate but it turns out that I have tried more than 9 modems, most of which are listed here:-

List of modems:-
Modular technology ext   serial port
usr Sportster            ext    serial port
Stirling                     int    PCI
Supra Max               ext    USB
Rockwell                  int 
3comm                     int
pctel                         int
conexant                   int
conexant                   int
us robotics                int

The SmartLink modem that I have in all my computers is a PCI

After doing some thinking, I do remember getting online with the external, serial port, Modular technology but it would only connect at 9,600 baud and that was with Mepis.   This SmartLink generally gets on at 50,666 baud

Mepis uses KPPP and, since you ask, “Did you make note of how you did it successfully under Mepis? “, I will admit that I did not.  Getting online with Mepis was as easy as falling off a log and I just assumed that the SmartLink modem was the answer to my dreams and that I would be able to use any type of Linux with it.  BTW, Mepis also worked perfectly for me in 3 older computers, in each of which I had installed a SmartLink modem.

When I first got Ubuntu and realize that it was not a snap to get online, I bought a Kubuntu disk, since it has KPPP but I have never been able to get online with it, either.   :-(

>>>>
Once you have the computer talking to the modem 
<<<<

Does it appear to you, from the ModemData file, that the computer is communicating with the modem?

Many times I have ‘configured’ the logon applet in Ubuntu and got the message ‘modem ready’ but when I hit the ‘query’ button, it just goes through the motions but doesn’t return any data.

When I hit the ‘connect’ button, I get ‘modem ready’, then ’initializing’ but that is as far as it ever gets.

Kind regards.

Lewis.

---

