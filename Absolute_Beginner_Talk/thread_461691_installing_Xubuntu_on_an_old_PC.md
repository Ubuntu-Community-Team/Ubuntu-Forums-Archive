---
title: "installing Xubuntu on an old PC"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by disco2000 on 2007-06-01
ok. I have burned Xubuntu 6.10 ISO on a CD. I load my old laptop with it, it boots and then it tells me:

"Linux decompressing.OK Loading the Kernel.
(17179569.1840001) ACPI: unable to find RSDP."

and then blank screen and nothing more happens. My laptop is an AMD K6 3D 333Mh with 128Mb of RAM and a Hard Drive of 3Gb.It presently runs Win98.


Any help would be welcome

Danny.

---

### Post by drowner on 2007-06-02
Have you tried being there, 2 o'clock, at the fountain down the road?

---

### Post by hellmet on 2007-06-02
Why do you create duplicate threads??

---

### Post by disco2000 on 2007-06-02
Well, why not? Am I missing something here?

---

### Post by bone43 on 2007-06-02
Hmm?

[http://ubuntuforums.org/search.php?searchid=21316677](http://ubuntuforums.org/search.php?searchid=21316677)

Read back threw the your original posts theres plenty to get you started with out a new thread.:)

---

### Post by freefromXP on 2007-06-02
I am in the process of install Xubuntu on a dell pii 400 laptop.  What I did was download ubuntu 5.10 install server the install Xubuntu.

  I used this guide [https://help.ubuntu.com/community/InstallingXubuntu]("https://help.ubuntu.com/community/InstallingXubuntu")

Hope it helps

---

### Post by southernman on 2007-06-02
> **drowner said:**
> Have you tried being there, 2 o'clock, at the fountain down the road?
rofl...

Wait, is that some sort of cryptic code? Bahaha

---

### Post by ugm6hr on 2007-06-02
If you are using the LiveCD (DesktopCD) - that might be your problem.  

In theory, it should run on your system, but it might be better to try the alternate CD.  Otherwise, ensure you already have a swap partition before booting the LiveCD (that might help).  

But you will almost certainly not be able to install from the LiveCD anyway (only boot from it).  So you may as well use the alternate CD.

PS: Why not use Xubuntu7.04 rather than 6.10?

---

### Post by freefromXP on 2007-06-02
Well I used 5.1 because it requires a lot less ram to install and once I get it running from HD I can update.


  The newer versions require at least 196rm to install I believe.  Really really slow if it does install

---

### Post by disco2000 on 2007-06-02
with Xubuntu 7.04, it tells me the same thing: could not find RSDP. Then it goes thru a few lines quickly and finally tells me that:

"(initramfs) 6577.781610 hda:timeout waiting for DMA.
"6618.298546 hda:drive not ready for command"

and this is the live CD. I am just trying to boot the Live CD!!!!!

---

### Post by freefromXP on 2007-06-02
I think your system may not have enought ram or speed to run that.  I would to a 5,10 server install. then add Xbuntu (Xfce4) desktop to it.

   I just install Kubuntu 5.10 to a pii 400 nd it took a hour but it installed from install disk and work fine.  I am going to add Xubuntu .

---

### Post by disco2000 on 2007-06-02
thanks.

I'll try what you have described. I have read the installation procedure and it makes sense. I think I will also try the Alternate CD of Xubuntu 6.10 and see what it tells me.

Danny

---

### Post by ugm6hr on 2007-06-02
In case you haven't seen this:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Gives instructions on how to install desktop onto a server install (which I think is possible from any Alternate CD).  Also gives examples of other windows managers that are even lighter than XFCE.

---

### Post by sean4u on 2007-12-06
Old thread, I know, but since I've just gone through the labour pains of trying this...
HP Vectra P75, 16MB RAM, 700+ MB HDD

I got those initramfs messages from several distros, including Ubuntu, Xubuntu, Zenwalk, Slackware 12. DeLi and DSL (Dmn Small Linux) both installed, but maybe I've been spoilt by the beautiful thing that is Xubuntu (on my modern notebook), I wanted something 'wow'!

Just getting this old machine to the initramfs issue was difficult. It refused to boot from CDROM (although a DRDOS CDROM would boot). I used the excellent, but poorly spelt btmgr from [http://btmgr.sourceforge.net/](http://btmgr.sourceforge.net/), many distros that won't boot from CD on this machine can be booted by using the CDROM boot option after booting from btmgr on a diskette. They'll boot, but will die later in the boot process.

Eventually, I wondered if the common problem was the 2.6 linux kernel on all the distros that didn't work, so I dug out a Slackware 10.2 CD, and that worked a treat! I still couldn't install Slackware and X-windows on that HDD, just not enough room. Perhaps if I'd invested another few sleepless nights I could, but I had a spare 10G HDD lying around, and that works a treat as a second disk (swap partition and /usr partition) under Slackware.

The PC works a treat, it'll boot into XFCE, filling RAM and using about 20MB of swap, and using the basic XFCE utilities is ok - there are waits of up to a few seconds for things to start up, but it gives new wings to that old kit. A word of warning though: I installed firefox (it's the only browser I use, usually). It starts, but it took 20 minutes. I suspect that's almost certainly caused by the small RAM on ths PC. Dillo starts almost as quickly as any of the XFCE utilities, but surfing the web with a browser that says "I'm not displaying that, it's got errors!" might not be everybody's cup of tea! Or cup of Ubuntu.

With perseverance, btmgr and maybe an older ubuntu install CD, with a 2.4 kernel, you can save a PC like this from the dustbin. You'll need more memory than I have if you want recent windowing software to work on it. I'm sticking with Slackware 10.2 for the moment, just because installation was such a slow process. I use the Vectra as a headless development web server (Apache, Mysql, PHP and JRE), and it works a treat.

---

