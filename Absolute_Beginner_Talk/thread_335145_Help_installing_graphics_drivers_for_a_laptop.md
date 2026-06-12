---
title: "Help installing graphics drivers for a laptop"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Cellwind929 on 2007-01-09
Greetings,

It is with great success that I post here. I am posting on my freshly installed ubuntu 6.10 on my laptop, which now dual boots. My wifi miraculously works thanks to some fooling around and the app wireless assistant. I have also figured out how to install things using the apt-get command. Today has been a good day for linux progress.

Now I come to you with a few questions. Mainly, I would like to know how to install drivers for my laptops ATI mobility radeon x1600. Looking on the ATI site revealed that there are drivers available. They wanted me to run a file called check.sh to see which package I should use. I was unable to get this file working. I also noticed that the packages were in .rpm format, and after some research, I found that it probably wont work with ubuntu. If anyone has the ability to confirm this it would be greatly appreciated. I would like to figure out how to install drivers for my video card so that the scrolling is smooth and not stuttery like it is currently. Installing drivers would also help with allowing me to run other resolutions also.

Thanks for the help in advance.

PS: I also have .mp3's on my ntfs partition of windows, if anyone can tell me about a good .mp3 player that will work with those files, that would be appreciated.

---

### Post by tonyr1988 on 2007-01-09
-Download the check.sh file somewhere (desktop, home directory, it doesn't matter - just remember it).

-Open a Terminal and go to where you installed it (cd *directory*) and try ./check.sh (you may also be able to navigate to it in Nautilus and double-click, choosing "Run in Terminal" if you prefer). Go through whatever it says - I have no clue what it does. :)

-Download the right .rpm file. RPM files are for the Red Hat Distro (RPM = Red Hat Package Manager)

-sudo apt-get install alien

-Open a terminal, navigate to where you downloaded the .rpm's, and:

> alien name_of_package.rpm

It will make a .deb of the package in the same folder. You can then open the .deb like usual (double-click)

You could also run:

> alien -i name_of_package.rpm

instead. It will convert the .rpm to a .deb, install it, and remove the .deb. Uber-convenient. :)

PS-Reply: You need the right codecs to play mp3 songs (search the howto's or look at the wiki - it's not hard) and most (all?) media players will work. I personally prefer amaroK, even in Gnome.

---

### Post by Cellwind929 on 2007-01-09
Thanks, I'll give this a try now!

---

### Post by mlissner on 2007-01-09
Yes, Amarok is amazing. You'll be wowed. I believe if you sudo apt-get install amarok, you'll get amarok along with the codecs to play mp3's.

Good luck. AMAROK.

---

### Post by Cellwind929 on 2007-01-09
Amarok is installing now, thanks.
:D

I installed alien and tried to convert the .rpm to .deb. The problem is I got warnings in the terminal and a .deb package was not actually generated.

Code below:
```
cellwind929@cellwind929-laptop:~$ sudo alien /tmp/ati/fglrx_4_3_0-8.32.5-1.i386.rpm
Warning: Skipping conversion of scripts in package fglrx_4_3_0: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
fglrx-4-3-0_8.32.5-2_i386.deb generated
```

---

### Post by tonyr1988 on 2007-01-09
I've gotten those warning before and still had a successful .deb in the end.

Check your /tmp/ati folder for the .deb

---

### Post by Cellwind929 on 2007-01-09
I triple checked the directory and sadly it is not there.
:(

---

### Post by Cellwind929 on 2007-01-09
While I would love to get a driver for my video card working... Amarok is amazing, it installed wonderfully, it said "hey guess what, I can't play mp3's, wanna install mp3 support buddy?". Once I pointed it to my music, it build a collection. I'm impressed, now back to digging for mobility driver support so I can fix this slow scrolling.

---

### Post by kpkeerthi on 2007-01-09
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

See the section titled "Install from Ubuntu repositories (easier)"

---

### Post by mlissner on 2007-01-09
OK. Here's one method of installation of mp3 support for you. I used Automatix2, but apparently that's not a recommended method anymore so try this instead. 

Go to Applications > Add/Remove. Switch the thing in the upper right corner to "All availible applications", and the filter to mp3. Then get the one called "gstreamer extra plugins" and the one called "Xine extra plugins".

Then, when you have amarok open, try going to Settings > Configure Amarok > Engine. And select Xine. I hear a rumor that it's less buggy then gstreamer. 

Good luck.

---

### Post by Atomic Dog on 2007-01-10
> **mlissner said:**
> OK. Here's one method of installation of mp3 support for you. I used Automatix2, but apparently that's not a recommended method anymore so try this instead. 


Says who?  Use Automatix2 if you want to get it installs easily.  I use it and so far nothing has blown up.

---

### Post by mlissner on 2007-01-10
Yeah, I used it too, but afterwards, I read this really long, ugly thread about how it does harmful things or something. Sadly though, I'm not finding the thread now....sorry. I guess look around a bit more? 

Somebody know what I'm talking about?

---

### Post by riven0 on 2007-01-10
> **mlissner said:**
> Yeah, I used it too, but afterwards, I read this really long, ugly thread about how it does harmful things or something. Sadly though, I'm not finding the thread now....sorry. I guess look around a bit more? 

Somebody know what I'm talking about?

I know what you're talking about. There's been a lot of FUD about automatix lately... read [this thread]("http://www.ubuntuforums.org/showthread.php?t=332926&highlight=automatix").

---

### Post by mlissner on 2007-01-10
No...I was reading a much uglier and specific version than that, though perhaps I've been made a culprit in spreading the FUD. Sigh...

---

### Post by Cellwind929 on 2007-01-10
kpkeerthi is officially my hero. The guide he posted was amazing and it installed the correct drivers just by constantly using apt-get. I now have it set up perfectly, running full resolution and no scrolling lag. Thanks for the help.

---

### Post by kpkeerthi on 2007-01-10
> **Cellwind929 said:**
> kpkeerthi is officially my hero. The guide he posted was amazing and it installed the correct drivers just by constantly using apt-get. I now have it set up perfectly, running full resolution and no scrolling lag. Thanks for the help.

You are welcome. :)

---

