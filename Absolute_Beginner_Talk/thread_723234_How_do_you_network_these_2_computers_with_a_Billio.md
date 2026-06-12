---
title: "How do you network these 2 computers with a Billion BiPAC 7420GL?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by scrapmetal on 2008-03-13
QUESTION 1 : How do you network these 2 computers with a Billion BiPAC 7420GL so they can see each others hard drives etc. and exchange files/backups and share resources (printers/ scanners?

1. I have searched all the forum - self help areas I can find, but realy need a step by step instruction guide to complete this current quest for enlightenment, before embarking on setting up a server unit for my local community to access.

PLEASE NOTE: Due to accident inducing brain injury, I now have to function on remaining IQ, as short, and hence long term memory is of limited use to knowledge acquired after 2002. Thank the powers that be for hibernate on Ubuntu.
ALSO: Ubuntu and Kubuntu have been a brilliant boom to my humanity/self esteem. Thank you to every one involved in educating me to this point. I just have to do my bit to spread the logical conclusion to others. (Ubuntu and Kubuntu is easy to do on sole machines with internet connection, so keep spreading the word).

2. I am using a Billion BiPAC 7420GL [ADSL2+ (running at ADSL speeds due to exchange limitations) router 10/100 (4 ports) Wireless 54 Bps (not activated, Ariel disconnected now) firewall?

3. Internet Service Provider &#8211; iinet.com.au. (no problems here, I just put this in for Australian newbies like myself to read, no promotion intended, or implied).

4. Internet/broadband: working on both machines.

5. Have pinged both computers from the other successfully.

Computer 1's Hard drive has been allocated 50% each for each operating system, set XP up first with Kubuntu to be loaded second. Now find that I need to scrap XP and reload it due to the drive donation being stuck on G:/ instead of going back to C:/ and Direct X corruption in XP. Makes the partner real grumpy as she just wants it to work for her games (no online service required by her, in XP, for now!)

QUESTION 2 : How do you do a fresh load of XP Pro SP2 (on CD), without damaging GRUB or Kubuntu?

Computer 2 has a hard drive for XP, and the other for Ubuntu based operating systems. All hard drives are set to 150 throughput only, now while setting systems up. Will change this to 300 if advised that it  is safe to do so.

QUESTION 3 : Is safe to enable SATA II 300 on hard drives?

NOTE: ISP connection backup unit: Dynalink ADSL Router/modem. Model &#8211; RTA 220. (not tested yet as Billion has not failed, and I have not learnt the Dynalink setup procedure yet.

Computer 1:
Mother board - GigiByte model no: GA-K8VT890-9 ,AMD 3200+, 2 Gig RAM, Hard Drive: 320 GB, [restricted to 150], Optical Drive DVD-CD-RW Combo, Pioneer, Floppy Drive, Monitor,LCD Chimel wide screan, Keyboard-101 extended, Mouse-Logiteck 3 button, with scroll wheel Cord-less, Video Camera - Logiteck auto-focus, with built in microphone. [USB, Skype usage], Headset/Microphone- KOSS with boom microphone, Printer - Hewlett Packard HP PSC 1410 all-in-one.
SOFTWARE;
Duel boot loader: GRUB (Linux)
Operating System: 1. Microsoft Windows XP Professional Edition [Games Only, internet access via hardware configuration will be activated when and if requested (I prefer to do away with XP completely from this machine, and as soon as possible, 'ADMINISTRATOR') ]
Operating System:2. Kubuntu 7.10 (i386) KDE, Graphical User Interface, default load [Usage = Work/Production] 

Computer 2: Administrator's computer, IE: mine)
Mother board - GigaByte model no: GA-M61P-S3, nv6100, ATX, Duel Raid, Duel DDR II 800, VGA, PCIx16, SATA-II, DVI. Sound Integrated 5.1 Channel (Audio). Central Processing Unit - AMD Athlon 64 X2 Duel Core 3800+, Random access memory - 2 Gig - Geil. Video Card - Nvidea 7300GS 128mb. Hard Drive: 2 x Western Digital - WD3200AAKS SATAII/300, 320 GB, 16 Mb Cache (7200RPM) [restricted to 150, NOW, WHY?], Optical Drive DVD-CD-RW Combo Pioneer, 5 in 1 card reader: CF MD, SM/XD SD/MMC 1x USB2. Floppy Drive. Keyboard - 101. Mouse -  A4 Tech corded. Monitor - Samsung &#8211;940 &#8211; Black, 19&#8221;, LCD, 8ms, 700:1 Contrast, Analog, Ultra Narrow Bezel. Am trying to set up a Hewlett Packard ScanJet 5200C to work still, any suggestions?
SOFTWARE;
Multi boot loader: GRUB (Linux)
Operating System 1. Microsoft Windows, XP Professional Edition  [Games Only, no internet access via hardware denial configuration]
Operating System 2. Ubuntu (Gutsy Gibbon 7.1). i386 &#8211; Gnome GUI (English) [Work/Production]
Operating System 3. Ubuntu (Gutsy Gibbon 7.1). AMD64 - GNOME & KDE 4.0 GUI  (currently KDE usage) [Play/Production/Experimental]

QUESTION 4 : Have I complicated matters to much with "operating system 3" as my primary usage platform, for setting up a working network. And should I revert to "operating system 2" for now. IE: To much, to fast, for a newbie beginner?

SECURITY;
Hardware firewall: Now Billion BiPAC 7420GL, if configured properly?

Thanks to all for reading this far.
I hope I have included enough detail, to enable those in the "know"' to advise me what to do next.
I will not be able to respond for about 6 days to any replies, as I have to travel a ways, to undertake some body and brain work of my own, to keep this unit functioning.
Looking forward to catching up on this thread upon my return.

:)--Give an extra smile to someone today, they are free, but can put joy into any person, and they are contagious!--:)

---

### Post by diablo75 on 2008-03-13
> **scrapmetal said:**
> QUESTION 1 : How do you network these 2 computers with a Billion BiPAC 7420GL so they can see each others hard drives etc. and exchange files/backups and share resources (printers/ scanners?

1. I have searched all the forum - self help areas I can find, but realy need a step by step instruction guide to complete this current quest for enlightenment, before embarking on setting up a server unit for my local community to access.

PLEASE NOTE: Due to accident inducing brain injury, I now have to function on remaining IQ, as short, and hence long term memory is of limited use to knowledge acquired after 2002. Thank the powers that be for hibernate on Ubuntu.
ALSO: Ubuntu and Kubuntu have been a brilliant boom to my humanity/self esteem. Thank you to every one involved in educating me to this point. I just have to do my bit to spread the logical conclusion to others. (Ubuntu and Kubuntu is easy to do on sole machines with internet connection, so keep spreading the word).

2. I am using a Billion BiPAC 7420GL [ADSL2+ (running at ADSL speeds due to exchange limitations) router 10/100 (4 ports) Wireless 54 Bps (not activated, Ariel disconnected now) firewall?

3. Internet Service Provider – iinet.com.au. (no problems here, I just put this in for Australian newbies like myself to read, no promotion intended, or implied).

4. Internet/broadband: working on both machines.

5. Have pinged both computers from the other successfully.

Computer 1's Hard drive has been allocated 50% each for each operating system, set XP up first with Kubuntu to be loaded second. Now find that I need to scrap XP and reload it due to the drive donation being stuck on G:/ instead of going back to C:/ and Direct X corruption in XP. Makes the partner real grumpy as she just wants it to work for her games (no online service required by her, in XP, for now!)

QUESTION 2 : How do you do a fresh load of XP Pro SP2 (on CD), without damaging GRUB or Kubuntu?

Computer 2 has a hard drive for XP, and the other for Ubuntu based operating systems. All hard drives are set to 150 throughput only, now while setting systems up. Will change this to 300 if advised that it  is safe to do so.

QUESTION 3 : Is safe to enable SATA II 300 on hard drives?

NOTE: ISP connection backup unit: Dynalink ADSL Router/modem. Model – RTA 220. (not tested yet as Billion has not failed, and I have not learnt the Dynalink setup procedure yet.

Computer 1:
Mother board - GigiByte model no: GA-K8VT890-9 ,AMD 3200+, 2 Gig RAM, Hard Drive: 320 GB, [restricted to 150], Optical Drive DVD-CD-RW Combo, Pioneer, Floppy Drive, Monitor,LCD Chimel wide screan, Keyboard-101 extended, Mouse-Logiteck 3 button, with scroll wheel Cord-less, Video Camera - Logiteck auto-focus, with built in microphone. [USB, Skype usage], Headset/Microphone- KOSS with boom microphone, Printer - Hewlett Packard HP PSC 1410 all-in-one.
SOFTWARE;
Duel boot loader: GRUB (Linux)
Operating System: 1. Microsoft Windows XP Professional Edition [Games Only, internet access via hardware configuration will be activated when and if requested (I prefer to do away with XP completely from this machine, and as soon as possible, 'ADMINISTRATOR') ]
Operating System:2. Kubuntu 7.10 (i386) KDE, Graphical User Interface, default load [Usage = Work/Production] 

Computer 2: Administrator's computer, IE: mine)
Mother board - GigaByte model no: GA-M61P-S3, nv6100, ATX, Duel Raid, Duel DDR II 800, VGA, PCIx16, SATA-II, DVI. Sound Integrated 5.1 Channel (Audio). Central Processing Unit - AMD Athlon 64 X2 Duel Core 3800+, Random access memory - 2 Gig - Geil. Video Card - Nvidea 7300GS 128mb. Hard Drive: 2 x Western Digital - WD3200AAKS SATAII/300, 320 GB, 16 Mb Cache (7200RPM) [restricted to 150, NOW, WHY?], Optical Drive DVD-CD-RW Combo Pioneer, 5 in 1 card reader: CF MD, SM/XD SD/MMC 1x USB2. Floppy Drive. Keyboard - 101. Mouse -  A4 Tech corded. Monitor - Samsung –940 – Black, 19”, LCD, 8ms, 700:1 Contrast, Analog, Ultra Narrow Bezel. Am trying to set up a Hewlett Packard ScanJet 5200C to work still, any suggestions?
SOFTWARE;
Multi boot loader: GRUB (Linux)
Operating System 1. Microsoft Windows, XP Professional Edition  [Games Only, no internet access via hardware denial configuration]
Operating System 2. Ubuntu (Gutsy Gibbon 7.1). i386 – Gnome GUI (English) [Work/Production]
Operating System 3. Ubuntu (Gutsy Gibbon 7.1). AMD64 - GNOME & KDE 4.0 GUI  (currently KDE usage) [Play/Production/Experimental]

QUESTION 4 : Have I complicated matters to much with "operating system 3" as my primary usage platform, for setting up a working network. And should I revert to "operating system 2" for now. IE: To much, to fast, for a newbie beginner?

SECURITY;
Hardware firewall: Now Billion BiPAC 7420GL, if configured properly?

Thanks to all for reading this far.
I hope I have included enough detail, to enable those in the "know"' to advise me what to do next.
I will not be able to respond for about 6 days to any replies, as I have to travel a ways, to undertake some body and brain work of my own, to keep this unit functioning.
Looking forward to catching up on this thread upon my return.

:)--Give an extra smile to someone today, they are free, but can put joy into any person, and they are contagious!--:)

Question 1:  If I understand correctly, you have a DSL modem and a router attached to that modem, with two computers attached to the router, and they can ping each other.

The short, GUI based method for sharing files is to right click on a file or folder, which will bring up a little menu, and then you click "Share folder", and select SMB/Samba as your protocol.  Though, this isn't very bullet proof, I don't think.  Here is a thread that will show you how to set up a Samba share:

[http://ubuntuforums.org/showthread.php?t=76647](http://ubuntuforums.org/showthread.php?t=76647)

Question 2:  You want to install Windows AFTER ubuntu.  From what I've read, you'll need to shrink your ext3 partition to make space for a new NTFS partition for Windows to be installed on.  After install, Grub will be overwritten by windows and you have to reinstall it using an Ubuntu Live CD.  Here are two useful threads I've found about this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=384355](http://ubuntuforums.org/showthread.php?t=384355)

Question 3:  I couldn't tell ya, but it sounds like a BIOS feature.  I would enable it and if your computer doesn't want to boot, disable it.  I doubt it would do any damage to the data on your hard drive to just try it out and see if it works.  The only thing your changing is whether or not you want your motherboard to support that particular bandwidth speed.  And if the hard drive supports it, everything should just work fine.

Question 4:  No, you haven't complicated things...much  ;)  Though it is possible to have both Gnome and KDE installed on the same system.  Switching back and forth between KDE and Gnome is done at login, by changing your "session" preference.  Other window managers, like fluxbox, icewm and xfce can also be installed and switched if you would like.

---

### Post by scrapmetal on 2008-03-20
Thank you diablo75, so very thorough in explanation, even I can understand it all.. I will go through the stages now and will post the results for others who seek the same type of information.

Note: The hard drives have a jumper pin connection on the back of them. They come default set to 150 through put. I can change these to 300 (SATA-II , I think?) Both mother boards support SATA-II so will give it a go and check if  BIO's  change is required. I did not think to check BIO's.

A big **_THANK YOU_ **for putting me on the correct path in learning more.:)

---

### Post by scrapmetal on 2008-03-21
It now appears that I was pinging each machine in **_a loop_**:mad: ie: I was pinging between each computer and the router (Billion). Very:( 

QUESTION 1: Do you have to have a microsoft home network running before running**_ Samba_**, because I did not?:confused:

Note: here is a video tutorial that may help others with **_Samba_**
[http://static.screencasts.ubuntu.com/20070704_samba_filesharing](http://static.screencasts.ubuntu.com/20070704_samba_filesharing)

QUESTION 2: Computer 1 has now done the following, and I am pretty sure it is some thing I have done and not the programs involved. What it is, I have not a clue.

I have no idea why this has happened?
It started with a normal update, failure ensured, and no option was given to attempt the updates again. Source was international, not Australia as it probably should have been.

So here is what information my be helpful from computer1to solve this mystery. **Very**:confused:

KDE add/remove programs will not work it reports'


START add/remove programs REPORT:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1236060480 (LWP 5609)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb658e875 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6590201 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb679a6e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb6797f65 in ?? () from /usr/lib/libstdc++.so.6
#11 0xb6797fa2 in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb67980ca in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0x0812b916 in ?? ()
#14 0x0812be8a in ?? ()
#15 0x0812bee8 in ?? ()
#16 0x0812c735 in ?? ()
#17 0x0812a22d in ?? ()
#18 0x08114379 in ?? ()
#19 0x080951ed in ?? ()
#20 0x0807378d in ?? ()
#21 0x0807408e in ?? ()
#22 0xb6dde893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb716a8ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#24 0xb6dfe842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#25 0xb6e06258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb6d75af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb6d7791f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb753bcd2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6d08209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb6d6853b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6d1cd49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb6d901ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0xb6d8ffde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0xb6d77699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x0806f75e in ?? ()
#36 0xb657a050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0806f401 in ?? ()


END add/remove programs REPORT:

START  Synaptic Package Manager REPORT:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

END  Synaptic Package Manager  REPORT:

START Terminal command  REPORT:

Terminal command: sudo apt-get install samba

END Terminal command   REPORT:

START Database Locked – Adept Manager  REPORT:

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.

END Database Locked – Adept Manager   REPORT:


Computer 1:
Mother board - GigiByte model no: GA-K8VT890-9 ,AMD 3200+, 2 Gig RAM, Hard Drive: 320 GB, [restricted to 150], Optical Drive DVD-CD-RW Combo, Pioneer, Floppy Drive, Monitor,LCD Chimel wide screan, Keyboard-101 extended, Mouse-Logiteck 3 button, with scroll wheel Cord-less, Video Camera - Logiteck auto-focus, with built in microphone. [USB, Skype usage], Headset/Microphone- KOSS with boom microphone, Printer - Hewlett Packard HP PSC 1410 all-in-one.
SOFTWARE;
Duel boot loader: GRUB (Linux)
Operating System: 1. Microsoft Windows XP Professional Edition [Games Only, internet access via hardware configuration will be activated when and if requested (I prefer to do away with XP completely from this machine, and as soon as possible, 'ADMINISTRATOR') ]
Operating System:2. Kubuntu 7.10 (i386) KDE, Graphical User Interface, default load [Usage = Work/Production]

QUESTION 3: Internet/network? connection is dropping out intermitently upon boot to Both xp and Kubuntu (as above). Hardware connections ok, going out through billion with this computer (2) with out problems. Again it must be some thing I have done in software with Kubuntu or in attempting to set up a microsoft home network (used windoze wizard and it would not write network files to freshly formated floppy disk).:( and :confused:

Any help greatly appreciated:confused:

---

### Post by scrapmetal on 2008-03-24
Gave up trying to fix this.
Hardware, ok.
Cable connections, ok.
Re-formated the hard drive, 50% each to XP and Kubuntu.
XP has installed ok. (no network connection allowed)
Kubuntu from CD, ok.
Duel Boot, ok
Hardware again, ok.
Cable connections again, ok.
No restricted modules loaded.
No extra anything loaded.
Kubuntu auto update, problems.
Kubuntu version update, big problems.

Conclusion: Either the (setup) router / firewall / wireless (not enabled) / modem has developed a weired fault, but this computer 2. works fine. Or there is some thing weired with Kubuntu update as it reports another add/remove program needs to be terminated so it can work. There is only the default add/remove program installed.

Reported to bug fixes, the error interruptions.

Any suggestions?:mad::confused:

---

### Post by scrapmetal on 2008-04-09
Flattened hard drive, will try Debian.

---

