---
title: "Distro of choice."
date: 2011-09-16
forum: Any Other OS
---

### Post by jerinian on 2011-09-16
Hi everyone! I have many questions that i wish someone could answer here.
  I don't know which distro will offer me these features: i want a distro that you can play many audio and video formats right away without downloading audio/video plugins, a distro that has compiz and emerald already installed, and graphics driver installed like ati catalyst.
  Because i've already tried Sabayon 5.5 i was really excited to use this but the problem is, it revert back to it's original UI or settings after i logout/in, the settings for emerald is not save, yes sabayon can play mp3 and avis right away, i like that, umlike ubuntu, you have to download everything. Internet connection is not forever affordable at my place, i've tried using ubuntu download script but it think it's not the best. And on Sabayon 5.5 it says that it is not activated? It's not the exact line but it says not activated. I still have many question that needed answering but these are all for now.
   Thank you for the time reading my thread. I hope someone could point me to the right distro i fit. :D

---

### Post by NightwishFan on 2011-09-16
> Hi everyone! I have many questions that i wish someone could answer here.

You will probably get many answers/opinions in the next few hours. Be prepared. :)


> i want a distro that you can play many audio and video formats right away without downloading audio/video plugins
Trust me, having them 'available' is good enough. Having them already installed is a violation of laws in some ignorant places. (Where I live).

Some distros like Mint have them already installed though. I think Mepis has them already installed as well, been a while since I have used it someone can correct me if I am wrong.

> , a distro that has compiz and emerald already installed, and graphics driver installed like ati catalyst.
I am not sure how many distros would automatically enable proprietary drivers? Mint/Mandriva perhaps. Emerald is a dead project but some distros like Ubuntu have it included.

> Thank you for the time reading my thread. I hope someone could point me to the right distro i fit. :D
Any general purpose distribution should probably do. Why worry about having everything pre-installed when it is so easy to download and install? Find a distriubtion that has the software you like (available not installed by default it is **easy to install**. Has a release schedule that fits you, or a focus that suits your needs.

Try:

Fuduntu
Linux Mint (yeah I am actually recommending Ubuntu Green Edition :p )
Mandriva?

---

### Post by jerinian on 2011-09-16
Thank you for the reply, i want it pre-installed because i don't think i have access to internet forever, there will come a time that i'll get broke lolz :D and i can't pay for it anymore, so now i'm looking for a distro that has many features, maybe it's impossible for the Ati Catalyst to be included in a dvd distro i think it's ok. A distro with emerald, compiz, flash player, audio and video plugins pre-installed will do :D
Many thanks again for the reply, i appreciate it :)

---

### Post by NightwishFan on 2011-09-16
If you have no internet I suggest you download/purchase (very cheap) a DVD distro. I use and recommend Debian though it will not have proprietary drivers installed by default it will have most codecs (except x264 **en**coding and libdvdcss2). Those are easy to get offline (dvdcss2 is a single deb file from debian multimedia)

It will not have compiz installed by default but it may be on the dvd. I am not sure. But few distros will except ubuntu and maybe mint. I do not like [COLOR="PaleGreen"]Mint[/COLOR], but if it has a DVD it might be your best bet. I know it has codecs installed. I do not know if it offers a dvd or not.

This is not technically "official" however this product was made by a Debian developer and I do highly recommend it. Get the once for your cpu arch (32 or 64-bit) not the "multi-arch" because the multi arch will not have all of the codecs likely.
[http://raphaelhertzog.com/products/debian-cd-dvd/](http://raphaelhertzog.com/products/debian-cd-dvd/)



It is possible to download programs offline and burn them to a installable cd (for debian based distros) using AptonCD. It is in the repos for each of them.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by drawkcab on 2011-09-16
I second the Mint recommendation.

---

### Post by sanderd17 on 2011-09-16
There is no OS that has more features (some call it bloat) than Pinguy OS.

[http://pinguyos.com/](http://pinguyos.com/)

---

### Post by Dangertux on 2011-09-16
Have you considered creating an apt on cd archive or perhaps a local mirror on your network so the packages you want are available for when you don't have Internet access?

---

### Post by Megaptera on 2011-09-16
> **sanderd17 said:**
> There is no OS that has more features (some call it bloat) than Pinguy OS.

[http://pinguyos.com/](http://pinguyos.com/)

Except for the Ultimate Editions (if I'm OK mentioning them?)
[http://ultimateedition.info/ultimate-edition/ultimate-edition-2-6/](http://ultimateedition.info/ultimate-edition/ultimate-edition-2-6/)

That's their LTS edition I've linked to btw.

---

### Post by jerinian on 2011-09-16
Thank u, i'm going to research now how to do that apt for cd. :D

---

### Post by jerinian on 2011-09-16
I've never seen or used Pinguy before, but it looks cool, i'm gonna give it a try, i hope it can be installed inside windows?

---

### Post by jerinian on 2011-09-16
Thanks! :D

---

### Post by Mitjaa on 2011-09-18
Try this [http://www.zegeniestudios.net/ldc/index.php?firsttime=true](http://www.zegeniestudios.net/ldc/index.php?firsttime=true)
It's an online quiz that helps you to choose your linux distro.

---

### Post by spidi123q on 2011-09-19
Icefeast Linux can offer you the most you want.it is made to simple
and have all a user want
give a try to it):P
[IMG]http://dl.dropbox.com/u/27936650/icefeast/na.png[/IMG]

---

### Post by Flymo on 2011-09-21
Hi Jerinian - good luck in your quest!

I'd say +1 to Ultimate Edition, based on a 10.04 LTS installation I did that has been running well without tech support (me) for over a year on a relative's machine.  LTS is 'Long Term Support'.

Pinguy OS looks good, too, but I have no personal experience other than playing with it live. Seems to work OK on my hardware (Intel T5600, 2GB RAM, nVidia Go 7600).

Would **not** consider the 'Icefeast' (above) as suitable, since it looks to be very new.  Expect bugs!  Leave that for when you want to experiment rather than use for reliable daily stuff.  Even Ubuntu has a load of updates soon after a new release.  That's to be expected.

Most Linuxes can be used from inside Windows using virtualisation (KVM/Qemu, VMware, VirtualBox, MS Hyper-V, etc, etc), and there used to be something called Wubi for Ubuntu (& some derivatives) that did a similar trick. Not sure if it's still around.

That's OK for when you are sorting out what you want to use daily, but can be a bit limiting for regular use in my experience.  This is not a particularly fast machine, so your mileage may vary.

There's a better solution, in my view.

About 3 1/2 years ago we got XP running in Qemu under Ubuntu to our entire satisfaction; this to my mind is the logical solution to aim for.

The fragile, crash-prone, easily infected Windows OS is protected from internet nasties by the industrial-strength battle-hardened Linux (Google for SeLinux and AppArmour and IPtables for more info).

This allows Windows to run safely in a sandbox without all the aftermarket toot that it needs before it is safe to stroll around the World Wide Web, since it now never needs to go there.

Upshot is (even on a spavined Celeron 540) XP ran fractionally faster under Qemu/Ubuntu than on bare metal. Very surprising!

This is because it was (and always would be, every day) a fresh virtual installation with all the now-unnecessary processes disabled, and no aftermarket anti-malware or other stuff dragging it down. 

Pity is that we've hardly ever used it, since we just don't use Windows any more.  :P

So although you may find that running Linux under Windows is a bit sluggish (depending on your hardware) long term you can plan for a Linux machine with (eg) Tiny XP in KVM/Qemu or whatever virtual system you prefer. 

HTH, Ben

---

