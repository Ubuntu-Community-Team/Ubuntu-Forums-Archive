---
title: "n00b with internet trouble on IBM T22 with aPCMCIA wireless, and a build-in netcard."
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by tntc1978 on 2006-01-19
I&#8217;ve been roaming the forums (and wiki&#8217;s: [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)) for an answer, but alas no luck. I&#8217;m a n00b so be gentle. The problem is as follows. 

I&#8217;m using an IBM T22 laptop computer with an integrated Internet card (which PCLinuxOS found when I installed that OS, but I prefer Ubuntu, so I thought I would give the forum a try before embracing the KDE look in PCLOS). Beside this I also have a wireless PCMCIA card that neither Ubuntu or PCLOS has been able to recognize yet. With Ubuntu I&#8217;m unable to access the internet with either netcards

When I click: Click System->Administration->Networking I only see my Modem

When I type &#8220;lspci&#8221; in the terminal I get, among other things:

0000:00:03.0 Ethernet controller: 3Com Corporation 3c556B CarBus [Tornado] (rev 20)
0000:00:03.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 20)
0000:06:00.0 Ethernet controller: Realtek Semicinductor Ca., Ltd. Rtl8180L 802.11b MAC (rev20)

I think the first and second one is my modem I think (funny enough, since that&#8217;s what it say) and the last one is my Wireless PCMCIA I think...

I appreciate all the help I can get.
Kind regards
Thomas

---

### Post by carlosqueso on 2006-01-19
The modem and the wired ethernet have the same manufacturer, but don't appear to be the same card.  The bottom is your wireless card. In fact, it's the same one I use.   [http://www.ubuntuforums.org/showthread.php?t=96989](http://www.ubuntuforums.org/showthread.php?t=96989) may help, but if you don't have internet on Ubuntu, you'll need to get the ndiswrapper-utils package from [http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils) first and install it manually with ```
sudo dpkg -i <name of file>
```  As far as your wired internet, someone else will have to help, because I don't know.  

EDIT: made the command right, since I'm too sloppy to do it right in the first place.

---

### Post by tntc1978 on 2006-01-19
Thanks for helping Carlos but I'm kind of lost in a couple of things :-)

1. which one am I supposed to download?
2. I'm also uncertain of the command I'm supposed to write. The dpkg -i should be followed be the path of the file right?

Sorry for my ignorance

---

### Post by carlosqueso on 2006-01-19
1.  You need to download the package that corresponds to your processor architecture.  Type ```
uname -r
``` and download the file that corresponds to the last number that that gives you.  If you're wondering about the drivers, they're on the bottom of my post.

2.  you are correct.  they should be in your home directory or on your desktop.

3 Don't be sorry for your ignorance.  I was much like you only a few months ago.  This is how you learn :-).  By the way, Copenhagen's awesome, I lived there for 6 months and loved it.

---

### Post by tntc1978 on 2006-01-19
I think I've figured out which one to download: [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb)

Now all I need is to figure out the command :???: 

when I try: dpkg -i ndiswrapper-utils_1.1-4_i386.deb and the file is on my desktop I recieve a error saying that it can't access the archive.

---

### Post by carlosqueso on 2006-01-19
DOH! you need to put sudo before that.....my bad.  What's bad is I was just using dpkg yesterday.

---

### Post by tntc1978 on 2006-01-19
I still get the access error, in Danish though :-)

I write this line:
sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb 
(coresponding to the file on my desktop). I get prompted for the password and then it says no such file or archive.

Nice to know you liked it here in Copenhagen? Where you here for business or pleasure?

---

### Post by tntc1978 on 2006-01-19
Wait, I moved the deb file to my directory instead of desktop, and that did the trick \\:D/

---

### Post by tntc1978 on 2006-01-19
I do this: 
sudo ndiswrapper -i NET8180.INF

I get this output:
cp: can not complete stat () 'net8180.inf' No such file or directory.

I write the same command again, and it says:
net8180 already installed. Use -e to remove it.

I write:
sudo modprobe ndiswrapper

and the reply is:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Any thoughts?

sudo ndiswrapper -l gives:
Installed ndis drivers:
net8180 invalid driver!

---

### Post by carlosqueso on 2006-01-19
Did you memember to capitalize everything? Linux is case sensitive.   Also, make sure that the rtl8180.sys file is in the same folder as the INF file.  Try removing the driver and doing what I just said.

I was in Copenhagen nominally for school, so really for pleasure.

EDIT: are you in the directory to which you unzipped the files? That may be important too.

---

### Post by tntc1978 on 2006-01-20
I tried to respond a couple of times last night, but the forum was down.

I'm happy to say that it was a success :D

It must have experienced the problem because I didn't think about the uppercase case :-)

A huge thanks to you Carlos, you saved the day (night). Now I'm flying with my laptop. Now I just need to install my build-in card, but I'll wait, because I mostly use the wireless.

Again, thanks a bunch.
Thomas

---

### Post by carlosqueso on 2006-01-20
'tis what we're here for.  The case-sensitivity bugged the heck out of me coming from Windows (and DOS), so I know how you feel.   Enjoy!

---

### Post by tntc1978 on 2006-02-20
After a bold, but failed adventure into Dapper I did a fresh install of Breezy, but now I cannot get my wireless working again.:-| 

I've done it all to the detail... but no luck.
```
lsmod | greb ndis
``` gives me:
> ndiswrapper 114376 0
usbcore 104188 3 nidswrapper,uhci_hcd

```
ndiswrapper -l
``` gives me
> Installed ndis drivers:
net8180 driver present, hardware present

Any thoughts?

---

### Post by tntc1978 on 2006-02-20
After several reboots I succeeded in finding my network, even though my other computer finds the signal very easilly... :rolleyes:

---

