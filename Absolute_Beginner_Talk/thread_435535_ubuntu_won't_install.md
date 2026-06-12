---
title: "ubuntu won't install"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by halligan46 on 2007-05-07
Hi All

I have a new system with winXP home installed and have been trying to install ubuntu \, but no success.
system info:  intel mobo dg965wh
                     Intell dual core 6400
                     2 SEAGATE HDD 500&300 GB SATA
                     I PLEXTOR PX 750A DVD-ROM WITH AN ADAPTOR FOR SATA PORT
                     1 SAMSUNG FLOPPY DR
                     2 GB KINGSTON DDR 6400 RAM
tHE DVD ROM works fine until I try to load Ubuntu, At this point I am using a disc from shipit and once the cd drive spins up I get the disc tree screen with the additional downloads but not the ubuntu set up screen.
I have the dvd-rom #1 in the boot menu in the bios. not using raid.  I'm pretty much lost. I got a copy from a magazine of Xandros and have the same problem.
Any ideas would be appreciated.  Another user suggested that my dvd-rom and hard drives might not be compatible so I used and adaptor to allow the dvd drive to connect to a serial ata post still no go.

Thanks again
JimThomas

---

### Post by jargoman on 2007-05-07
Correct me if I'm wrong but your trying to install while windows is running. 

once the disk is in restart your computer. That way you boot into linux and not windows!

---

### Post by teddybairs1 on 2007-05-07
You may need to reset your bios to boot from cd first instead of your hard disk. On the very first start up screen, before it even tries to load an OS hit either del, f1, f2, or esc depending on your system and it should put you into the bios set up. You've got to be quick about it though.

---

### Post by alienexplorers on 2007-05-07
To load Ubuntu put your liveCD in the DVD-ROM drive. Reboot your computer making sure the DVD-ROM is selected as the first drive to load.  You can change this in the BIOS at startup by pressing either F1 or DEL or whatever key loads your BIOS setup.  Once the DVD-ROM is selected reboot and wait for Ubuntu LiveCD to load.

---

### Post by GrahamCracker on 2007-05-07
I just had this problem too on an XP OS.  I'll change the BIOS and see what happens.

---

### Post by halligan46 on 2007-05-07
Sorry to whine but I have done all of the above.  My dvd-rom is number one in the boot order so I am thinking maybe I have a hardware problem.  
 I don't think my system recognizes my dvd drive.    in bios it shows the sata port is not activated or open that the dvd drive is hooked up to.  I hope that made sense.
Again thanks to all for your help, this process is a lot less intimidating with all of you holding my hand

JimThomas












i

---

### Post by croxi on 2007-05-07
have you tried to reinstall the drivers for your DVD?

if you've done that then it should make things a little easier for you...

---

### Post by teddybairs1 on 2007-05-07
Did you install the dvd-rom or did someone else? Could it be your cable?

---

### Post by halligan46 on 2007-05-07
Hi all

Someone on another post suggested that since my dvd-rom was an ide device and my hdd's are sata I should get an adapter to convert the dvd drive to a  fit a sata port.  I am going to undo this as I don't get anywhere with this.  I have noticed when I get into my bios the dvd-rom is first in the boot sequence however when I look a my drive configuration the dvd-rom shows but is on a port that is not open and I am unable to change it.  

Should the fact that the dvd drive is IDE render inoperable on my system?  everything else seems to work fine, movies, music etc.
I tried updating the driver but it is current.  I will remove the adapter and double check the cables and try again. 

If anyone else is using the intel dg965wh mobo could you let me know what setting you are using in your BIOS.

It is frustrating to be stumped by something that is probably a very simple fix.

Thanks again

Jimthomas

---

### Post by halligan46 on 2007-05-07
sorry to keep harping on the same problem,  I removed the ide to sata adapter from the dvd drive, double checked all my cables.  the dvd drive is now hooked up to the ide port on the mobo.  dvd is number one in the boot sequence.

inserted the dvd from shipit, rebooted and got to the ubuntu installation screen.  selected run/install and the following message appeared after about 30 seconds of watching the progress bar go back and forth:


/bin/sh: can't access tty; job control turned off
(initramfs)


wtf? do I do now?

thanks again
Jimthomas

---

### Post by oilchangeguy on 2007-05-07
read this:
[http://ubuntuforums.org/showthread.php?t=323136&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off+%28initramfs%29](http://ubuntuforums.org/showthread.php?t=323136&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off+%28initramfs%29)

---

### Post by halligan46 on 2007-05-07
okay,
 I removed my second hdd and am still having the same message appear, I have also tried to load Xandros andthat does not work either. Should I try any of the other options on the ubuntu start up screen.  I truly hope this is better than windows when I finally get it to work,so far ubuntu to me is all hype...it  should not be this difficult to load.

Jimthomas

---

### Post by halligan46 on 2007-05-08
I'm Still trying..... I guess my frustration was showing in my earlier posts.
since my last post I have tried an alternate install, I got to the point where I ran into this message, which seems to be the root of my problem.  In the detect and mount cd-rom I find this  MANUALLY SELECT CD_ROM MODULES.  I'm am asked for a floppy to load these and there is none and when given the option to manually select modules I don't know what these are or where to find them.

I suspect that this is a "hardware problem more than a software one.

Is it possible that burning my own cd as an iso image will work rather than the shipit disc I ordered?

Thanks again

Jimthomas

---

### Post by teddybairs1 on 2007-05-08
What's your motherboard spec? another guy on another post had the same problem with an ASUS motherboard, and I think another thread said something about it being a weird disk interface problem.

---

### Post by halligan46 on 2007-05-08
sorry for the multiple posts.

I have an intel DG965WH motherboard,dual core2 6400 cpu and 2gb of ddr2 6400 ram, one seagate 300 gb hdd and a plextor PX750-A ATAPI (E-IDE) dvd drive.

My dvd drive seems to handle everything except the live cd for ubuntu. It is a disc from shipit.

I need ,I think to detect and mount the cd-rom?

Thanks
Jimthomas

---

### Post by kyphi on 2007-05-11
Hello again Jim,

Sorry to read that you have had no success.

I too have an Intel DG965WH motherboard, a dual core processor, two SATA II hard drives and two DVD-RW drives.  The Marvell IDE controller on the mobo is the culprit that Ubuntu is at loggerheads with and the only way I could find around that was to install an IDE to SATA adapter.

The end result of that was that I have two DVD-RW drives recognised by XP but only one recognised by Ubuntu because, strangely, a second adapter did not work the same way.  I must admit though that I have not tried it in different ports.  Please be aware that the adapter needs to have power connected to it and there is usually a spare connector available from your power supply.

Here is some information as to how my BIOS is configured:

In Advanced, Drive Configuration:
ATA/IDE Mode               <NATIVE>
Configure SATA as       <IDE>
S.M.A.R.T.                     <ENABLE>

SATA Port 2                  <Pioneer DVD-RW>
SATA Port 4                  <ST380811AS>
SATA Port 5                  <ST380811AS>

In Boot:
Boot Menu Type            <ADVANCE>
Boot Drive Order           <Legacy Floppy>
                                      <Pioneer DVD-RW>
                                      <Pioneer DVD-RW>
                                      <ST380811AS>
                                      <ST380811AS>
After that,  Boot to Optical Device is <ENABLE> and Boot USB Devices First is <DISABLE>

I am expecting another DVD-RW drive any day now (SATA) and hopefully that will give me the two DVD-RW in Ubuntu that I need.

Since we both have similar systems, try my Bios settings.

---

### Post by halligan46 on 2007-05-12
Hello All

Thanks for your patience and input, my install problem is now solved!  I had been using an live CD for 6.10 I received online and had absolutely no success in installing UBUNTU at all.  Today I received a 7.04 DVD from linuxcd.org, and within 30 Feisty was up and running without a single hitch in the process!

I do not have a clue as to why the problem with 6.10 , however I am a happy camper now.  The real learning begins.

Thanks for listening to me complain for so long, and for all of your advice.

UBUNTU-INGLY 
Jimthomas

---

