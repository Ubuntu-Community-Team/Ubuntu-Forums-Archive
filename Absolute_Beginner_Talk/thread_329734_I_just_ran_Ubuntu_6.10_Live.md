---
title: "I just ran Ubuntu 6.10 Live"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-02
I can't belive my own eyes. The internet conection is working, without even installing any drivers. Sound too. How is this possible ?
I only need to set up graphics drivers...

It's my first time and i really like it !!!
Unbelivable!

---

### Post by michaeljustman on 2007-01-02
Great! You're a lucky one... laptops are hell, desktops less so, but it seems that there is always something in linux that you'll have to fiddle with to get it to work, but that's half the fun. :-D

---

### Post by shanepardue on 2007-01-02
I disagree. Out of the three computers I use (2 desktops and one laptop), I haven't had a problem with any hardware and my setup is more stable than any other operating system's setup.

---

### Post by spockrock on 2007-01-02
thats the joy of linux, that stuff tends to work out of the box.  I am lucky on this laptop everything detects like a charm as well.

---

### Post by Sef on 2007-01-02
> hats the joy of linux, that stuff tends to work out of the box. I am lucky on this laptop everything detects like a charm as well.

Mine too.  Although I have a tweak to do to get my sound running on my desktop.

---

### Post by petersjm on 2007-01-02
Tried Edgy Live yesterday, too. Worked like a charm. Haven't installed yet, though. Need to pluck up the courage to upgrade from Dapper to Edgy. Wonder if I can simply "upgrade" (and keep settings), rather than install Edgy over the top of Dapper...

---

### Post by shanepardue on 2007-01-02
yep. just change all the instances of "dapper" in your /etc/apt/sources.list to "edgy" then "apt-get update" and "apt-get dist-upgrade"

---

### Post by Sef on 2007-01-02
> Tried Edgy Live yesterday, too. Worked like a charm. Haven't installed yet, though. Need to pluck up the courage to upgrade from Dapper to Edgy. Wonder if I can simply "upgrade" (and keep settings), rather than install Edgy over the top of Dapper...

If you do, then **back up** your files first.   There are problems at times with it, so also have a install disk handy, just in case.

---

### Post by petersjm on 2007-01-02
Thanks Shane and Sef. I'll back up important files to a spare HDD and give it a whirl. Probably not until the weekend, now though. Happy New Year!

---

### Post by michaeljustman on 2007-01-02
I guess my opinion is a bit biased and I've only installed Ubuntu on one machine... with a broadcom wireless card and an ATI graphics card, a logitech mouse as well. Everything else worked out of the box though. (It all works great now). Also I find that I reboot my Ubuntu as much or more than Windows because my sound stops working, the wireless is acting up, programs wont start, etc.

Did I mention that I'm never going to buy a computer with ATI graphics again?

---

### Post by spockrock on 2007-01-02
yeah  both of my logitech keyboard and mice work out of the box, but not with full functionality.  I just configured my mouse to be 100%, however my keyboard, does not have full functionality.  Considering the mx5000 drivers in windows is aweful, and dont work properly 100% of the time, I can live with my sliders not working......100%

---

### Post by shanepardue on 2007-01-02
Ha yeah. ATI can really annoy on linux and I see where you are coming from. Hopefully AMD will open up some drivers like the rumors have said.

---

### Post by spockrock on 2007-01-02
yeah ati drivers pretty much suck, lets hope amd changes that.......

---

### Post by michaeljustman on 2007-01-02
If AMD opens the ATI drivers I will be a very happy camper. I'm just glad that fglrx 8.32.5-1 supports Sideport only for my ATI Radeon Xpress 200M... I hated giving up 128MB of my main memory for 3D acceleration.

---

### Post by Sef on 2007-01-02
Happy New Year to you too Peter.

---

### Post by Lord Illidan on 2007-01-02
> **shanepardue said:**
> I disagree. Out of the three computers I use (2 desktops and one laptop), I haven't had a problem with any hardware and my setup is more stable than any other operating system's setup.

That could be you are lucky with your hardware.

On my late grandfather's laptop, wifi didn't work. Broadcom wireless card. And the S3 graphics card was a bit flaky too. Though the sound worked ok.

And on my system, snd_hda_intel gave me a heck of a lot of problems, though I found the solution here. (Where else? :mrgreen:)

But, yeah, hardware support is awesome.

---

### Post by CroEragon on 2007-01-02
> **Sasa_Ivanovic said:**
> I can't belive my own eyes. The internet conection is working, without even installing any drivers. Sound too. How is this possible ?
I only need to set up graphics drivers...

It's my first time and i really like it !!!
Unbelivable!
In my experience, Ubuntu is hardest distro to set up after installation. On my computer things just doesnt't want to work out of box . My resolution was messed up, freezing of os, hardware acceleration, mounting windows partition, no support for writing on ntfs (thats all linux problem not just Ubuntu), no any kind of multimedia drivers and even worst because as far as i know australia is signing some contract about free trading or some **** that makes using mp3 drivers on ubuntu illegal, same as in USA and pretty stupid GNOME desktop.
Anyway i solved most of it (except freezing and hardware acceleration) and my Kubuntu is working very well, it is fast, and stable and never crash or causes me to lose data (except freezing, but it is not crash , computer just get frozen on 4-5 minutes and unfreeze itself.)
It was pretty hard, but i managed it.
Jer, sto te neslomi, to te ojaca.

---

### Post by Sasa_Ivanovic on 2007-01-02
well i gues i'm lucky compared to you...

---

### Post by Sasa_Ivanovic on 2007-01-02
> **CroEragon said:**
> 
Jer, sto te neslomi, to te ojaca.
Odakle si ?

---

### Post by CroEragon on 2007-01-02
> **Sasa_Ivanovic said:**
> Odakle si ?Iz Hrvatske, Slavonije ali mislim da modovi nebi bas htjeli da pricamo na stranom jeziku i jos da je off. Odakle si ti?

---

### Post by Sasa_Ivanovic on 2007-01-02
Nova Gradiska, preko puta vase Stare Gradiske. U Republici. Ali nije vazno, sada sutim.

---

### Post by Lord Illidan on 2007-01-02
> **CroEragon said:**
> In my experience, Ubuntu is hardest distro to set up after installation. On my computer things just doesnt't want to work out of box . My resolution was messed up, freezing of os, hardware acceleration, mounting windows partition, no support for writing on ntfs (thats all linux problem not just Ubuntu), no any kind of multimedia drivers and even worst because as far as i know australia is signing some contract about free trading or some **** that makes using mp3 drivers on ubuntu illegal, same as in USA and pretty stupid GNOME desktop.
Anyway i solved most of it (except freezing and hardware acceleration) and my Kubuntu is working very well, it is fast, and stable and never crash or causes me to lose data (except freezing, but it is not crash , computer just get frozen on 4-5 minutes and unfreeze itself.)
It was pretty hard, but i managed it.
Jer, sto te neslomi, to te ojaca.

Did you try any other distro?

---

### Post by noneofthem on 2007-01-02
I am testing new systems all the time. My experience with Ubuntu (and most  other GNU/Linux distributions) was that there are no major hardware problems when installing a fresh system at all. The only two things I always had to set up manually afterwards on Ubuntu were my ATI 3D acceleration and my wireless LAN. Everything else runs out of the box.

I was pretty surprised when MS Windows Vista wouldn´t recognize either my soundcard or my network card. Pretty amazing when you think about how long they have been working on this crap.

---

### Post by CroEragon on 2007-01-02
> **Lord Illidan said:**
> Did you try any other distro?
Yes, OpenSUSE, Mandriva and SimplyMepis. But just tried it, first Linux i ever used was Knopix (i know it's live, but cant they make so god out of box like Knoppix) and after that Ubuntu Drapper. I was terrified when i booted Ubuntu LiveCD. Knoppix worked so good without slightest glitch and when i booted Ubuntu, icons were HUGE (resolution).
I didnt give rest of distros lot of time as Ubuntu, it totally stunned me when i tweaked itan im using i now.

---

