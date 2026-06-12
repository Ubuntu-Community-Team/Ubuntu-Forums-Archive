---
title: "This is kiling me =("
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by 2bad on 2008-03-29
So a few days ago I got rid of vista and installed ubuntu 7.1, but apparently I hadn't done enough research.  I coudn't get wireless to work and my vid cards are ATI.  I coudn't fix either of these probems so decided just to go back to vista.  I don't have anything on the harddrive that I need, and all I want is my vista back.  I tried booting to the vista reinstalation disk and choosing the install now option but to no avail, "windows must be installed to a partition formatted as NTFS".  *cry*.  I try to format it and then: "windows failed to format selected partition".  *cry*.  I then attempted to follow a guide to uninstal ubuntu and typed "fixmbr" into the command prompt...but it is not even a command (am I typing it in the wrong place?).  Please help...this is becoming a nightmare for me.  Thanks.

---

### Post by NightwishFan on 2008-03-29
Well you tried to come to linux at least. If you formatted Vista im assuming its gone. Sorry im not sympathetic. You _might_ have to fork some money for another Vista cd.

---

### Post by Inxsible on 2008-03-29
do you have the installation discs for Vista ? The upgrade discs that you normally get will not install the OS.

If you do, then put in the Ubuntu Live Cd and open Gparted and then format everything to ntfs. Then use the Vista installation discs

---

### Post by alexforcefive on 2008-03-29
I'm not sure if the vista install cd has a partition editor, but I'm presuming it does. Just have a look around the options and see if you can figure out how to delete the partition and start afresh.

If you can't figure it out, come back and I'll talk you through using gparted on the ubuntu live cd

*edit* everyone types too fast! >:|

---

### Post by Ub1476 on 2008-03-29
Download [GParted]("http://gparted.sourceforge.net/") as a live cd to modify your partitions. 

After Vista is installed, you can set up a dual-boot with Ubuntu if you'd like. If you post the output of:

```
lspci | grep VGA
lspci | grep Network
```

..I can see if I can find any available driver for your hardware:)

---

### Post by twin_57103 on 2008-03-29
If you're unable to reformat through the Vista installer, perhaps try a different formatting tool.  gparted is free, otherwise consider Partition Magic or another commercial product.  I don't know if it will help, but it might be worth a try.

---

### Post by TechDragon on 2008-03-29
I felt the same way, LINUX SUCKS, after about a week of using it.  It took a good month b4 feeling somewhat comfortable with it.  

Here are a few suggestions:

a. dont give up, linux is worth the effort
     1. its faster
     2. its safer
     3. it stable

b. ask one question at a time, the community here is extremely helpful.

c. focus on fixing one issue at a time, once you learn how, you will likely smack yourself at how simple the solution was.

d. Linux is not "Harder" than "windows" just different.  It just like windows takes a learning curve.  If you had started off in life with Linux, then windows would seem frustrating.


For, ATI, Google "Envy ubuntu" and download the installer.  It makes life easier.

Search my name for I have asked most of these questions already, and had them all answered. 

Last case scenario, try a different Linux, Mandriva is about the only other Linux I would suggest to a newcomer.

---

### Post by armitage1337 on 2008-03-29
I'd have to second TechDragon. The first time I tried Ubuntu I was sick of it within a week and went back to Windows for 6 months. But the second time I tried it, I put in the effort to make it work, and since then I've had no problems at all. I've got an ATi graphics card - you just use the restricted drivers manager to install the driver. As for wireless, it really depends on the chipset, but you can usually get it to work.

---

### Post by 2bad on 2008-03-29
o.O thanks for all the fast replies guys =).
> **Inxsible said:**
> do you have the installation discs for Vista ? The upgrade discs that you normally get will not install the OS.

If you do, then put in the Ubuntu Live Cd and open Gparted and then format everything to ntfs. Then use the Vista installation discs

All I have is the "reinstallation disk" for when the OS is already installed on your computer...I hate to do it but I think I might have to hit up rapidshare on this one = /.

> **Ub1476 said:**
> Download [GParted]("http://gparted.sourceforge.net/") as a live cd to modify your partitions. 

After Vista is installed, you can set up a dual-boot with Ubuntu if you'd like. If you post the output of:

```
lspci | grep VGA
lspci | grep Network
```

..I can see if I can find any available driver for your hardware:)

ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
Intel Corporation 82562V 10/100 Network Connection (rev 02)

I'm not as conerned about the Radeon as I am the wireless network not working.  It just doesn't show up as one of the options next to "wired connection" and "modem connection".  I tried installing wicd but I get an error saying that it interferes with Network Connections or something.  I wish I would have set up a dua boot in the first place, but I had no idea what I was doing =O.  Thanks =)


> **TechDragon said:**
> I felt the same way, LINUX SUCKS, after about a week of using it.  It took a good month b4 feeling somewhat comfortable with it.  

Here are a few suggestions:

a. dont give up, linux is worth the effort
     1. its faster
     2. its safer
     3. it stable

b. ask one question at a time, the community here is extremely helpful.

c. focus on fixing one issue at a time, once you learn how, you will likely smack yourself at how simple the solution was.

d. Linux is not "Harder" than "windows" just different.  It just like windows takes a learning curve.  If you had started off in life with Linux, then windows would seem frustrating.


For, ATI, Google "Envy ubuntu" and download the installer.  It makes life easier.

Search my name for I have asked most of these questions already, and had them all answered. 

Last case scenario, try a different Linux, Mandriva is about the only other Linux I would suggest to a newcomer.

I was thinking of trying that or PClinuxOS, but don't I still need to uninstall ubuntu to do that anyway?

---

### Post by TechDragon on 2008-03-29
no, Mandriva will format the drive and take over, I tend to flip flop between the two,  PCLinuxos is an offshoot of Mandriva, it is very popular but a little behind the curve these days.  It seems to have a slower development cycle than Mandriva.  I like both ubuntu and mandriva but I will tell you that you will get help if you need it quicker here.  The help you get at mandriva is good and acurate but not as quick.  PCLinuxos sometimes has trouble formatting the drive and installing itself, also the community seems a little weak.

I would suggest downloading the LIVE version of mandriva or pclinuxos if it finds all your hardware then install it.  If it doesn't don't bother.  You can do this with most linux distros, 

Mandriva,  [http://www.mandriva.com/en/download]("http://www.mandriva.com/en/download")

Download the default version "one" version, stay away from the FOSS version, FOSS means Free or Open Source Software, and includes no proprietary software.  

PCLinuxos,[http://www.pclinuxos.com/index.php?option=com_ionfiles&Itemid=28]("http://www.pclinuxos.com/index.php?option=com_ionfiles&Itemid=28")

OpenSuse, [http://en.opensuse.org/Mirrors_Released_Version]("http://en.opensuse.org/Mirrors_Released_Version")
Very good but don't expect an overly "Friendly" environment

Fedora,[http://fedoraproject.org/get-fedora.html]("http://fedoraproject.org/get-fedora.html")
If you can take a little razzing from the community, it can be a solid distro

Here is a great place for distro info
[http://www.distrowatch.com]("http://www.distrowatch.com")

Stay away from Gentoo, ARCH, Slack, Debian, intill you get much more attuned to Linux, and simply stay away from Gentoo forever :)


Also, consider asking one question at a time in this forum, this absolute beginner forum
People will help you resolve them one at a time and within a few days most of your problems will be solved.

One other thing make sure you have all your repo's available here in ubuntu, you have to do it from inside "Synaptic"  and if you go to Mandriva you will probably see me around there too.

---

### Post by jjgauthi on 2008-03-30
I hope I am not too late to help you.

I found myself in the same boat, installed Ubuntu without thinking and had no network, my video did work.

I tried to document every step I took and put in pertinent links on this [post ]("http://ubuntuforums.org/showthread.php?p=4614497#post4614497")

I will keep an eye on this thread but if you want to read it first and then post questions that would be great.  I wrote it for someone of my comprehension so I hope it is helpful I'm very new to linux.

Instead of the realtek drivers I would go and find the drivers for your specific card, mainly you want to find the windows 98/ME drivers, the INF and SYS files is what you will need.

Don't despair, baby jesus ain't crying yet.

---

### Post by spacefreak86 on 2008-03-30
Have you tried downloading and installing a copy of FreeDOS (or getting a Win98SE boot disk), doing fdisk, then installing Vista?

Although I agree, you should try out Linux for a bit longer (assuming its still on your system). I found Ubuntu a bit strange, but got over most of it with Kubuntu. It still took me two weeks to get all of the kinks out (connecting wirelessly to my school network with two or three layers of encryption being the hardest part), but now its running fine for what I need it for.

---

### Post by 2bad on 2008-03-30
Thanks a ton for the info Tech =D, and I' try to limit mysef to one question per.  JJ I feel like and absolute beginner, but how do I change my directory?  I know th command is CD /xxx but I don't really know what to change it to lol.  The 2 files are sitting in a folder called wireless on my desktop.  Thanks tons for the fix though I can't wait to see if it works, I've aready had ndiswrapper installed I didn't know there was more to it then that.  Maybe I will be sticking with ubuntu after all =D.  *crosses fingers*

EDIT: ok so I found out how to change the directory to the right one, even though I still dont understand the concept >.> .  I put in the folowing:
```
sudo ndiswrapper -i net8185.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l

```

But instead of getting what he said I should (the following):
alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
device (10EC:8185) present (alternate driver: r8180)

I got:
lucas@home:~$ cd /home
lucas@home:/home$ sudo ndiswrapper -i net8185.inf
driver net8185 is already installed
lucas@home:/home$ sudo depmod -a
lucas@home:/home$ sudo modprobe ndiswrapper
lucas@home:/home$ sudo ndiswrapper -m
module configuration already contains alias directive

lucas@home:/home$ sudo ndiswrapper -l

What did I do wrong?  =(

---

### Post by seshomaru samma on 2008-03-30
to get to the desktop go
```
cd Desktop
```
to get to the folder with the files
```
cd folder's_name
```
pay attention to upper and lowercase "cd [COLOR="Red"]d[/COLOR]esktop" will not work

---

### Post by TechDragon on 2008-03-30
I hope you get it working.  The community here is probably the friendliest.  IMHO, once u work out the bugs you will love the low maintenance that Linux grants.  No spyware, No Viruses, No hassles

Secunia rates software
Ubuntu [http://secunia.com/product/16251/]("http://secunia.com/product/16251/")

WindowsXP [http://http://secunia.com/product/22/]("http://http://secunia.com/product/22/")

WindowsVista [http://secunia.com/product/13223/](http://secunia.com/product/13223/)

Sorry I can't help you much on the wireless card I didn't run into probs with mine

The video card can be fixed easily with this

Envy [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

I am stuck with an integrated x1300 ATI once you get it working it is very good.

---

### Post by Ub1476 on 2008-03-30
[Here's]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") the community docs for ndiswrapper. I assume it will help a bit :)

---

### Post by Sidewinder1 on 2008-03-30
Welcome 2bad! Whatever you do please don't give up. I have been using ubuntu for my first try at Linux since Dec. '07. I couldn't be happier with it and the folks on this forum will "bend over backwards" to get you up and running. What others have said is true, no viri, spyware, malware, and it's all open source. There are currently over 23,000 software packages available through your Synaptic Package manager which will allow you to do just about anything you need to do. Does require patience though; just persevere and good luck.
Side

---

### Post by jjgauthi on 2008-03-30
> **2bad said:**
> Thanks a ton for the info Tech =D, and I' try to limit mysef to one question per.  JJ I feel like and absolute beginner, but how do I change my directory?  I know th command is CD /xxx but I don't really know what to change it to lol.  The 2 files are sitting in a folder called wireless on my desktop.  Thanks tons for the fix though I can't wait to see if it works, I've aready had ndiswrapper installed I didn't know there was more to it then that.  Maybe I will be sticking with ubuntu after all =D.  *crosses fingers*

EDIT: ok so I found out how to change the directory to the right one, even though I still dont understand the concept >.> .  I put in the folowing:
```
sudo ndiswrapper -i net8185.inf
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -l

```

But instead of getting what he said I should (the following):
alan@alan-desktop:~$ sudo ndiswrapper -l
[sudo] password for alan:
net8185 : driver installed
device (10EC:8185) present (alternate driver: r8180)

I got:
lucas@home:~$ cd /home
lucas@home:/home$ sudo ndiswrapper -i net8185.inf
driver net8185 is already installed
lucas@home:/home$ sudo depmod -a
lucas@home:/home$ sudo modprobe ndiswrapper
lucas@home:/home$ sudo ndiswrapper -m
module configuration already contains alias directive

lucas@home:/home$ sudo ndiswrapper -l

What did I do wrong?  =(

I had a similar problem when I installed the xp drivers and it told me it was an invalid driver.

here is what I did to fix it, this might work.

1) type *sudo ndiswrapper -l* this will tell you what driver was installed
2) use *sudo ndiswrapper -r (filename)* if type *man ndiswrapper* in a terminal it tells you that the *-r* is used to remove something from ndiswrapper.
3) once you have it removed go ahead and try to re-install using the windows 98 drivers.

Lets keep this rolling and see if we can get you up and running

---

### Post by 2bad on 2008-03-30
Well, I removed whatever driver I had on there and got net8185 installed, then followed the rest of the instructions and rebooted, but there is still no option for "wireless connections" when I go to network.  There was something that didnt seem right though, I never did see this pop up in the terminal:

device (10EC:8185) present (alternate driver: r8180)

I do however see the driver as being installed, but there is no "device present"

EDIT: I attempted to remove the driver and try starting over from the beginning but when I typed in the comand to remove it I got:

couldn't delete /etc/ndiswrapper/net8185: Innappropriate ioctl for device

= /

---

### Post by jjgauthi on 2008-03-30
Really dumb question, and it took me awhile to figure this out but have you blacklisted the r8180 driver, if not I'l work on a quick write up as to how I did it then, we'll try some more to get you up and running.

---

### Post by lswest on 2008-03-30
first off, the command for Vista is no longer "fixmbr" or "fixboot" it's ```
bootrec /fixmbr
bootrec /fixboot
``` and secondly, you can use the liveCD to reformat the drive into NTFS, then installing vista should work fine.

---

### Post by kamitsukai on 2008-03-30
> **lswest said:**
> first off, the command for Vista is no longer "fixmbr" or "fixboot" it's ```
bootrec /fixmbr
bootrec /fixboot
``` and secondly, you can use the liveCD to reformat the drive into NTFS, then installing vista should work fine.


**_If you really want to go back to vista_**

here's what to do vista won't install on a partition or drive formated with ubuntu (in my limited expiereience!) i dont know why but it just doesent like it! what i did was download active kill disk (the freeware version) and burnt it to a disk then wiped clean the drive and then vista would format and install on the drive itself 

***Direct download link from the site***
[http://software.lsoft.net/boot-cd-iso.zip](http://software.lsoft.net/boot-cd-iso.zip)
Just burn the iso file to a cd and then restart your pc with it in the drive and follow the options it gives you

or visit there site yourself at:[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by 2bad on 2008-03-30
Yeah, I backlisted it and set it to load when I boot.

Also, thanks for the vista info guys^^.  If I can't get the wireless card working then I'll definately be putting vista back on (and then attempting to dual-boot with another linux of course =D).

---

### Post by Raccoon1400 on 2008-03-30
If you try other distros, you may end up with ubuntu in the end. I have tried many, and it is still my favourite. I really like the community.

If you are looking at other distros, I would recommend ones with the gnome desktop, even though kde looks more like windows. Gnome is simpler.
I would suggest PClinuxOS, OpenSuse, or debian as alternatives.

If you really want to use vista, you can use gparted off the ubuntu CD, you don't have to download it separately.

If your wireless card is Broadcom, try this. It worked for me.
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/#comment-8217](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/#comment-8217)

---

### Post by kamitsukai on 2008-03-30
> **Raccoon1400 said:**
> If you try other distros, you may end up with ubuntu in the end. I have tried many, and it is still my favourite. I really like the community.

If you are looking at other distros, I would recommend ones with the gnome desktop, even though kde looks more like windows. Gnome is simpler.
I would suggest PClinuxOS, OpenSuse, or debian as alternatives.

If you really want to use vista, you can use gparted off the ubuntu CD, you don't have to download it separately.

If your wireless card is Broadcom, try this. It worked for me.
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/#comment-8217](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/#comment-8217)

Yep agreed ive always come back to ubuntu mainly because of the community but if ubuntu implemented the point and click iinterface of pclinuxos it would be amazing (not saying that commands aren't great but can be daunting..) and u can get desktop effects working just by clicking an option to turn it on!:guitar:

---

### Post by lswest on 2008-03-30
Also, on another thread, a guy who was restoring Vista to his laptop (to dual boot) said that creating a fat32 partition and formatting it to ntfs in the vista install worked for him.
[http://ubuntuforums.org/showthread.php?t=738460&page=2](http://ubuntuforums.org/showthread.php?t=738460&page=2)

---

### Post by 2bad on 2008-03-31
Well I have vista installed now so I'm dual booting.  Yay =D

---

### Post by lswest on 2008-04-01
Congrats!  Maybe you could mark this thread as solved then?  So that others know there is a solution?  Thanks!

---

