---
title: "About to leave Windows for Ubuntu"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by blissend on 2006-07-06
Until I can build a separate computer for windows, I'm getting rid of it in favor of Ubuntu.

I have tried Ubuntu v5 before and it worked. My current setup is...
AMD Athlon 64bit 3000+
EPoX 9NPA nforce4 ultra
GeForce 6600 TF 128MB (gv-nx66128dp)
250GB sata150 WesternDigital (wd2500jd)

I face a few problems before I can do this. Hopefully I can get some help here before I attempt to make a changeover.

[LIST=1]
[*]I have tried the 64bit Ubuntu and it worked, but the 32bit version worked much better. Is that still the case for the current Ubuntu version?
[*]I have tons of music (+40gigs) on my Windows setup. How would I go about keeping that on the hard drive while getting rid of Windows in place of Ubuntu?
[*]How does one choose between Gnome and KDE?
[/LIST]

Anyway, any help would be appreciated. :)

---

### Post by Iarwain ben-adar on 2006-07-06
Hi,
well, about the 64-32 question i can't help much (i also have an 64 system, but i installed the 386 version of DD)

For your second question: you could make your partitions so that you can transfer your music to a Ext2 (or FAT32) partition. 

And the last question: it's al a matter of taste :D
I'm a Kubuntu user, just because the first DE was KDE (SuSE 6.x)
They're both as nice, so it's all up to you ;)


Iarwain

---

### Post by woedend on 2006-07-06
1 - to avoid headache use 32 bit
2 - resize your windows partition down, make a 100 gb or so ext3 partition.  Go back into windows, install the necessary ext3 drivers and move the files over.  Or, rather, you can install ubuntu alongside windows, then use it to move them from windows to the other partition.  But you do NOT want to keep using that ntfs windows xp partition.
my setup uses 100-120 gb for files, 3 for swap, and the rest for / partition of linux...thats it.
3 - you can install both.  but use gnome :p

---

### Post by atoponce on 2006-07-06
1) 64-bit is just odd.  Never have figured it out.  Use 32-bit (x86) Ubuntu.  You'll be glad you did.
2) Get an external hard drive, and store your music there.  Ubuntu will recognize the HDD upon immediate plugin.
3) Don't use either.  They're both bloated.  Install xubuntu-desktop.

---

### Post by ubuntu27 on 2006-07-06
> **blissend said:**
> Until I can build a separate computer for windows, I'm getting rid of it in favor of Ubuntu.

I have tried Ubuntu v5 before and it worked. My current setup is...
AMD Athlon 64bit 3000+
EPoX 9NPA nforce4 ultra
GeForce 6600 TF 128MB (gv-nx66128dp)
250GB sata150 WesternDigital (wd2500jd)

I face a few problems before I can do this. Hopefully I can get some help here before I attempt to make a changeover.

[LIST=1]
[*]I have tried the 64bit Ubuntu and it worked, but the 32bit version worked much better. Is that still the case for the current Ubuntu version?
[*]I have tons of music (+40gigs) on my Windows setup. How would I go about keeping that on the hard drive while getting rid of Windows in place of Ubuntu?
[*]How does one choose between Gnome and KDE?
[/LIST]

Anyway, any help would be appreciated. :)


1)The drawback about 64bit is that there are many apps that are 64bit compatible (Take Flash for example). Better use the 32 bit.   [Note: Windows is also not ready for 64bit]
2)DualBoot, and then in Ubuntu, mount your Windows partition, then copy your files to your Ubuntu's Home directory. After that you can delete Windows (with Gparted or Qtparted)
3)Now that's a personal choice. I choose Ubuntu because there are more documentation about it than Kubuntu or Xubuntu.  YOU decide.

---

### Post by simonn on 2006-07-07
> **blissend said:**
> 
[*]I have tried the 64bit Ubuntu and it worked, but the 32bit version worked much better. Is that still the case for the current Ubuntu version?


Same. I found the 64 bit version unstable (breezy) and i386 is just less hassle.

> 
[*]I have tons of music (+40gigs) on my Windows setup. How would I go about keeping that on the hard drive while getting rid of Windows in place of Ubuntu?


Get an external harddrive to use as a backup. No, really, back it up, keep a copy on your hardrive too!

> 
[*]How does one choose between Gnome and KDE?


Work out what applications you want to run. KDE is QT based, Gnome is GTK based. What are these things? They are graphical toolkits, the libraries that provide the windows, controls etc.

GTK is also GPLed (a type of open source license) which IMHO is morally superior to the other open source licenses. QT is not GPLed.

However, the GPL makes distributing a closed source application using open source code difficult, if not impossible, so you will find that a lot of commercial/closed source linux applications are QT based e.g. Skype, Google Earth etc. Another however, most of the time QT is statically linked to these applications so it makes no difference what you use.

In summary, make a list of what you want to use your computer for. Mine is roughly:

1) Web browsing/messaging
2) Programming
3) Music
4) Movies

I found that the better applications are generally GTK based (Firefox, XMMS, mplayer, Xine/Totem etc), so I went with gnome.

Find the software which does the task you want and then choose.

---

### Post by mssever on 2006-07-07
If you have the disk space, you might want to install both GNOME and KDE. KDE is much more configurable, and comes with cool sounds if you want them. It's also a little more Windows-like (talking about the default setup here). I personally prefer the GNOME interface though (maybe because I started out with GNOME years ago). Just choose whichever one you like best. The debates about which desktop environment is the best have become wuite heated many a time.

---

### Post by aysiu on 2006-07-07
> **blissend said:**
> How does one choose between Gnome and KDE? You choose Gnome--not because it's "better" (though many will argue that it is)--but because most people offering help on these forums will assume you're using Gnome, and they will also know more about Gnome...

... in other words, as a new user, you will get the best help you need to get set up.

If you later want to add KDE, it's trivial to do so. Then you can switch back and forth as needed.

If you're really curious about the differences, read this:
[http://www.psychocats.net/ubuntu/kdegnome.html](http://www.psychocats.net/ubuntu/kdegnome.html)

---

### Post by blissend on 2006-07-08
Wow, support here is truely amazing! Many thanks to every that replied.

I have decided to use 32bit ubuntu gnome (love gpled stuff) while storing my music on a separate hard drive. The separate hard drive only became an option recently. :)

Again many thanks!

---

### Post by ubuntu27 on 2006-07-08
> **blissend said:**
> Wow, support here is truely amazing! Many thanks to every that replied.

I have decided to use 32bit ubuntu gnome (love gpled stuff) while storing my music on a separate hard drive. The separate hard drive only became an option recently. :)

Again many thanks!


You're welcome.



PS:  Werlcome to the Community! :KS

---

