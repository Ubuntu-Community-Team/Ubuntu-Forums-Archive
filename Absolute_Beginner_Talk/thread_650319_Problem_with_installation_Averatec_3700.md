---
title: "Problem with installation Averatec 3700"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ericmc783 on 2007-12-26
I'm having a problem installing Ubuntu 7.10 on my averatec 3715. I'm using the download 

from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
The regular O/S on this machine is Windows Vista Home Premium.

I'm having the problem some other people have had, getting stuck on [B]"*Running Local Boot 
Scripts (/etc/rc.local)"[/B] The cursor stays there and it just hangs there forever.
(further down in this post, I've listed all the specs for my PC).

I've tried using both the regular download, as well as the alternative, and I still end up 
at the same point. (Although on the alternative, I go through all the blue install screens 
and have the a partition run, and the installation appears to go ok, until the PC reboots 
and I end up seeing the exact same thing.


I have tried typing the following commands beneath *Running Local Boot Scripts 

(/etc/rc.local):

[B]sudo ls -lh /etc/rc.local

sudo ls -lh /etc/rc.local[/B]

Nothing happens.

Maybe I'm typing them in wrong?? (keep in mind I'm a total n00b when it comes to linux).


I've also tried hitting Ctrl+C, and also just hitting the ENTER Key, as I was told on 
another webpage. Nothing happens.


Each time I try to install, I get a message saying "[B]Ubuntu is starting in low graphics 
mode[/B]", because it was unable to detect my graphics settings. I've tried both clicking OK to 
accept low-graphics mode, and I've also hit configure and set the option for "Generic, 
1024X768, each time with the same results.

On the regular download, I tried the option for checking the Install CD for errors, which 
brought up no results. I also tried "Load Ubuntu with safe graphics mode". My screen 
flickered several times, and then I received the following error message at the "Running 
Boot Scripts" Point:


[B]"The display server has been shut down 6 times in the last 90 seconds. It is likely that 
something bad is going on. Waiting for two minutes before trying again on display. :O"[/B]


Each time, when Burning the .ISO image to a CD, I used the InfraRecorder program.

Posted below are specs about this laptop:

Model: Averatec 3715-ED1

512 MB DDR RAM, 60 GB HD.

Processor: AMD (K8) Sempron 3000+ Processor.

Graphics: VIA/SG3 UniChrome Pro (It's an Integrated Card, not really designed to handle 
heavy 3D graphics, but should be able to run Ubuntu without much problems).


One other peice of info that may be useful: This isn't the very first time I've tried to 
install Ubuntu on this PC. It's been over a year ago, but I installed it via LiveCD on this 
same laptop, and was just checking it out a little bit. I has the actual O/S installed just 
fine, and was able to go into system properties, and Applications to install apps like 
OpenOffice, Etc. I took it off my PC because I didn't feel like learning how to program and 
use it back them, knowing I would probably check it out more in the future. I have no idea 
what the current version of Ubuntu was back then. 

The only thing that has changed is, back then I was running windows XP Home, and 
Now I have Windows Vista. Since installing vista I have made sure my graphics drivers are 
installed properly and up-to-date, along with using Microsoft's DirectX 10.


Thank you for reading this somewhat long post and for any direction you can give.

---

### Post by ericmc783 on 2007-12-26
In the meantime, I've done a little more researching and I'm wondering if maybe I shouldn't just try xubuntu

---

### Post by overdrank on 2007-12-26
> **ericmc783 said:**
> In the meantime, I've done a little more researching and I'm wondering if maybe I shouldn't just try xubuntu

Hi and welcome, these links may help 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ericmc783 on 2007-12-26
> **overdrank said:**
> Hi and welcome, these links may help 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 


For both the regular LiveCD and the alternative, I followed the EXACT steps in the link above, under windows. No lies.

> **overdrank said:**
> 
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


I will do a checksum. 
And although I doubt it's a problem with the server i'm downloading from, maybe I'll try a different server just to be sure.

---

### Post by ericmc783 on 2007-12-27
update.....

Downloading from a different mirror resulted in the same thing, and when performing a checksum, the hashes matched.

I wish I knew why it's giving me this crap. My laptop, while not exactly top-of-the-line, should be able to handle this.

anyway, I'm gonna try xubuntu. I'll keep you guys posted when I get around to it.

---

### Post by Spitphire on 2008-01-01
I have the same exact computer as you, except i added 2gb's of ram.. which caused me some problems with overheating during install.. I also experienced very similar install problems so here's what you do in a nutshell... which seemed to work for me..

1.  Download the Alternate Install CD

2.  Install a Command Line System (DO NOT INSTALL XWIN initially!)

3.  Reboot into Command Line System.

4.  install the following packages: (make sure you CD is loaded as a source) 

ADD CD-ROM AS SOURCE:

> sudo apt-cdrom add
sudo apt-get update


then:

when you install this it will ask you for video display ONLY PICK 1024X768!!) Make sure you install them all seperately and not all on one line. My system had problems and overheated when I installed them all together, could just be my system though..

> sudo apt-get install xorg  
sudo apt-get install gdm
sudo apt-get install gnome-app-install
sudo apt-get install gnome-panel


5.  Edit /etc/X11/xorg.conf   and add the following under the 'Video Card Device':

> nano /etc/X11/xorg.conf

Option "DisableIRQ"

Your's will look slightly different than this on initial install:

Section "Device"
        Identifier      "Generic Video Card"
        BoardName   "via"
        VendorName  "VIA Tech"
        Driver "via"
        Option "DisableIRQ"     <**---- HERE**
EndSection

at this time you should be able to reboot and get into gdm, then update your video driver. good luck


now install these packages (they will be helpful for you...):

> fast-user-switch-applet 
gnome-systemtools
gnome-nettool
gnome-terminal
gtk2-engines
compbiz

powernowd   <--- for CPU scaling you may or may not need this depending if you sys overheats

Hope that helps let me know if you need any more help.

---

### Post by Spitphire on 2008-01-01
Also,

Anyone out there able to get the desktop effects enabled with the Averatec 3715? 

```
am@lp:~$ lspci |grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

Whenever I try to enable it doesn't work.  I don't have any shadows under my menus or anything.. 

An help would be appericiated.

Thanks.

---

### Post by mrfuzzemz on 2008-04-05
I was able to get compiz working on one of these machines.  I was amazed that it worked, but it didn't work perfectly.  If you get the 3D driver straight from via, you will have AIGLX compatibility, but when I tried it 6 months ago it was still a little buggy. (And it is integrated graphics so don't expect too much.)

Here is where you would get the driver:
[http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220](http://www.viaarena.com/default.aspx?PageID=2&OSID=45&CatID=3220)

That should be the Ubuntu Linux section of the display drivers section.  You just have to find which card is yours and there are instructions included for setting the driver and, optionally, compiz up. 

Good luck and report here if have and troubles or success. I may be able to assist further.

> **Spitphire said:**
> Also,

Anyone out there able to get the desktop effects enabled with the Averatec 3715? 

```
am@lp:~$ lspci |grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

Whenever I try to enable it doesn't work.  I don't have any shadows under my menus or anything.. 

An help would be appericiated.

Thanks.

---

