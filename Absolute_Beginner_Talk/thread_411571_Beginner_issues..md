---
title: "Beginner issues."
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by bobtherocket on 2007-04-17
Hi! Windows XP crashed on me last night, quickly burned a Ubuntu CD from safe mode, and now I'm hooked. Goodbye, Windows. We knew you more than we cared to...

Anyway, running on a Toshiba Satellite a105-s4134. (Randomly typed my model number + linux into Google, and found a review saying Ubuntu and the laptop worked well together.) Few issues, though, since I'm almost a complete noob.

Trying to get the touchpad working, so I could at least use the scrolling features. I had the synaptics driver, and I browsed the forums looking for a fix, and so I editted xorg.conf, and...Blew it up. So, yeah...Any other possible fix?

Getting used to running apt-get and such to grab needed programs, but if I can't find them, I have to resort to using tar.gz. Is it really just alright to slap them on my desktop, use ./configure from the terminal, then delete the remnants from the 'top? Any style of installing/etc I should be following to keep things neat?

Ummm...Move around a lot, so I rely on MSN/AIM/YIM to contact buddies, with webcam/mic. Is there a program like GAIM that has at least those three, and lets me send/receive webcam/mic invites with Windows users?

Ah, final issue. I tried installing gtk-gnutella, and it seems to install properly, but when I go through Apps>Internet>gtk-gnutella, nothing happens. Same with LimeWire. FrostWire will load the splash screen and open the application, but it vanishes a few seconds later.

Sorry for all the questions, and there's bound to be more, so please bear with me!

Thanks ahead of time!

---

### Post by punong_bisyonaryo on 2007-04-17
> **bobtherocket said:**
> Hi! Windows XP crashed on me last night, quickly burned a Ubuntu CD from safe mode, and now I'm hooked. Goodbye, Windows. We knew you more than we cared to...

Amen to that!

> **bobtherocket said:**
> Trying to get the touchpad working, so I could at least use the scrolling features. I had the synaptics driver, and I browsed the forums looking for a fix, and so I editted xorg.conf, and...Blew it up. So, yeah...Any other possible fix?

Did you back up your xorg.conf file before it blew up? I'm guessing you didn't.

> **bobtherocket said:**
> Getting used to running apt-get and such to grab needed programs, but if I can't find them, I have to resort to using tar.gz. Is it really just alright to slap them on my desktop, use ./configure from the terminal, then delete the remnants from the 'top? Any style of installing/etc I should be following to keep things neat?

I don't think it matters. After you install them it puts them into their appropriate folders anyway so wherever you extract your tarball should be fine. Just like Windows program installers that you need to extract to a temporary folder.

> **bobtherocket said:**
> Ah, final issue. I tried installing gtk-gnutella, and it seems to install properly, but when I go through Apps>Internet>gtk-gnutella, nothing happens. Same with LimeWire. FrostWire will load the splash screen and open the application, but it vanishes a few seconds later.

I had that issue, too. I tried running the said program in terminal, and there's how I found out that I had a problem with my Java. Try running those in terminal see what you come up with.

Sorry, I'm no expert. The others might give you more useful answers, though.

---

### Post by punong_bisyonaryo on 2007-04-17
Try to check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org), too. Lots of quick installation instructions, including J2SE for your frostwire/limewire/gnutella.

---

### Post by bobtherocket on 2007-04-17
Hmmm...gt-gnutella says it is running an ancient version, so I removed it, now about to install the newer version, but apparently there's the libgnutls11 dependency...Can't seem to find it to download, though.

---

### Post by bwhite82 on 2007-04-17
The wiki is a newbie's best friend (I'm still one, even though I've been using Linux on and off since the mid-nineties.). Check out both the Official and Community documentation:
[URL="http://wiki.ubuntu.com"]
Ubuntu Wiki[/URL]

---

### Post by punong_bisyonaryo on 2007-04-17
> **bobtherocket said:**
> Hmmm...gt-gnutella says it is running an ancient version, so I removed it, now about to install the newer version, but apparently there's the libgnutls11 dependency...Can't seem to find it to download, though.

Hmm, so the ancient version was the one in from the repositories, and right now you installed the latest from their site. Is this correct?

BTW, you can quickly install packages by typing
```
sudo aptitude install libgnutls11
```
for example.

---

### Post by bobtherocket on 2007-04-17
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "libgnutls11"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

---

### Post by aberry5555 on 2007-04-17
If your xorg.conf was damaged when you manually edited it open a terminal and type

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

Now restart Ubuntu

This should reset your settings file to when you originally installed  Ubuntu

---

### Post by jvc26 on 2007-04-17
> **bobtherocket said:**
> Hi! Windows XP crashed on me last night, quickly burned a Ubuntu CD from safe mode, and now I'm hooked. Goodbye, Windows. We knew you more than we cared to...

Excellent news :)
> **bobtherocket said:**
> 
Ummm...Move around a lot, so I rely on MSN/AIM/YIM to contact buddies, with webcam/mic. Is there a program like GAIM that has at least those three, and lets me send/receive webcam/mic invites with Windows users?

Gaim is on Ubuntu - Applications -> Internet -> GAIM
Note: Newer versions of apps will be in the repositories for Feisty, which is the new Ubuntu version coming out in 2 days.
Il

---

### Post by bobtherocket on 2007-04-18
Ok, so gAIM/aMSN don't do what I want, which is both webcam and voice capabilities with Windows users. Is there a program that will? Or can I run Windows Live through wine?

---

