---
title: "Lubuntu and Eeepc"
date: 2011-10-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by vancheese on 2011-10-14
Hi People

I'm running an original EeePC 900A with ubuntu remix LTS. The main problem is that the 3GB is rapidly filling up with only 30 mb free.

How does LXDE run on a EeePC 900A and how much hard disk space does it use?

Thanks for any pointers

Andy

---

### Post by renehasekamp on 2011-10-18
Hi,

I have an EeePC 701, with 4 GB, and in the weekend I installed lubuntu 11.10 on its sdd. It works very,very well!
But there was one problem: If you run the installer fron a usb stick, it stops while configuring apt. 
The solution is to burn a bootable cd from the iso and install it from that. You need a usb cd/dvd drive for that. Like booting from an usb stick, press ESC when you see the Asus logo, put the cd in, choose the cd drive and press ENTER. That's it. Installation takes about 45 minutes. 

It is a silly bug that installation from a usb drive stalls, that should have been discovered! 

Anyway, it (lubuntu) runs like a charm from the eee pc.

---

### Post by zhogan85 on 2011-10-18
Even Lubuntu will fill up your 3gb pretty fast, I'm afraid. Have you considered installing your OS of choice (Ubuntu/Lubuntu/whatever) onto an SD card? I know that's a common solution many people with small SSD take. There are several threads detailing this, nothing a little Google can't help with.

---

### Post by vancheese on 2011-10-18
I was just wondering if there is a way to strip ubuntu down some more - I know there are other flavours ....
The SD card is an excellent suggestion

---

### Post by zhogan85 on 2011-10-18
As far as stripping down goes, it might be easier to do a minimal install, and only install the packages you want.

---

### Post by Plumtreed on 2011-10-18
It looks like a lot of these 'new' editions are a bit too heavy for these small eeePCs and it takes a bit of tweaking to shoehorn them in effectively.

PeppermintTwo is ideal and installs well under the 4GB...less than 2GB. It assumes you are going to rely on the cloud for many things. This makes good sense with the eee!

Fuduntu is an excellent choice but needs work to trim it down, easily done with help from the Fuduntu forum. Everything on the eeePC701 works and Fuduntu includes Jupiter to improve battery 'duration'....Fuduntu feels like it was made for the small eees.

By making the exterior SSD your /home file you save a lot of headaches.

---

### Post by kalehrl on 2011-10-19
This how much space my lubuntu 11.10 takes:

```
root@lubuntu-laptop:/home/kalehrl# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  2.8G   32G   9% /
udev                  241M  4.0K  241M   1% /dev
tmpfs                 100M  764K   99M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  248M     0  248M   0% /run/shm
```

I upgraded it from 11.04 and used bleachbit and it cleaned up 1GB of space.
So now my lubuntu only takes 2.8GB of space.

---

### Post by amjjawad on 2011-10-19
I just don't get it? why can't they use larger than 3GB?

Anyway, even if you'll go for another distribution, by time, you'll run out of space.

Lubutnu will take less than 3GB but soon, you'll run out of space.

It's NOT smart IMHO to use external media (USB, HDD, etc) because that will reduce the speed (such media will run in less speed than your internal HDD) but looks like there is no other choice :)

---

### Post by zhogan85 on 2011-10-19
> **amjjawad said:**
> I just don't get it? why can't they use larger than 3GB?

That's how big the OP's hard drive is.

---

### Post by amjjawad on 2011-10-19
> **zhogan85 said:**
> That's how big the OP's hard drive is.

I know. I was talking about the manufacture company ;)

---

### Post by kurt18947 on 2011-10-19
This may be an expensive option compared to the value to the eeepc but is it possible to install a larger SSD? In other words, is it a standard SATA drive or integral to the machine? The price of smaller SSDs, 32 GB or so, have come down quite a bit recently. The other option I was considering before I killed my eeepc a larger capacity class10 SDHC card to load an OS on. I learned that higher class #=faster read/write so that might be an interesting experiment. See how fast it is or isn't.

---

### Post by zhogan85 on 2011-10-19
> **amjjawad said:**
> I know. I was talking about the manufacture company ;)

My apologies then, sir (or ma'am).

---

### Post by amjjawad on 2011-10-19
> **zhogan85 said:**
> My apologies then, sir (or ma'am).

No need to apologize at all and I'm a "He" not "She" :)

---

### Post by Linuxisfast on 2011-10-20
The usb install bug is related to our ASUS netbook BIOS, on my Vaio it installs fine via USB. Unity Ubuntu 11.10 works brilliant on my small 1015-B with 2GB.

---

### Post by tartalo on 2011-10-20
I had one of these, I fell OP's pain. I used to remove Cups and everything related printing (Do you print from this netbook?), Compiz, Ubuntu Docs, games, Evolution, Pulseaudio ...

It was never enough, and there are too many huge packages that are stupidly marked as dependency instead of recommendation (You can't uninstall the weather applet without uninstalling all the Gnome applets? really?)

This dependency madness has gotten worse with every new Ubuntu release.

zhogan85's recomendation makes a lot of sense. Avoid Gnome and go for a small DE (LXDE was good enough for me). 

Another distro as Puppy Linux might be a solution too, I didn't try it myself though.

EDIT: Ah, you are already using LXDE.

---

### Post by niteman on 2011-12-13
> **kurt18947 said:**
> This may be an expensive option compared to the value to the eeepc but is it possible to install a larger SSD? In other words, is it a standard SATA drive or integral to the machine? The price of smaller SSDs, 32 GB or so, have come down quite a bit recently. The other option I was considering before I killed my eeepc a larger capacity class10 SDHC card to load an OS on. I learned that higher class #=faster read/write so that might be an interesting experiment. See how fast it is or isn't.

I know this thread is a little old, but thought I may chime in. I too have a 900a, and still use it. It works quite well actually. It is possible to replace the horridly small SSD. I picked up a 16g Runcore on Ebay for just shy of $50. Works beautifully. 

I actually only decided to replace the 4g SSD because it started acting wonky. Prior to replacement I had run Crunchbang 9.04 for a long time with 1.4g of space left. I eventually ran vanilla Ubuntu 9.10 and stayed with that until I replaced SSD. Now, with 16g to play with, I could run pretty much any Linux distro with room to spare. 

I really have a strange attachment to this little machine. It's just built so well for what it is.

---

### Post by vancheese on 2011-12-14
Thanks for commenting - I too have a soft spot for these machines too.
Can you tell us what/where memory/hd you used? I can't find out which type to buy. Is there a bios limit?

---

### Post by amjjawad on 2011-12-14
> **vancheese said:**
> Thanks for commenting - I too have a soft spot for these machines too.
Can you tell us what/where memory/hd you used? I can't find out which type to buy. Is there a bios limit?

If your machine is still under warranty, try to check with the dealer you bought it from and see if they can replace some part because that would be easier for you.

I too feel and understand your situation. Lately, I got Lenovo G570 which has everything I want except it's Web Cam is SO BAD that I can't use it at night :/
It's my mistake, I was looking for a brand name more than hardware specifications so I blame no one but myself. Next time, I'll do my homework really good :)

Hmm, do you have External HDD? I know the performance is going to be slower but at least that will save some money for you in case you are short of money (like me :P) :)

---

### Post by MSEslacker on 2012-01-17
Just wanted to throw my 2 cents' worth in.
I picked up a 900a on the woot.com special back in '09.
The pre-installed Asus-Xandros OS was ... awful, and I pretty much shelved it for 2yrs.

I pulled the eeePC out recently and started messing around with Linux distributions.
I've had a pretty good experience running a Xubuntu Live distribution from an 8GB USB flash drive.  I started out with a 2GB "persistence" file (which stores the /usr filesystem), to get a feel for how the OS would perform with only 4GB of SSD.  It worked surprisingly well.  The distribution's files only required 670MB, and 2GB was more than enough for the packages I wanted to install.

But, apparently, the Live distributions are compressed when they install.
I was very surprised when I installed to the SSD, and the OS files occupied 2.5GB.  And the OS allocated itself 1GB for swap.  There wasn't even enough free space left to install the first round of updates.
If I could figure out how to install the OS compressed (as in the Live distro) to the SSD, that's exactly what I'd do.

But, I can't figure out how to do it.  So, I'm looking into upgrading the SSD.
I'm considering this 32GB SATA mini PCIe drive:
[www.mydigitaldiscount.com/mydigitalssd-32gb-50mm-bullet-proof-msata-ssd/]("http://www.mydigitaldiscount.com/mydigitalssd-32gb-50mm-bullet-proof-msata-ssd/")

Next question is: will my BIOS support it?
Apparently, yes.  Seems SATA support was introduced in v1006, according to *users.telenet.be/tom.alderweireldt/Eee900-en.pdf*.
I've got BIOS v1103.  Most recent available from asus.com is 1102.   So, I guess I'm ahead of the curve there.  v1103 might have been installed by Asus during an RMA repair/replacement incident...   Anyway, v1102 and v1103 should support SATA SSD drives.

Another thing about the Live distributions is that they never run fsck to repair the /usr filesystem.
Since I still have that cramped Xubuntu install on the SSD, I can use it to run fsck on the USB stick's persistence file periodically and clean up the ext filesystem with:
sudo fsck -y -t ext3 /media/[drive]/casper-rw
as per:
[http://askubuntu.com/questions/18466/how-can-i-repair-casper-rw-file-system-file-in-liveusb](http://askubuntu.com/questions/18466/how-can-i-repair-casper-rw-file-system-file-in-liveusb)
Otherwise, the casper filesystem tends to self destruct after a dozen boot cycles or so.

_________________________________
Asus 900a | Atom N270 Hyperthreaded, 2 logical cores, 1.6GHz | 1024x600
1GB DDR2 | [32GB  MyDigitalSSD mSATA SSD]("http://www.mydigitaldiscount.com/mydigitalssd-32gb-50mm-bullet-proof-msata-ssd") | Xubuntu 11.10 | BIOS v1103

---

### Post by rrashkin on 2012-01-17
I have a eeePC 701 with 4G of drive.  I'm currently using EasyPeasy but it's pretty full.  I get periodic messages that I only have 300-odd MB of available disk.  Since I use an SD card for data, I'm just living with it.  

Now I'm thinking of going to Lubuntu using the Alternate ISO (since that's recommended for smaller environments).  This thread, however, has given me pause.  I don't have an external CD reader so a thumb drive is really my only option.  Does anyone know if there's any way to get Lubuntu to install from a thumb drive onto an ASUS eeePC?

One question in this regard is whether to use Universal-USB-Installer-1.8.6.8.exe (which is what I got from links on the Ubuntu site)or unetbootin-win-549.exe (which I got somewhere else)?

---

### Post by MSEslacker on 2012-01-17
rrashkin,

I used Universal USB Installer v1.8.7.3 to install several Ubuntu variants to USB flash drives.
When you boot from the USB drive, with whatever "*buntu" flavor, there should be an icon on the desktop labelled "Install *buntu".
That's how I did the Xubuntu install to my SSD drive.
And it worked.  Smooth sailing, except for the space constraint.

Universal USB Installer provides a "persistence" option that UNebootin  doesn't seem to offer.  That lets you save changes to the Live environment, like retaining installed packages, across reboots.
Of course, the persistent casper-rw filesystem  tends to self destruct before too long, if you don't manually run fsck on it from time to time...   (see my previous post)

Since the Live distribution on the USB drive seems to get by fine  without a swap partition, you can probably reduce the size of the swap  partition that the OS installs and recover some space that way.

I don't know how you're using the SD card right now (and I don't know  how flexible the installer will be) but you might consider getting a  fast SD card ("class 10", "133x", or better) and making it a permanent  part of the system by putting the /usr filesystem on the card, so that  packages and libs install there, instead of on the internal SSD.

There are several netbook and eeePC-specific distros out there (Lubuntu,  Peppermint OS, Ubuntu-eee/Easy Peasy, Leeenux, Eeebuntu/Aurora OS,  etc.).  I'm really not clear on the differences.  All are supported by Universal USB Installer...except for Aurora, which has its own installer.

Post back and let us know how the Lubuntu alternative ISO works out on your eeePC.

---

### Post by rrashkin on 2012-01-18
Thanks, I will.

---

### Post by bpb101 on 2012-01-18
easiest solution is buy a ssd  12 gb , want cost a huge fortune
if you can find ssd that  is that low now of days

or  a  1.8' hard drive can fit in them , 

[SIZE=1]although ive only ever seen a 1.8' hard drive once[/SIZE]

---

### Post by rrashkin on 2012-01-18
The EASIEST solution is to use Puppy Linux and bypass the SSD altogether. I just would rather have an Ubuntu system on it.

---

### Post by Plumtreed on 2012-01-19
> **rrashkin said:**
> The EASIEST solution is to use Puppy Linux and bypass the SSD altogether. I just would rather have an Ubuntu system on it.

You may have heard of 'Leeenux', Ubuntu based, and seems to be aimed at eeePCs.......looks promising and you might find it something to work with.

---

### Post by rrashkin on 2012-01-19
I'll keep that in mind but I think I'll try Lubuntu first.

---

### Post by Plumtreed on 2012-01-19
> **rrashkin said:**
> I'll keep that in mind but I think I'll try Lubuntu first.

.......you might want to add 'Jupiter' no matter what you decide....it is ideal for the eeepc...extends battery time etc....but google 'webupd8 Jupiter' for the best way to install on Ubuntu based OSs and more details.

---

### Post by rrashkin on 2012-01-23
I tried loading Lubuntu this weekend, both regular and manual install.  In both cases, the actual install was fine but Lubuntu failed to recognize my wireless.  I tried a couple of things but -- well -- I'm back to EasyPeasy.

---

### Post by rrashkin on 2012-01-30
I hope this isn't considered heresy but the solution for me is Bodhilinux.  It's based on Ubuntu but it's ultra-lite.  When it's installed, it initially takes up only 1.3Gb, but, then, it doesn't have any software to speak of, only a lite browser (Midori) and a file manager, text editor, and terminal.  I loaded gnumeric, abiword, and inkscape, and now I'm up to 1.5Gb.  Granted, it uses the Enlightenment desktop and that's not a whole lot of fun but it works for me.

---

### Post by Plumtreed on 2012-01-30
You made a good choice with Bodhi & Enlightenment because they are very 'lightweight' and use only a small amount of the available space.

One thing I have found with the eeePC is that, when you have only 4GB, it makes no sense to carry around empty disk space so mine is always maxed out! I also clean out all the extra language files and 'help' documents that I don't and will never use.

I have a /home file on the 'external' 2GB drive and frequently use 'Bleach-Bits' to keep things clean.

I have found Fuduntu the ideal OS for my eeePC because it has pre-installed Jupiter, which maximises battery time, and all the function keys work the way they should. It runs a bit on the large size but I can't see much value in having excess blank space on a 4GB drive.......and wifi & mobile broadband works!

---

### Post by amjjawad on 2012-02-01
> **rrashkin said:**
> that's not a whole lot of fun **but it works for me**.

The point is: use whatever works for YOU :)

If you need any help with Lubuntu on another machine, I'm here ;)

---

### Post by Flazer on 2012-02-01
Just as a comment to one of the questions posted.  I had no problems putting the latest stable release of Lubuntu, or any 'buntu' on a USB stick and installing or running a live cd environment.

my eeepc is the 1005hab, so it has a larger HDD.

i'm having some other issues i'll post, but it seems to work great on this set up, much cleaner than any of the other 'buntu's.

---

### Post by Azyx on 2012-03-06
For a couple of days ago I start to use Lubuntu 11.10 to avoid gnome3 and unity on my home PCs(wow now VNC work great again :) ). I like it very much now and have just installed it on my eeePC 900, with 1GB RAM. Wireless, camera and stuff work fine. My only problem I have is how I power-manage. Can't find it under preference or system :( I want the computer to 'suspend' when it's on battery and the lid is closed, but when it's on AC only the sceen should went off. Another little thing is that I need to type password after suspend.

/Cheers

---

### Post by asw24 on 2012-06-05
I just completed the installation of Lubuntu 10.04 on my old EEE701 with the 4 GB drive. I am very happy to see it working. I do not need the latest software releases but like to have a small PC with the possibility to use my SD drive and USB drives. So far so good, just concerned how long the disk can be used before its is blocked through temp files. Sofar still  2Gb is empty so let us see.

Like I wrote: I do not need the latest software releases but am curious as to why it is recommended to stay with 10.04 but here I find several reports of people installing a later version on the same machine.

FYI: at home we use two desktops with only Ubuntu 10.04 installed. The next LTS version I plan to install after a few months. That will give time to iron out any major bugs.

---

### Post by Smerpette on 2012-06-06
Hi, 
  I am new to the ubuntu forums and I have been reading this sub-forum about Asus Ubuntu Support. While I have found it very interesting and a good read. I have an Asus Eee PC 1018PB with UNR installed and fully operational. I have Gnome GUI installed also. So I guess my question is or maybe not so much a question as an understanding. Why would you want to put a desktop version distro on a netbook when the desktop version won't match up with the hardware on a netbook and vise versa.  Hope I am not sounding like jerk it was not my intentions.

---

### Post by rrashkin on 2012-06-07
After Ubuntu stopped producing the UNR version (Lucid, I think), even though the claim was that the standard ISO would install correctly on limited platforms, I was unable to get it to work with my eeePC 701. I used EasyPeasy for a while but I prefer Bodhi.

---

