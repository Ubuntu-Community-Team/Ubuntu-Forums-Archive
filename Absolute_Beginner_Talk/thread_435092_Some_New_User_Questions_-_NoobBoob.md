---
title: "Some New User Questions - NoobBoob"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by noobboob on 2007-05-06
ok... so after reading a few tutorials/basic stuff... i installed ubu 6.06 dap server edition.  i plan on creating a home network file server (i plan on making a parition for a web server in the future when i figure out how to set up/program/run a LAMP), but for now since its just on the home network, i installed the gnome gui on top. (yes, i know i know... servers aren't suppose to have gui's except for webmin and what not, but i need to learn as much as possible about both environments)

i have some real basic questions:

1.  i have a raid sata card from addonics runnin a silicon chip that is suppose to be supported by newer linux kernels.  when i boot into the X, i can see my regular 40gig HD and CD rom Drive, but I have no way of access the space on the Raid.  The Raid has 4 320gig sata drives and during the boot before grub gets started it asks me to type f4 or "ctrl + s" for the raid configuration.  When i hit those keys nothing happens and it just boots normally into the DM.  While in the gui under System/Admin/Disks I see the 4 sata drives with 298 gigs.

1a. how do i access my sata hard drives because they are not available under Places/Computer although my 40gig is there?

1b.  before grub boots it shows my sata drives has having 304 gigs per HD, but under the disk manager they only register as 298gig, where did my gigs go? (not to mention they are 320 gig drives...)

1c.  do i have to recompile some drivers or something for my system to read the disks?

1d.  how would i set up the RAID functions?

1e.  do i have to format the HD for linux to read them?

2.  Ok this migh sound silly, but how do i access the CLI from the GUI?  Do i have to log out of the X or is it hidden somewhere? If i have to log out where do i go when i reboot to access the CLI?

3.  I just started my computer and forgot to plug in the ethernet, but after plugging it in I couldn't access the internet.  (I rebooted with the ethernet plugged in and all is gravy), does ubuntu not support "plug n play" with the ethernet?

4.  I have a generic, random USB wireless device that I found in the garage.  I've heard that wireless is sometimes an issue to set up, but is it possible for me to use the USB wireless?

5. I've been browsing the "themes" settings and don't like the default options.  Is there anyway I can program my own theme with different colors, buttons, and task bars?  Or maybe download one already assembled?  I'm just looking for something a little more stylish.

6.  How do I check my ip addy in the GUI?.  Is there a way to check the internal case temps?  Does Ubuntu have firewall settings?

7.  When loggin into the X, am I the root user?  Can I switch to the root user in X?  on the CLI am I the root? can I switch over to the root if not?

8.  Once I get the Sata drives up and running, how do I enable other computers (Win XP and Mac OSX, mainly the mac) to be able to read and write to them? Is it possible to format the sata drives to whatever file system the mac uses and still have ubuntu read them?

9.  When using the X, I can shutdown and the computer turns off.  In the CLI how do I shut down?  I usually exit back to the login prompt but can't figure out how to shut it down.  I just switch off the power supply at that point but I'm afraid it'll corrupt/damage my hard drive.

10.  How do I go about installed the Kbuntu and Xbuntu on top/along with the gnome GUI?  can i switch from one X to the other or would I have to shut down and restart and pick which GUI to use?  

11.  Can i remote login from my Mac into Ubuntu and use its apps or vice versa (remote login into the Mac from Ubuntu and use its apps)?


Thanks, i think that's all i have for now... any help would be greatly appreciated!

---

### Post by Nekiruhs on 2007-05-06
To access the CLI from GNOME you can go to Applications >Acessories >Terminal or press ctrl +alt + F1 to access a full screen terminal.

---

### Post by bobplano on 2007-05-06
wow. ok. 
GUI aren't advised for servers but it's ok for a home server since people won't be accessing too much (well people that aren't you that is). 
i'm not real sure about the RAID stuff so skip that.
hard drives are usually mounted in /dev/ or sometimes /media/ so look there for your hard drives. if they're not mounting that's a different problem. 
gigs are made up of megabyts and those of kilobytes and so on down to byets and bits. there are 320,000,000,000 or so bytes in your drive (i think) but a gig isn't an even 1,000,000,000; its more.
 if your hard drives aren't formatted at all, they won't store anything. linux can read fat32, ext3 and ntfs with ntfs3g. if it is a file server and windows and linux are using it then make it a fat32 since both can read it easily. 
for the USB wireless just try plugging it in and see if it detects it. if it is older, but was one of the more popular one then you might be set. otherwise you might need ndiswrapper. 
for the terminal(cli) it's under applications>accessories. 
to  use root powers you need to use sudo (root for one command) or su(root until exited). logging in as root will work but is disabled by default and not advised. for themes there are downloadable ones but i don't remember where. for terminal shutdown use sudo shutdown now. 
for kubuntu and xubuntu desktop enviroments use 
sudo aptitude install kubuntu-desktop or sudo aptitude install xubuntu-desktop. these install all the programs too. for only the look use
sudo aptitude kde-core and sudo aptitude install xfce4

---

### Post by noobboob on 2007-05-06
:tongue:  awesome thanks for the info... so i finally found the terminal and will be grabbing the kde/xf soon... 

how do i check to see if my drives are mounted/formatted? i'm looking in the CLI /dev and i see "cdrom" "disk" "dvd" etc. but the text are different colors (yellow, blue, cyan, hot pink)... what do the colors mean?  i think i see the sata hard drives "hda" "hda1" "hda2" and "hda5" but they are yellow.

---

### Post by xpod on 2007-05-06
You might be interested in "gnome-art" for changing your themes and stuff.

install it from either synaptic.....system>administration>synaptic
or the terminal....sudo apt-get install gnome-art

Great little program for the job which connects directy to gnomelook.org hence theres loads to choose from.
Of course you can just go to gnomelook.org but this makes it all a bit easier i think:) 

You`ll find your x/kubuntu desktops accessable via "sessions" at the logon screen once you install them.

Good luck

---

### Post by chalex on 2007-05-06
> **noobboob said:**
> 

1.  i have a raid sata card from addonics runnin a silicon chip that is suppose to be supported by newer linux kernels.  when i boot into the X, i can see my regular 40gig HD and CD rom Drive, but I have no way of access the space on the Raid.  The Raid has 4 320gig sata drives and during the boot before grub gets started it asks me to type f4 or "ctrl + s" for the raid configuration.  When i hit those keys nothing happens and it just boots normally into the DM.  While in the gui under System/Admin/Disks I see the 4 sata drives with 298 gigs.


Find out whether the card is a "true hardware raid" or a "fakeraid" card.  If it's a fakeraid card, most of the functionality is in the Windows driver and not in the hardware.  Under Linux you can either just use software RAID (man mdadm) or look into the "dmraid" driver which I think has the same functionality as the Windows driver.

> 
1b.  before grub boots it shows my sata drives has having 304 gigs per HD, but under the disk manager they only register as 298gig, where did my gigs go? (not to mention they are 320 gig drives...)

This depends on the exact meaning of "gigabyte".  Disk manufacturers claim it is 1 billion bytes.  If you use  the binary meaning (1024 bytes *1024..) then it's less.  There is also some overhead for the filesystem data.
> 
6.  How do I check my ip addy in the GUI?.  Is there a way to check the internal case temps?  Does Ubuntu have firewall settings?

From the cli, "ifconfig" deals with the network settings.  For the case temps, configure lm_sensors or smartmontools.  There's probably no firewall running by default, because it is not necessary, but you can configure it if you like.  A popular GUI for iptables setting is called Firestarter.
 
> 
8.  Once I get the Sata drives up and running, how do I enable other computers (Win XP and Mac OSX, mainly the mac) to be able to read and write to them? Is it possible to format the sata drives to whatever file system the mac uses and still have ubuntu read them?

I think you will need to use the dmraid driver.  Then you'll need to format the device with a filesystem that all three OSs can read and write.  Your best choice is probably FAT32.

> 
9.  When using the X, I can shutdown and the computer turns off.  In the CLI how do I shut down?  I usually exit back to the login prompt but can't figure out how to shut it down.  I just switch off the power supply at that point but I'm afraid it'll corrupt/damage my hard drive.

the command is "shutdown".  "man shutdown' for more info.  "sudo shutdown -r now" will reboot, "sudo shutdown -h 5m" will halt in 5 mins.

> 
10.  How do I go about installed the Kbuntu and Xbuntu on top/along with the gnome GUI?  can i switch from one X to the other or would I have to shut down and restart and pick which GUI to use?  

Install the meta-packages "xubuntu-desktop" and/or "kubuntu-desktop" respectively.  You'll need to log out, then choose a different session at the login menu to switch.

> 
11.  Can i remote login from my Mac into Ubuntu and use its apps or vice versa (remote login into the Mac from Ubuntu and use its apps)?

You can either configure a VNC server and use a VNC client on the other machines or just use remote X, in which case you'll need to have X11 installed on the Mac or Cygwin/X or another X server installed on Windows.

---

### Post by noobboob on 2007-05-18
Thanks everyone for the help, I'm much further along now... just still struggling with the RAID stuff.

> **chalex said:**
> Find out whether the card is a "true hardware raid" or a "fakeraid" card.  If it's a fakeraid card, most of the functionality is in the Windows driver and not in the hardware.  Under Linux you can either just use software RAID (man mdadm) or look into the "dmraid" driver which I think has the same functionality as the Windows driver.


OK so after much searching, I think my card is a "fakeraid"  I came across an article that says my addonics raid card's bios isn't accessible via the intel 945g chipset (no idea why).  If I could access the bios settings before grub loads, then I think I could get the SATA HDs to mount, but as it stands i'll have to use dmraid I think.

how do I install dmraid? is dmraid the same as "dm"? whats the difference between dm, dmraid, and mdadm?  also, i came across some info about setting up the raid via "make menuconfig"? what's that?

*** I just need some directions on how to set this thing up... :confused:

---

### Post by noobboob on 2007-05-18
I got dmraid to install now, but after typing in dmraid -ay, i get the no raid disks error.... 

do i have to partition the sata HDs BEFORE doing the dmraid -ay?  how would i go about doing this?

*** much thanks to anyone who can help out a newbie

---

### Post by igloocentral on 2007-05-24
> do i have to partition the sata HDs BEFORE doing the dmraid -ay? how would i go about doing this?

No. Read my [FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug) page and attach your results in this thread.

---

