---
title: "General Usage Questions"
date: 2008-04-02
forum: Arch and derivatives
---

### Post by Masteroc on 2008-04-02
So i'm thinking of switching from Ubuntu to Arch simply because of the speed difference that i'm hoping it will yield. But before i switch i would like to know, in every day usage, what do you (the user) have to do that ubuntu would normally do for you. For example, if i put in an audio/data cd, would arch recognize it or would i have to mount it myself? I don't expect it to open and run an application, just recognize and mount it. Also, does it find network places like ubuntu, will it find the shared folders on my Windows computers and can it read NTFS? How hard is it to install network or local printers and maybe media players like an ipod? I know that arch is geared more toward the advanced user, and i don't mind learning how to configure things through conf files and learn how to set things up myself, but i just want to figure out if i will have to do everything myself...i mean like it common things that would just be annoyances (at least to me) like having to mount usb drives and cd's myself, etc. Any opinions would be great, on just general usage and setup of arch and any annoyances that you have found or things that ubuntu takes care of that you found out that you had to do on your own.

Thanks!

---

### Post by K.Mandla on 2008-04-03
Hmm. ... It can do all those things, but chances are you'll have to set it up to do them yourself, or use a desktop environment that makes allowances for some of those things.

For example, I use Arch on one machine and if I insert a CD, nothing happens. But that's because I use Openbox, and I don't have any utilities or daemons installed to mount CDs automatically. I do it by hand -- I could install something to do that if I wanted to, but I don't.

Is that a fair answer?

---

### Post by kpkeerthi on 2008-04-03
The answers to questions depends on what Desktop Environment you choose to use with Arch. I use GNOME. It automounts flash drives, audio CD (and blank/data discs) and even my iPod. I was able to sync my iPod with rhythmbox with absolutely no fiddling at all. 

I dont have any networked Windows machine or NTFS formatted drive... so can't say anything about it. But I'm sure GNOME should automount it read-only. If you need write support for NTFS or [SAMBA]("http://wiki.archlinux.org/index.php/Setting_up_Samba"), sure they are just pacman -S <what-you-want> away. Once setup, I see no reason to mess with it on a daily basis.

---

### Post by Littleweseth on 2008-04-03
I know that arch is geared more toward the advanced user, and i don't mind learning how to configure things through conf files and learn how to set things up myself, but i just want to figure out if i will have to do everything myself...i mean like it common things that would just be annoyances (at least to me) like having to mount usb drives and cd's myself, etc. Any opinions would be great, on just general usage and setup of arch and any annoyances that you have found or things that ubuntu takes care of that you found out that you had to do on your own.

Hai;

I use Arch on my desktop, running a KDE/Openbox session. First off, answers to your specific questions, as relative to my desktop (YMMV) :

----

Automounting : Courtesy of the services that KDE provides, CDs, USB drives, and my iPod are all automounted under /media with no manual intervention required.

Printers : KDE's Printer control panel applet provides a wizard for adding local or network printers, though I've never had to actually install a printer myself.

Finding network shares : Konqueror has an equivalent to windows 'Network Places' - autodiscovery of windows samba shares and so forth.

Note that Gnome (responsible for the same things in Ubuntu) also provides all of these services.

NTFS : All the required packages to read/write NTFS are available in the Arch repositories, namely ntfs3g (which is the one you want to use.) IIRC, this is what Ubuntu uses for NTFS support.

-----

Arch isn't really that much different from Ubuntu when it comes right down to it - my desktop has much the same stuff installed and running as an average Kubuntu install. Most of the common tasks you don't want to do manually (mounting removable media, etc.) are handled by the KDE or Gnome session managers, so if you're running either, everything should be sweet.

However, a base Arch install is really quite spartan, so it's what you install that determines your experience. I went for the full KDE desktop : if you go for something a bit more minimal - namely, you don't run a desktop environment of some kind - do expect to be doing a lot of manual tasks yourself. I ran Openbox without a desktop environment for quite some time (for speed reasons), and I did have to manually do a lot of things.

Finally : updating Arch packages can lead to breakage of various things once in a while, partially because there isn't quite as much rigourous testing and partially because of the rolling release system. As usual, Google is your friend (for googling up error messages), which you end up doing a bit more of as compared to Ubuntu.

Hope this helps :)
-lws

---

### Post by disturbed1 on 2008-04-03
> **Masteroc said:**
>  if i put in an audio/data cd, would arch recognize it or would i have to mount it myself? I don't expect it to open and run an application, just recognize and mount it.

Ubuntu did not invent this. It's called HAL. Gnome Mount reads HAL's output and does what you define it to do. In the preferences if you have it set to open VLC everytime a DVD is inserted it will. There are default HAL rules and Udev rules that define what goes on behind the scenes. 

 > Also, does it find network places like ubuntu, will it find the shared folders on my Windows computers This is Samba, not Ubuntu.

> and can it read NTFS? ntfs3g, nothing Ubuntu did.

> How hard is it to install network or local printersPrinting is done by CUPS (Common Unix Printing System) maintained by Apple. If there is a PPD file for your printer, it is supported.

The difference between setting up a printer in Arch and Ubuntu - Ubuntu when you plug in the USB cable it prompts you to add the printer, In arch you tell CUPS to find a new printer.


 > and maybe media players like an ipod?Depends on what software you want to use. If the software from Ubuntu worked with your iPod it will work the same in Arch.

> 
 I know that arch is geared more toward the advanced user, and i don't mind learning how to configure things through conf files and learn how to set things up myself, but i just want to figure out if i will have to do everything myself...i mean like it common things that would just be annoyances (at least to me) like having to mount usb drives and cd's myself, etc. ..........

> 
Any opinions would be great, on just general usage and setup of arch and any annoyances that you have found or things that ubuntu takes care of that you found out that you had to do on your own.

Thanks!Ubuntu didn't write the software. The Ubuntu process goes like this - (etremely dumbed down ;) )

Upstream (the actual authors of the software) release the code. Debian removes the stuff that doesn't agree to DFSG, attaches rules to the file so the depends are known, packages it as a deb file. Ubuntu takes the debian package add Ubuntu branding, further adjusts the rules to meet the renamed Ubuntu packages, maybe a patch/hack/slash here and there, then packages it as a deb file.

In arch the process is like this. Upstream releases the code - arch devs compile that code, you get the undiluted upstream version. Patches are only added if 100% necessary for core and extra packages. If you download the source file and ./configure && make you'll get the same thing as the arch package...........software the way the author meant it to be.

---

### Post by Masteroc on 2008-04-03
Thank you all for the responses, and i do know that it is not Ubuntu itself that does all these things, it is the distro in general that i was talking about, not spefically the ubuntu programmers who made it auto mount things and read ntfs. I was wondering if Arch did these things as well automatically (meaning that the core had the specified programs such as Cups and Hal to do this with). I am definitely going to give arch a try now (most likely with gnome). Thanks again for the help!

---

### Post by disturbed1 on 2008-04-03
You'd be surprised how many Ubuntu users believe Ubuntu (re)wrote the kernel, Gnome, and everything else that make a Linux Distrobution :D

You have to install these things. That's what makes Ubuntu different, they managed to group together a great number of packages to allow a decent OTB experience. With Arch, after the install, you're left with a command line system that you have to mold into how you want.

If you want printing, you have to
**pacman -S cups**
BUT..... that only gives you cups, not all of the printer drivers, the foomatic engine/ppds, not hpijs, not gutenprint, just cups. This is what I like. I don't own an HP printer, so there is no need for hpijs to be installed, loaded and running at boot time :)

If you want automounting -
**pacman -S hal**

Want Xorg?
**pacman -S Xorg**

Want gnome **pacman -S gnome**
But that gives you the basic gnome, you might want gnome-extra as well.

Have good read through the wiki, or least the installation guide.

---

### Post by Masteroc on 2008-04-03
Thanks disturbed (and all others in this thread), i will have a look at the arch wiki and hopefully be able to set my system up this weekend.

---

### Post by kpkeerthi on 2008-04-04
[Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") is all you need to get started. Be sure to print it out. Good luck.

---

### Post by Masteroc on 2008-04-04
Thanks, just for a quick update. I've gotten the cli base system installed and hopefully this weekend i can get the gui part done.

---

### Post by crimesaucer on 2008-04-06
With Arch I use Grip music ripper and player that plays audio CD's when you insert them with out having to mount them.

I also use NTFS-3g to read and write to my Windows Xp partitrion.

Some of my old DVD and CD's that I burnt in xubuntu don't play because of some block, but a simple:

```
mount /mnt/cdrom
``` 

will mount it instantly.

check this install guide: [http://www.raiden.net/?cat=&aid=276](http://www.raiden.net/?cat=&aid=276)

---

