---
title: "Am I missing something copying a DVD"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by tjpearson on 2008-01-06
Hello everyone,

Just installed ubuntu so still learning a lot but have a second problem and just wonder is it that I may just have some simple downloads missing.  

Using the pretty much standard stuff right, clicking on a DVD I select copy and everything seems fine until I need to then burn the DVD.  I'm requested to put blank disk in but no matter what format I use the system spits it out saying it is not compatable.  The strange thing is that on the menu that instructs to put in blank disk it asks to be sure one of the following formats are used but nothing is listed and this leads me to believe I might be missing something very simple.  

Anybody got any ideas, would appreciate the help.

---

### Post by bumanie on 2008-01-06
Install the kde program k9copy 
sudo apt-get install k9copy 
(I think that's the command line from memory)
Basically it is an open source version of dvd shrink and should do what you are after.

---

### Post by tjpearson on 2008-01-06
yes, thanks I got this, but once it copies the DVD it doesn't seem very happy burning a DVD as well, that's why I suspect I'm missing something else.  I'll give it anther go as this programme comes highly recommended.

---

### Post by bumanie on 2008-01-06
I think the output from k9copy is an iso file - right? If so, may be you should try to burn the iso with another program such as the default cd/dvd creator or k3b.

---

### Post by tjpearson on 2008-01-06
I get the ISO file but every time I try to burn this to disk it asks for me to put in compatable format but just won't accept anything.  

The box asking this says to use any of the following disk types but nothing is listed.

---

### Post by DocForbin on 2008-01-06
Sorry I can't help, but just wanted to say I've had this same issue since upgrading to 7.10. I even did a clean install. It just doesn't want to recognize blank DVDs.

btw, DVD Shrink runs fine in wine with a tweak or two if you prefer using it.

---

### Post by bumanie on 2008-01-06
Sorry, I have not come across this before.
This may sound silly, but how do you try to burn the disk. For cd/dvd creator all you have to do is right click on the iso and a drop box should give you an option to burn the disk. I have no idea what to suggest if you are already doing this.
PS: I don't know whether this is relevant, but I guess you have installed all the relevant (propriety) codecs.

---

### Post by tjpearson on 2008-01-06
Yes. doing exactly this bumanie, I get the option to burn to disk but just as DocForbin says, it just wont except any blank DVD's.

Thanks anyway, you have still helped and with Doc's reply I think I'll just give up on it for now.

---

### Post by DocForbin on 2008-01-06
Try doing sudo dmesg - c. Then put a blank DVD in and try to burn an iso. Then run dmesg, and post the output.

---

### Post by bumanie on 2008-01-06
May be it is an issue with gutsy (and may be some types of hardware or something), however, regularly viewing these forums, I can't recollect seeing the problem before.

---

### Post by tjpearson on 2008-01-06
oh my god Doc, you've lost me totally.  

Do you mean just type this in terminal and run it ?

---

### Post by DocForbin on 2008-01-06
tj, yeah, just type that in the terminal. You can copy/paste the output.

---

### Post by tjpearson on 2008-01-06
The system must recognise my drve cos it keeps spitting out any disc I put in.  I also get this message as below,

Please replace the disc in the drive with a supported disc with at least 4.3 GiB free.  The following disc types are supported:

Notice how no disc types are listed.

Here the terminal result, I've not copied all of it cos its a mile long:

[   38.080000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   39.380000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   39.380000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   39.380000] agpgart: Putting AGP V3 device at 0000:01:05.0 into 8x mode
[   40.732000] [drm] Setting GART location based on new memory map
[   40.732000] [drm] Loading R200 Microcode
[   40.732000] [drm] writeback test succeeded in 1 usecs
[   70.244000] NET: Registered protocol family 17
[   70.804000] ieee80211_crypt: registered algorithm 'WEP'
[   71.136000] SoftMAC: Open Authentication completed with 00:16:e3:d7:06:e3
[   77.828000] NET: Registered protocol family 10
[   77.828000] lo: Disabled Privacy Extensions
[   77.828000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   88.092000] eth1: no IPv6 routers present
[  155.572000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  335.588000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  395.596000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  455.596000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  515.604000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  575.604000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  635.612000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  695.612000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  755.620000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  815.620000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[  935.636000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1235.676000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1295.676000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1355.684000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1389.556000] cdrom: This disc doesn't have any tracks I recognize!
[ 1415.684000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1475.692000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1595.704000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1655.704000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1775.724000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1835.732000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1895.732000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 1955.740000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2015.740000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2075.748000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2135.748000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2195.756000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2255.756000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2315.764000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2375.764000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2435.772000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2495.772000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2615.788000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2675.796000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2735.796000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2795.804000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2855.804000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2915.812000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 2975.812000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3035.820000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3155.828000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3215.828000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3275.836000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3335.836000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3395.844000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3455.844000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3515.852000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3575.852000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3635.860000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3695.860000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3755.868000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3815.868000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3875.876000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3935.876000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 3995.884000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4055.884000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4115.892000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4235.900000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4284.868000] cdrom: This disc doesn't have any tracks I recognize!
[ 4295.900000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4355.908000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4415.908000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4475.916000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4535.916000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4558.988000] cdrom: This disc doesn't have any tracks I recognize!
[ 4595.924000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4655.924000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4715.932000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4775.932000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
[ 4955.956000] bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
tjpearson@TJPEARSO-PHHEZO:~$

---

