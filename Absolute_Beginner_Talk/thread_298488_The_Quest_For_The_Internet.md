---
title: "The Quest For The Internet"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Ireclan on 2006-11-12
Well, after doing some minor fiddling in Ubuntu and skimming over the system help documentation, I have finally decided to see if I can get my dial-up modem working under Linux. The system help documentation says that I should embark upon this journey by first identifying what chipset my modem uses by typing in this series of commands at the terminal:


wget -c [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)
gunzip -c scanModem.gz > scanModem
chmod +x scanModem
sudo ./scanModem
gedit Modem/ModemData.txt


The thing is, I don't know what these commands are actually telling my OS to DO. The first line seems to request the system to fetch the package "scanModem.gz" from the web address "http://linmodems.technion.ac.il/packages/scanModem.gz". The second appears to request that the system uncompress the package "scanModem.gz". I have no idea what the fourth line does at all, but the fifth seems to be requesting that the system run the package "scanModem" with root privileges, while the sixth appears to request the system to open the document "ModemData.txt" with the program "gedit". Are these suppositions correct? If so, why would the system documentation tell me to tell the OS to fetch a package over an internet connection when I don't have one? I would really like a full interpretation of this series of commands, so I can actually learn what they mean, and not just chuck them at my OS in total ignorance.

---

### Post by goatflyer on 2006-11-12
Reading the documentation page

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

I notice the following:

> 
scanModem will scan your modem and tell you what it is and how to configure it. It will not configure it for you. But after running, you will see a number of new folders, including a 'Modem' folder. Read read1st.txt and modemdata.txt in there, and see if you modem was recognized.


I do not have a dialup modem myself, so I don't know if this is the latest and greatest instructions for setting up a dialup modem (these instructions were written from the time of Hoary).

What version of Ubuntu/Kubuntu/Xubuntu are you using?  In any case, running the scanmodem should not hurt your system, only (attempt) to detect it.  Depending on what it finds, you will use that for your next step - which would probably be locating the correct driver.

What do you find in System>Administration>Networking ?

Hope this helps :)

---

### Post by Ireclan on 2006-11-12
UPDATE


OK, I've downloaded the scanModem.gz package. What should I do next?

---

### Post by goatflyer on 2006-11-12
As the instructions said: copy it to your home directory, unzip it, chmod +x the program file, and run it using sudo.  Then read the output file ModemData.txt using whichever editor you prefer.  gedit is the default gnome (ubuntu) graphics editor.

---

### Post by gargoyle on 2006-11-12
Hi,
First I a fairly new at Ubuntu too.
You have interpreted the information fairly well.
[LIST=1]
[*]**Correct**The first line seems to request the system to fetch the package "scanModem.gz" from the web address "http://linmodems.technion.ac.il/packages/scanModem.gz".
[*]**Correct**The second appears to request that the system uncompress the package "scanModem.gz".
[gzip The data compression program]("http://www.math.utah.edu/docs/info/gzip_toc.html")*Manual on using zip*
[*]I have no idea what the fourth line does at all,
*This line is to give yourself permission to run the program.*[Using chmod]("http://www.cs.bu.edu/help/unix/using_chmod.html") Look at the link for further explanation.
[*]**Correct**the fifth seems to be requesting that the system run the package "scanModem" with root privileges
[*]**Correct**the sixth appears to request the system to open the document "ModemData.txt" with the program "gedit".
[/LIST]

*You said***If so, why would the system documentation tell me to tell the OS to fetch a package over an Internet connection when I don't have one?**
Your right why would you want to run these set of instructions.
The answer is how are you connecting to the Internet now?

**Are you using Windows?**
If so the the instruction will not work for line 1 but what you need to download the zip file and transport it to Ubuntu. How you do this irrelevant, use a floppy, burn cd or use a usb stick.
Create a folder and place the zip in it or place it on you desktop.

Then run the instruction from line 2 to the end.
You will have to change the line to reflect where you placed the zip file.
It is nice to see another person who wants to know what the commands are doing, I thought I was the only one with this desire.

I hope I cleared up for you, if in the future if you do not know what a command does just do a search on the command there a lot of sites with explanations and examples.

---

### Post by Ireclan on 2006-11-13
OK. I ran the scanModem thingy. What should I do now? I have a folder named "Modem" with a whole bunch of ".txt" files in it, which I have printed off for the conveniance of anyone wishing to help me (for some reason, Ubuntu will not let me copy the files to the CD that had scanModem.gz on it). So, how do I interpret all this new information? What should I be looking for?

---

### Post by Ireclan on 2006-11-14
I'm bumping this topic, as I am determined that it not be lost beneath 15 pages worth of topics. Mods, if this is a no-no, tell me and I will stop.

---

### Post by Ireclan on 2006-11-15
A little help here would be most appreciated. BEFORE this topic gets buried yet AGAIN. Since the document "ModemData.txt" does NOT simply say "YOUR CHIPSET IS..." and instead has a bunch of unclearly labled information.

---

### Post by Ireclan on 2006-11-18
I don't get it. What should I do to get help around here? What is the problem? Have I posted in the wrong forum? Does nobody have an answer to my question?

---

### Post by autocrosser on 2006-11-18
OK--I run a PCI modem with Edgy & have used several different types of modems with Linux over the years--

1. I would search this forum & the site in general about modems.

2. I would guess that you have a SOFTMODEM that is not addressable in Linux (I do hope not)

3. Please post the modemdata.txt file

4. Goto this page after you know what your modem is: [http://start.at/modem](http://start.at/modem)  (click on "mirror site")

5. Think about buying a SmartLink or Conexant internal PCI modem--look here: [http://www.ubuntuforums.org/showthread.php?t=190728&highlight=sl-modem](http://www.ubuntuforums.org/showthread.php?t=190728&highlight=sl-modem)

6. Some OLDER USB modems work also--Most OLDER serial modems work  (US Robotics & Zoom models)

7. Keep trying;)

---

### Post by Ireclan on 2006-11-19
Finally! Someone to help!:D Do you need all three pages of ModemData.txt? Or just a specific part?

---

### Post by autocrosser on 2006-11-19
Just upload the whole file--I'll look at it--

---

### Post by Ireclan on 2006-11-19
I cannot upload it- Ubuntu will not let me copy the files to a CD so that I may trandfer them to Windows. What shall I do?

---

### Post by autocrosser on 2006-11-20
Can you copy to a floppy?  Also--In Windoze, you can take a look at your installed devices--you might take a look at the modem control panel too--anything to get the type & model of modem in your system.

I don't hold out hope if your system is newer that 5yrs--almost all computers came with "soft" or "win" modems--these are software-control not hardware-control--only in very few cases are there drivers for softmodems--see my first post.

A erternal serial or USB modem has a better chance to work--choose a serial over a USB one--again, see my first post & do your homework---US Robotics or Zoom Serial, USB or internal PCI modems are the best--BUT only the OLDER models!!  Almost all the newer stuff is not worth being close to you (don't think of buying unless you have a 100% money-back;) )

In any case--keep trying--you'll get there--took me a while to get online at first (It is easier with Hi-Speed--Dialup has always been hard.)

---

### Post by Ireclan on 2006-11-21
Unfortunately, my computer has no floppy drive, only CD. Perhapse if you tell me HOW to transfer the documents to a CD, we'd get somewhere. Evidently, I'm not doing something right.

---

### Post by autocrosser on 2006-11-22
Do you have access to a USB thumb drive? Also, if you want to burn a disc--just put a blank cd in the drive & you will get a "burn what type of file dialog":)

Worst case--open your case up & get the info right off of the modem--I still think you should just go on eBay & get a older serial or USB modem--have you looked at the info I suggested?

---

### Post by PennYanPete on 2006-11-22
Hi Nomad O' North

I gave up after several attempts at those internal modems, not that you should, just don't let it get you down.

I ordered a TRENDnet TFM-560X from newegg $25, It's an external serial modem and has just worked.

Just another option if you get stuck.

PYP

---

### Post by Ireclan on 2006-11-22
Autocrosser, the CD I'm trying to use already has a file on it. But that shouldn't stop me from putting other files on the same disk...BTW, the OS claims that "root" owns the CD in question. Would that have anything to do with the CD problem?

---

### Post by autocrosser on 2006-11-23
If you burned the disc with--let's say windoze--it might say it belongs to root--try a blank disc. 

how are you doing with the info?

---

### Post by Ireclan on 2006-11-23
Rather than waste a disc, how about you tell me how to become root and transfer ownership of the disk to me? Wouldn't that solve the whole disk problem?

---

### Post by autocrosser on 2006-11-23
The problem is you are trying to multi-session a disc that was most likely not formated for it--I can't add material to a disc that has been burned closed-session (root or not)--You need Brasero or Gnome-baker to create mutli-session discs--Nautilus-CD-burn won't work that way (and it is the default install--If I'm wrong--someone point it out).

In any case--have you looked at the Info I posted?? The websites I pointed you to will give you a wealth of information to cure your main problem---Internet via Dial-up with Ubuntu.

Also--if you look at the pages of text you have--there should be a modem type in there--If not, You still can within windoze look at your internet dialer setup or installed devices--either way will give you a make-model & type of modem you have.

---

### Post by Ireclan on 2006-11-24
What do you mean by "multi-session"? Does it have to do with which OS I used to burn a disk? What do you mean by "closed-session"?

---

### Post by autocrosser on 2006-11-24
Unless you intentually format a CD to add data a bit at a time (multi-session burn), most (read almost all) disc-burning software (Nero, etc) will burn "disc-at-once" (or single-session "closed-session")--in this case, you can add data to the disc one time & then burn it. after that--you can't add anything to it--even if you used only 1K of the 700MB's available;)

When the average cost of a CD is .11--I don't normally worry about "wasting" a CD--I just bought a spindle of 100 TDK discs for 5.75us (.0575 per disc)--As you might guess, I go thru a fair amount of them per month.

---

### Post by Ireclan on 2006-11-25
Really? I don't recall Windows' CD burner operating in this manner at all. Oh well. I shall get ANOTHER blank disk, so that I may present "ModemData.txt" to you.


EDIT


Here it is, in all its helter-scelter glory:


 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2006_November_07


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:0b.0	11c1:048c	11c1:044c	Communication controller: Agere Systems V.92 56K WinModem 

 Modem interrupt assignment and sharing: 
153:        304   IO-APIC-level  uhci_hcd:usb2

 --- Bootup diagnositcs for card in PCI slot 01:0b.0 ----
[   30.180938] PCI->APIC IRQ transform: 0000:01:0b.0[A] -> IRQ 153

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  01:0b.0
   Class 0780: 11c1:048c Communication controller: Agere Systems V.92 56K WinModem
      Primary PCI_id  11c1:048c
 Support type needed or chipset:	Agere.SV2P
 Under Linux 2.6.n kernels, the chipset is NOT SUPPORTED . Read InfoGeneral.txt about alternatives.


 Vendor 11c1 is Lucent Technologies or subsidiary Agere Systems, Inc. Their Linux
 code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced, 
 and two have support under Linux:
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048(c,d,f) none           SV2P            soft modem 
 0600       none                           soft modem, very few in the field.
 062(0-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 14:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by Ireclan on 2006-11-28
Autocrosser? Are you going to help me interpret this mess?

---

### Post by mdsmedia on 2006-11-28
> **autocrosser said:**
> I don't hold out hope if your system is newer that 5yrs--almost all computers came with "soft" or "win" modems--these are software-control not hardware-control--only in very few cases are there drivers for softmodems--see my first post.

It appears, to my uneducated eye, that you have an internal, software controlled, WinModem. As autocrosser suggested, and I have no experience with dialup modems in Linux at all, WinModems or any software controlled modem are bad news in Linux. They are designed to work in Windows and the software which controls them is Windows based software.

A cheap HARDWARE controlled modem would appear, as has been stated before, to be your best option.

---

### Post by mdsmedia on 2006-11-28
> **Nomad O' North said:**
> *snip*
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:0b.0	11c1:048c	11c1:044c	Communication controller: Agere Systems V.92 56K WinModem 
*snip*
 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  01:0b.0
   Class 0780: 11c1:048c Communication controller: Agere Systems V.92 56K WinModem
      Primary PCI_id  11c1:048c
 Support type needed or chipset:	Agere.SV2P
 Under Linux 2.6.n kernels, the chipset is **NOT SUPPORTED** . Read InfoGeneral.txt about alternatives.
*snip*
Several different  modem chipset types  are produced, 
 and two have support under Linux:
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048(c,d,f) none           SV2P            soft modem 
 0600       none                           soft modem, very few in the field.
 062(0-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

-------------- end Agere Systems section -------------------
*snip*

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

*snip*
Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

*snip*

The above sections of your post point to the fact you have a WinModem and that it is not supported under Linux. They also offer suggestions of modem chipsets which are supported.

---

### Post by autocrosser on 2006-11-29
Sorry-I've been tied up for the last couple of days (work:mad:)--in any case--mdsmedia is right--you have a modem not supported in Linux--It's a softmodem as I feared--Your only bet is to get a PCI hard modem (or a soft that is supported), a Serial hard modem or a USB hard modem. The links that I gave you will tell you what is & is not going to work--I personally use a SmartLink supported softmodem (PCI-based) & have a Zoom USB 2986L hard modem as a backup unit.

THe Smartlink I bought from a vendor on eBay for 9.99 + shipping--The Zoom I've had for several years--

Check very carefully any claims you get as to workability in Linux--some vendors "say" a certain modem will work and will not--

There also are several threads about modems here--take a look & weigh your options.

---

### Post by Ireclan on 2006-11-30
Good news. I found another modem lying about my room, installed it, and ran scanmodem on it. It appears to be supported, but just to confirm that I'm reading ModemData.txt right, I'd like to post it for you guys to peruse. The problem is, Ubuntu will not let me erase or add more content to the disk I need to use to transfer the .txt file Windows-side. How would I accomplish this WITHOUT using a new disk?

---

### Post by Bartender on 2006-11-30
You never answered the earlier question - does the old PC have any USB ports, and do you have a thumb drive?  They're practically giving smaller thumb drives away.  I think last week you coulda bought a 4-pack of 256MB thumb drives for free after the rebate...

A thumb drive is certainly easier than burning up CD's.

---

### Post by Ireclan on 2006-11-30
No, Bartender. I do not have thumbdrives. Yes, my PC dose have 6 USB ports- 4 in the back and 2 in the front, of which three of the four back ones and none of the front are in use. But I do not use thumbdrives, I use CDs, so this is really not a legitimate solution to the problem.

---

### Post by Bartender on 2006-12-01
I understand that you don't want to keep wasting 640MB CD's just to transfer a tiny amount of data.  That's why I suggested using a thumb drive.  
Your conversion to Ubuntu will almost certainly cost you a little bit of money.  A stack of barely used CD's, a $10 thumb drive, maybe an external or internal US Robotics hardware modem, which would cost about $15 w/shipping on eBay - you're probly gonna have to shake loose some coin one way or another.

---

### Post by Ireclan on 2006-12-01
I've already had to shake loose some coin for a new modem, Bartender. I'm not going to buy a thumbdrive just because I can't figure out how to burn to or erase a CD. Instead, I'm going to take the more logical course in this matter and simply learn how to manipulate CDs under Ubuntu Linux. You wouldn't happen to know how to burn more content to a previously used disc or erase a disc, would you?

---

### Post by Ireclan on 2006-12-05
Um......Hello? Anyone?

...

Should I just make a new topic asking how to erase or add new content to a used CD?

---

### Post by autocrosser on 2006-12-05
Well--both Bartender & I have tried to help you help yourself.

I am here to tell you that unless you use CD-RW's, you can't add data to a burned CD UNLESS you have formatted it for "multi-session".  You can download Nero for Linux, Brasero, Gnome Baker, K3B or several other burning programs & you will find that they all work the same way. In addition, if you know one in Windoze--I would be interested to hear about it (I'd bet if you do--it is formatting multi by default).

You can't make media do something it is not formatted to do.
This is true of any operating system--Linux, Windoze or Mac OS.

---

### Post by Peti29 on 2006-12-06
As for the migration problem between Windows and Ubuntu. If you have both systems on the same computer you may mount your Windows partitions into Ubuntu's filesystem via "mount". It should be automatically done for you if you already installed Ubuntu (at least in Edgy). However if you are booting from the live CD you have to do it yourself.
(I don't know if NTFS partitions can be mounted writeable, but it works for FAT32)

---

### Post by Chinkostu on 2006-12-06
> **Nomad O' North said:**
> I've already had to shake loose some coin for a new modem, Bartender. I'm not going to buy a thumbdrive just because I can't figure out how to burn to or erase a CD. Instead, I'm going to take the more logical course in this matter and simply learn how to manipulate CDs under Ubuntu Linux. You wouldn't happen to know how to burn more content to a previously used disc or erase a disc, would you?

buy a rewritable CD. until you figure out wether you're burning in multi or single session (windows often compares multi-session to foppy disks). i can't remember if theres a way of checking the CD's type and if anything can be burned to it.

and anyway, if you are burning them single-session, then you've just used 2 cd's. investing in a USB pen drive is definately a worthy investment. i have 3 or 4 lying around (old mp3 players) and until i got my NTFS partitions set up and the like, it was the only way i got files from windows to ubuntu. on the same pc.

if you live in the UK i can mail you one of mine. it might be a bit tattered and abused, but it works perfectly.

---

### Post by Ireclan on 2006-12-06
Autocrosser, I AM using CD-RW. I apologize for not clearing that up sooner. I thought you would simply assume that's what I was using...

Okeydokey...

Now that we've cleared that up, could you tell me how to add more data to a CD-RW? And while you're at it, mabey you could also tell me how to erase a CD-RW?

---

### Post by Cariboo1938 on 2006-12-06
> **Nomad O' North said:**
> Um......Hello? Anyone?
...
Should I just make a new topic asking how to erase or add new content to a used CD?Hi Nomad O' North, 
Yes, it's actually another topic...Maybe you check [HERE]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+writing+without+tears") if that is what you want to do...

---

### Post by jordanmthomas on 2006-12-06
I'll throw in my two cents on getting your data real quick.
Try installing this in Windows:
[http://fs-driver.org](http://fs-driver.org)
You can mount your ubuntu partition and grab your text file to upload.
[I]
**leaves, because he knows nothing about modems**[/I]

---

### Post by autocrosser on 2006-12-06
Thank you for that--as you might guess--it does not pay to assume---I use Brasero--it allows erase of CD-RWs with ease & will setup a multi-session burn format if asked--I'm sure that others here will have favorites also;)

So I would "guess" that you have no problems with the internet (in Linux)?  
If so--it is time to move onto other threads as this one could be called "done"

> **Nomad O' North said:**
> Autocrosser, I AM using CD-RW. I apologize for not clearing that up sooner. I thought you would simply assume that's what I was using...

Okeydokey...

Now that we've cleared that up, could you tell me how to add more data to a CD-RW? And while you're at it, mabey you could also tell me how to erase a CD-RW?

---

### Post by Ireclan on 2006-12-07
I have yet to post the ModemData.txt for my most recent modem acquisition. After I have done that, and you have perused it to see whether I was correct in my assumption that my new modem is indeed compatible with Linux, I'll need somebody to walk me through the process of obtaining and installing the correct driver(s) and configuring my net connection.

As far as my two CD questions are concerned- are you saying that I have to go through the CD burning preogram to add data/erase the CD? I can't just copy the folder I need and paste it in the window that displays the content of the CD?

---

### Post by autocrosser on 2006-12-07
As far as the CD question--yes, you need to use a program to erase/multi-session burn--if you use the system default (Nautilus cd burn) it only will do disc-at-once & might not see that you have a CD-RW (treats it as a CD) & is limited in other ways--for basic burning, the default works, but is not the best solution.

---

### Post by Ireclan on 2006-12-08
So, just to make sure I understand you...

Nautilus CD Burner will not erase/multi-format a CD-RW?

If not, what other program can I use that is installed by default (remember, I have no net connection yet, so I cannot install additional packages unless they are on the CD or within the system)?

---

### Post by autocrosser on 2006-12-08
You are correct--it will do disc-at-once & BASIC burning functions--you will need to install a more advanced burning solution to open up your formats--

You could get Nero for Linux--download it in windoze & then transfer it to your Ubuntu install--take a look at the threads on reading NTFS in Linux--this would allow you to download things in windoze & then boot Ubuntu & copy things from the windoze partition--there is also some read/write useability that is coming of age--this would allow you to write the modem.txt to your windoze partition & work with it there. (search the forums for fuse)

You can also download the .deb files you need in windoze & transfer them also--

As you can see, I'm pointing out options that will work around the modem problem until it is sorted out.

---

### Post by Ireclan on 2006-12-08
I hate to be bull-headed, but isn't erasing a disc a "basic burning function"?

And are you saying that a more advanced program isn't installed by default in Ubuntu?

If I erase a disc Windows-side will I be able to burn something on it Ubuntu-side?

---

### Post by autocrosser on 2006-12-09
NO--erasing a disc is a advanced function (take a look at Nero for example--10.8MB download & Nautilus CD burn--2761K download).

YES a more advanced burning solution is not installed by default--the whole install has to fit on one disc--So the Devs go thru real agony everytime they set-up a new OS--so many things to include & a fixed disc space to put it on. The clamor for certain apps is very loud sometimes. They put a basic "blend" on the disc so you have a "out-of-the-box" full system--it is up to you to add the "extras" as you see fit--I customize my install to the point that it would take 4 or 5 discs to install it (my last backup went 12.6MB).

YES-if you erase the disc --Nautilus will (re)burn it. It will be treated as a "new" blank CD.

---

### Post by Ireclan on 2006-12-09
Okeydokey, Autocrosser- here's the new ModemData.txt!


==========================================================================


 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
 Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2006_November_07


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 01:0b.0	11c1:044c	11c1:044c	Communication controller: Agere Systems LT WinModem 

 Modem interrupt assignment and sharing: 
153:         23   IO-APIC-level  uhci_hcd:usb2

 --- Bootup diagnositcs for card in PCI slot 01:0b.0 ----
[   30.358806] PCI->APIC IRQ transform: 0000:01:0b.0[A] -> IRQ 153

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  01:0b.0
   Class 0780: 11c1:044c Communication controller: Agere Systems LT WinModem
      Primary PCI_id  11c1:044c
 Support type needed or chipset:	Agere.DSP
 


 The modem has a supported Lucent/Agere  Mars or Apollo DSP (digital signal 
 processing) chipset. Support packages for 2.6.n kernels are at: 
 [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)
 For a temporary fix for 2.6.18 kernels see 

 See AgereDSP.txt for Details.
  DSP=1

 Vendor 11c1 is Lucent Technologies or subsidiary Agere Systems, Inc. Their Linux
 code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced, 
 and two have support under Linux:
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048(c,d,f) none           SV2P            soft modem 
 0600       none                           soft modem, very few in the field.
 062(0-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

 0x044c -- Mars 3 Perseus data/fax only:North America and Global board
 0x044c -- Mars 3.2 Mercury data fax only when no eeprom is present, North America DAA
-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 14:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------



So, am I right? Is this modem supported under Linux? Incidentally, how would I change my CD write speed to the lowest possible?

---

### Post by autocrosser on 2006-12-09
You are right-I've not had experience with this one--the information page is: 

[http://martian.barrelsoutofbond.org/index.html](http://martian.barrelsoutofbond.org/index.html)

This requires a tarball build & I do know that you will not have the build tools for it--

I'll try a build of it & if it builds on my system, I'll find a way to get a finished build to you.....

---

### Post by autocrosser on 2006-12-09
Ok--I've built it--what you will need to do--(I "think" you won't need build tools--if you get a build error--then we will cross that bridge)

1. download the martin-full-20061203.tar.gz to your desktop
2. using Archive manager--expand the file
3. open a terminal (Menu>Accessories>Terminal)
4. in the terminal type cd & then drop the martian file on the open window This wiil look like- cd '/home/"yourhomename"/Desktop/martian'
5. hit return & then type make all  hit return then type sudo make install hit return
6. give your password
7. watch a fair amount of information scroll by
8. take a look at the useage part of the webpage--you will not need to do the scripts part
9. see below--
     [B]Usage
[/B]

     Load kernel module and launch user space driver     
     # modprobe martian_dev
# martian_modem     Leave it running and you can access the modem by /dev/ttySM0 file.     
   
         

10. the /dev/ttySM0 is your modem's "address"
11.goto Menu>System>Administration>Networking & highlight the "modem connection"--then tic the "properties" tab--input your information & where it asks "modem port" in the modem tab---put /dev/ttySM0---the rest of the information as your dialup connection requires.
12. do the "modprobe martin_dev" & martian_modem in the open terminal & then try the modem---

There might be some information I have forgot---

---

### Post by Ireclan on 2006-12-10
Sorry, it didn't work. Due to my inexperience with Linux, the only thing I can tell you for sure is that I extracted a folder called "martian" into my "/home/william/Personal Files" directory. I don't think "make all" did its job, but that's just a hunch that I have. In any case, "sudo make install" produces many errors and warnings. I honestly thought this would be simpler than it is. All I thought I would have to do was extract a file and slap it somewhere, and configure my connection. Guess I was wrong, huh? So...What's to be done?

---

### Post by autocrosser on 2006-12-10
OK--you are caught in a catch 22--you need everything in "build" to build a package for internet use--I didn't see a .deb file there anywhere (could be installed without all the "pain")--You will need the "make", "build" & most likely a slew of development packages to "make" the modem driver. This is the reason why I look VERY carefully before I buy anything--early in the thread I gave you information sites to check what modem would work well in Linux--this still holds true.

When I first started in Linux, I had bought a USB modem that would just work (Zoom 2986L) so I could download what I needed to setup my system--I later bought another modem that took a small amount of work to setup (read it had .deb files I could download) & as I have become more advanced in Linux-use, I find that I just build what I need--Problem is that you must crawl before walking or running.

So--I return to--buy a modem that after you check out the information--you "know" will work....period. I recommend the old Zoom I use--it's not the fastest modem out there, but it works---cost me 18+shipping on eBay & has been a very solid performer--I later bought a PCI Smartlink modem & keep the Zoom as a backup if I have problems. 

The problem is that dialup is a dying breed--it has ALWAYS been easier to connect via ethernet in Linux & now that Hi-Speed is becoming more available--dialup support is harder to find.

---

### Post by Ireclan on 2006-12-10
So what are you saying? Buy a new modem or give up?

---

### Post by tuxcantfly on 2006-12-10
No, It'll work, you'll just have to do some good old compiling. Just download all the packages on windows, transfer them to ubuntu via ext2-ifs, and dpkg -i them.

---

### Post by tuxcantfly on 2006-12-10
the packages you'll want are build-essential and all of the stuff it depends on (gcc and the like); see on packages.ubuntu.com

---

### Post by tuxcantfly on 2006-12-10
then, after installing them, do what autocrosser said: cd into the directory and do all the make, make install stuff.

---

### Post by Ireclan on 2006-12-11
What specific packages do I need?

---

### Post by Ireclan on 2006-12-14
*BUMP*

I'm not giving up...

---

### Post by Ireclan on 2006-12-18
You guys/gals DO know that I was serious when I said I wasn't giving up, right? In fact, I'm so serious that from now on, I will be re-bumping this topic EVERY THREE DAYS 'till mod prevent me or I get a reply. I am truely sorry to be this annoyingly dogged, but if that's what it takes to get a response to my query, then that's just what I'll do.

---

### Post by Ireclan on 2006-12-22
*bump*

---

### Post by Ireclan on 2006-12-26
*bump*

---

### Post by Bartender on 2006-12-26
Nomad -

I feel sorry for whoever has to put up with you on a daily basis.

---

### Post by Ireclan on 2006-12-26
Why, because I'm persistant?

---

### Post by Ireclan on 2006-12-30
Will using a U.S. Robotics external USB modem make things any easier?

---

### Post by gn2 on 2006-12-30
Your existing modem will not work.

Buying new hardware can be much easier than spending ages wasting time.

For a proven solution re-read post number 17.

Is ADSL not available where you are?

---

### Post by Ireclan on 2006-12-30
If my existing modem won't work, then why did tuxcantfly say it would? Not that it matters much anyway; I've almost given up on getting an answer on this question. One thing that YOU could do to help me decide whether Linux is truely a dead option is to answer my previous post: will an external USB modem work? Where I live, ADSL is not an option. Nor is buying things from the net.

---

### Post by gn2 on 2006-12-30
USB dial-up modem may work, there's one sure way to find out.....

Where are you geographically speaking?

---

### Post by leo1a0 on 2006-12-30
hello!  
I just want to say I've read the whole thread: Nomad O' North has received a  lot of help from many people and I haven't seen Nomad O' North being polite or even grateful with any one. -They're trying to help, at least you could be pacient and say thanks.

that's it, thanks

---

### Post by Ireclan on 2006-12-31
leo1a0, please don't post unless you're willing to help me. I don't need a lecture from you on politeness, I just need help getting a working modem. I'll thank people plenty when the thing I need done actually gets ACCOMPLISHED. ' Till then, I'm all business.  

As for gn2, I'm located in the Ozarks. That's in Missouri.

---

### Post by gn2 on 2007-01-01
> **Nomad O' North said:**
> leo1a0, please don't post unless you're willing to help me. I don't need a lecture from you on politeness, I just need help getting a working modem. I'll thank people plenty when the thing I need done actually gets ACCOMPLISHED. ' Till then, I'm all business.  

As for gn2, I'm located in the Ozarks. That's in Missouri.

Best advice I can give you is to do some more research and find a modem with a proven track record with Ubuntu. Like the one I already told you about that's mentioned in Post 17.
If you can't buy on the net you could order by phone?

As ADSL is out, you could try this: [http://www.idishnetwork.com/specials_internet.php](http://www.idishnetwork.com/specials_internet.php)

It's possibly quite expensive but if you've got a neighbour you trust to share the connection with.........

---

### Post by leo1a0 on 2007-01-01
Hello again, I just want to say you should read this thread before giving some more help:


[http://www.ubuntuforums.org/showthread.php?t=56931](http://www.ubuntuforums.org/showthread.php?t=56931)

Thanks

---

### Post by gn2 on 2007-01-01
Shipping is still free....... :)

---

### Post by Ireclan on 2007-01-01
Oh well, then. It looks like I'll just have to check back with linux in a few years, when hopefully it will support a wider variety of hardware. Thank you for you time, all who tried to help me (as opossed to trying to asasintate my character by using stuff from my past against me, a la leo1a0).

---

### Post by Bartender on 2007-01-01
> **Nomad O' North said:**
> (as opossed to trying to asasintate my character by using stuff from my past against me, a la leo1a0).

Yeah, right, a coupla weeks ago is "the past".  Don't let him get under your skin, leo1.

---

### Post by ardvark71 on 2007-01-01
> **Nomad O' North said:**
> Will using a U.S. Robotics external USB modem make things any easier?

A U.S. Robotics SERIAL modem would probably be your best bet.

---

### Post by Ireclan on 2007-01-02
Unfortunately, I do not believe serial modems are made anymore. I shall have to check, but I do belive that I was told they weren't. But won't a serial modem still require drivers? If that is the case, then this still won't help me, as I perused Linmodems.org and it seems that, according to them, U.S. Robotics isn't releasing Linux drivers for their products at this time.

And Bartender, if you really dislike me as much as you seem to, why are you even posting in this thread? The only reason I can think of is to stick up for leo1a0, which is really quite silly, as I am sure he is quite able to stand on his own two hind legs without your protection. I honestly don't know why you dislike me so much in the first place. At least leo1a0 gave a reason (he thinks me an ingrate), where as you have yet to give one.

---

### Post by ardvark71 on 2007-01-02
> **Nomad O' North said:**
> Unfortunately, I do not believe serial modems are made anymore. I shall have to check, but I do belive that I was told they weren't. But won't a serial modem still require drivers? 

Actually, last I saw, they are still being manufactured although probably not in great quantity at this point in time. You can usually find them at a computer or electronics store or on ebay used. And no, they don't require separate drivers, they usually work with Linux straight out of the box, just plug it in and configure through "Networking" or a program like "Gnome PPP." I'm using an old Zoom external that works great.

Best Regards...

---

### Post by Ireclan on 2007-01-03
OK. I shall check at Radioshack and a few other eletronics stores. Three quick questions, though: Why are external USB modems not supported? Do USB modems require a driver? If so, why don't serial modems?

---

### Post by maniac_X on 2007-01-03
> **Nomad O' North said:**
> OK. I shall check at Radioshack and a few other eletronics stores. Three quick questions, though: Why are external USB modems not supported? Do USB modems require a driver? If so, why don't serial modems?

[http://www.geeks.com/details.asp?invtid=EX560LKU&cat=MDM&cpc=MDMbsc](http://www.geeks.com/details.asp?invtid=EX560LKU&cat=MDM&cpc=MDMbsc) 

I bought one of these last week. I was up and running on the Live CD in a matter of minutes.
**No drivers to install!** Just opened up **System > Administration > Networking**, deactivated my 
Ethernet connection, clicked on Modem connection, entered properties to add ISP info and 
clicked Activate and I was surfing. Couldn't have been any easier except maybe being able 
to launch from the desktop. I have since installed to harddrive and am enjoying the beginning of freedom. ;) 

I notice that you mentioned you couldn't buy over the internet. Is there a reason that's not possible?

ps. I know the link shows a USB/Serial modem. Geeks shipped me Model# **EX560LKA** which is just 
the serial version. I bought it for the "serial" part so I didn't worry about sending it back because it did what 
I needed it to do.

---

### Post by ardvark71 on 2007-01-04
> **Nomad O' North said:**
> OK. I shall check at Radioshack and a few other eletronics stores. Three quick questions, though: Why are external USB modems not supported? Do USB modems require a driver? If so, why don't serial modems?

Usually, a USB "external" modem is just a Winmodem in a separate case. And like winmodems, they are not built to perform all of the duties a hardware modem does. A winmodem relies on software and the system's processor to do much of its workload. Linux, in general, still has not incorporated out of the box support to most winmodems. That's why the the USB externals are still not generally supported. External serial modems are usually hardware based and every version of Linux I've ever known supports them out of the box without a great deal of hassle or configuring, meaning the drivers are built into the operating system.

Trust me, if you're starting out in Linux, it's far easier just to get a device that is already  supported than it is to try and install Linux drivers. ;)

---

### Post by Ireclan on 2007-01-06
Okeydokey, I checked at Radioshack, and they have no serial modems. Not only that, but they also said that serial modems were old and no longer made. They also said that they knew of no one in my town who possessed such a device. What's really weird is that the guy helping me then burned me a Knoppix CD and told me to try that. I was under the impression that the only thing Knoppix excelled at was partitioning hard drives and running in live CD mode...

Anyway, enough about that. I've struck a deal with my computer teacher that now allows me to buy stuff on line. Do you guys/gals have any recommendations (other than those which I have already received) on which serial modem I should get?

---

### Post by ardvark71 on 2007-01-07
> **Nomad O' North said:**
> Okeydokey, I checked at Radioshack, and they have no serial modems. Not only that, but they also said that serial modems were old and no longer made. They also said that they knew of no one in my town who possessed such a device. What's really weird is that the guy then burned me a Knoppix CD and told me to try that. I was under the impression that they only thing Knoppix excelled at was partitioning hard drives and running in live CD mode...

Anyway, enough about that. I've struck a deal with my computer teacher that now allows me to buy stuff on line. Do you guys/gals have any recommendations (other than those which I have already received) on which serial modem I should get?

That doesn't surprise me, assuming Radioshack gave you accurate information. Sadly, dial-up modems are being phased out in favor of DSL/Cable. I think it will be only a matter of time before all dial-up's are no longer manufactured.

Please see my previous post (#75) on this thread as to my recommendation. Failing that, a Zoom or other serial hardware modem should do the trick as long as it least supports V.90. You can find used (or even brand new) cheapies on ebay or other auction sites.

Best Regards...

---

### Post by Ireclan on 2007-01-07
eBay seems a bit dicey to me...I'd like a good quality modem...One that'll last me, yet cost as little as possible for the quality of the device. You know what I mean? I really don't relish the idea of being ripped off...


I've looked up external serial modems at Tiger Direct.com. Does [this]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=84751&Tab=0&NoMapp=0") seem good? It has no on/off switch, and I'm afraid it might not be compatible with my ISP...

Should I make a separate topic asking for modem recommendations?

---

### Post by ardvark71 on 2007-01-07
> **Nomad O' North said:**
> eBay seems a bit dicey to me...I'd like a good quality modem...One that'll last me, yet cost as little as possible for the quality of the device. You know what I mean? I really don't relish the idea of being ripped off...


I've looked up external serial modems at Tiger Direct.com. Does [this]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=84751&Tab=0&NoMapp=0") seem good? It has no on/off switch, and I'm afraid it might not be compatible with my ISP...

Should I make a separate topic asking for modem recommendations?

Looks good to me! It has both V.90 and V.92 support so it should work with your ISP just fine. I couldn't see whether or not this unit had an on/off switch but it doesn't really matter. Some do and some don't. It shouldn't affect the performance any.

You could ask others for recommendations but I wouldn't expect a unified response, though.

Best Regards...

---

### Post by Ireclan on 2007-01-07
Okeydokey. I'll give it a shot. Here goes nothing, and thank you for your time. I'll let you know if everything works out or not.

---

### Post by ardvark71 on 2007-01-07
> **Nomad O' North said:**
> Okeydokey. I'll give it a shot. Here goes nothing, and thank you for your time. I'll let you know if everything works out or not.

You're welcome, glad I could help 8)

---

### Post by Ireclan on 2007-02-05
Okeydokey. I have the external serial modem up and working Windows-side. Could you please help me get it up and working Linux-side?

---

