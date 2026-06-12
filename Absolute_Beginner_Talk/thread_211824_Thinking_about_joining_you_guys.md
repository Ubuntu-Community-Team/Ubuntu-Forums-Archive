---
title: "Thinking about joining you guys"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Maheriano on 2006-07-08
Hey, I've been a Gentoo guy for about a year and it's been great but basically I'm looking for something a little more plug and play. I had a wrestle with my xorg.conf for 2 weeks before I got dual head working and now I just can't even think about doing the S-video. So I was thinking about giving Ubuntu a try, what do you think? I read the thread about deciding if it's for me and it sounds alright. If I can do Gentoo, I can do this. So as per stereotypical newbie protocol, I'll ask my first stupid question. How do I get it installed over Gentoo? :razz: 

(no, seriously...:-s )

---

### Post by BarfBag on 2006-07-08
... rotf ...

Not to be mean or anything, but you just made me snicker.  You managed to install Gentoo, but don't know how to edit your partition table?

Somebody else should explain this a little more clear, but it's very simple.  Are there any other operating systems installed on your PC?  If there's not, you could just format the entire drive (option in Ubuntu setup) and it would write Ubuntu over everything.  If there's another OS, just select "Manually Edit Partiton Table" and tell it to install to your Gentoo partitions.

---

### Post by Nano Geek on 2006-07-08
To install it you can download the .iso file from [Ubuntu.com]("http://www.ubuntu.com") and, if you are using Gnome, just right-click and press **Write to Disk**. Then reboot your computer and start it up!

---

### Post by Maheriano on 2006-07-08
So download .iso, burn as disc image, insert disc, restart? That it?
Will I lose any of the data on my drives?

---

### Post by Nano Geek on 2006-07-08
The Desktop CD you download is a live/install CD. It won't touch your hard drive unless you tell it to install.

---

### Post by Maheriano on 2006-07-08
Ya but I'm going to be installing it. I've installed Gentoo so many times, I can do it now in just a few hours. So I'll give Ubuntu a try for a while. So should I back up to my reserve drive, or just leave it and install from the CD?

---

### Post by Nano Geek on 2006-07-08
> **Maheriano said:**
> Ya but I'm going to be installing it. I've installed Gentoo so many times, I can do it now in just a few hours. So I'll give Ubuntu a try for a while. So should I back up to my reserve drive, or just leave it and install from the CD?Do you want to delete Gentoo?

---

### Post by blitzd on 2006-07-08
> **Maheriano said:**
> Ya but I'm going to be installing it. I've installed Gentoo so many times, I can do it now in just a few hours. So I'll give Ubuntu a try for a while. So should I back up to my reserve drive, or just leave it and install from the CD?

I always back up anything of importance before I install a new OS, even if on a secondary partition or drive. Better safe than sorry.

I've used Gentoo a fair bit as well, you'll find Ubuntu to be a breeze ;)

---

### Post by Nano Geek on 2006-07-08
By the way, forget about this installation taking hours, I was able to install Ubuntu in less than 30 minutes.

---

### Post by blitzd on 2006-07-09
> **asjdfwejqrfjcvm msz34rq33 said:**
> By the way, forget about this installation taking hours, I was able to install Ubuntu in less than 30 minutes.

Indeed, my initial install took less than 5 mins. Probably 15 counting updates, initial boot, and reboots...

---

### Post by woedend on 2006-07-09
even if you don't decide on ubuntu, stay to hang out and help where you can.

---

### Post by Maheriano on 2006-07-09
Ya, as a former Gentoo guy, ask me any questions you want. Not sure where I can help out, but I'll do what I can.

Yes, I want to get rid of Gentoo for now. I have the live CD to always install it later. So do I just burn that disc image and restart my computer with it in? Or run it while in KDE?

---

### Post by woedend on 2006-07-09
restart with it in the tray, assuming your computer boots from CD Rom.  It will get you into ubuntu to try out.  IT WILL BE SLOW!!!  ubuntu is much faster when installed naturally.  IF you decide you like it, and want to install it, there is a huge install icon on the desktop.  it should hold your hand from there.  Its no gentoo, its simple :p.

---

### Post by Nano Geek on 2006-07-09
Could you tell us how it wnet?

---

### Post by Maheriano on 2006-07-10
I haven't done it yet, I've got a bit of a chain on my hands....

1. I have to back up my hard drive on my secondary hard drive before I can do it.
2. My automounting is botched so I can't access my secondary drive right now. Something with the X11-DRM modules, the package is fubed.

So I may just install Ubuntu on my secondary drive, then copy everything between drives, and install Ubuntu again on my main drive.

---

### Post by Maheriano on 2006-07-10
Okay, since I swapped motheroards, my automounting mysteriously works again. I guess I should be able to go ahead with it tonight. Am I going to have to configure much after installing it?

---

### Post by DJ Scribblinni on 2006-07-10
The only thing you'll be configuring is hardware that may not work initially, and your desktop eye candy that some people seems to like.  Otherwise you set to go.

---

### Post by user1397 on 2006-07-10
be sure to try out the live cd for all your hardware, so that you dont have any compatability issues

---

### Post by Maheriano on 2006-07-10
This is retarded, my new motherboard doesn't give me the option to get into the BIOS. I can't make it boot from the CD! I guess the only thing I can do is unhook the hard drive.

---

### Post by cyberlite on 2006-07-10
What kind of mobo do you have??? make and model???

---

### Post by Maheriano on 2006-07-10
Okay so I read the manual that came with the board, it was F2, not DEL. I got the .iso burned, restarted the computer, and it brought me to the menu on the CD. When I tried to install it, it kept complaining the xxxxxx.DEB file was corrupt. That was the alternate file.

So I downloaded the desktop file (both i386), burned that, restarted, and it brought me to the same menu but it only had 1 install option this time. But any option I chose this time, it kept saying there was error 10 and it couldn't read from the CD. So I burned the image again, different CD, same thing. What's wrong with these files?

---

### Post by brentoboy on 2006-07-10
get the alternate CD instead of the livecd

it installs in text mode, but it is still menu based (not command line)

it is more mature than the new live cd installer, so if there is a bug in the live installer, it is an excelent fall back.

It also has better partition handling than the live installer (or so I am told.  I have never even used the live installer.

---

### Post by Maheriano on 2006-07-10
I was downloading both and the alternate was taking 7 hours where the regular was taking 30 minutes. So just wait I guess?

---

### Post by steve.horsley on 2006-07-10
I think it's worth the wait.

Standard advice here is to 1: chack the md5 sum ot the ISO after downloading and 2: burn at as slow a rate as you can - it takes a long time but gives more reliable results.

If you plan to blow away Gentoo, the best thing is to delete all the gentoo partitions and then tell the Ubuntu installer to use the free disk space - let it do its own partition sizing etc.

---

### Post by blitzd on 2006-07-10
> **Maheriano said:**
> Okay so I read the manual that came with the board, it was F2, not DEL. I got the .iso burned, restarted the computer, and it brought me to the menu on the CD. When I tried to install it, it kept complaining the xxxxxx.DEB file was corrupt. That was the alternate file.

So I downloaded the desktop file (both i386), burned that, restarted, and it brought me to the same menu but it only had 1 install option this time. But any option I chose this time, it kept saying there was error 10 and it couldn't read from the CD. So I burned the image again, different CD, same thing. What's wrong with these files?

Sounds like it may be your CD drive more than the files. If you have any compressed air or a lens cleaner for your optical drive maybe try blowing it out or giving the cleaner a run through. There should be MD5 sums which you can use to verify the checksum of any images you download as well. I don't know the specific command line args to do that, but I'm sure someone here can point you in the right direction (anybody?)

There is also an option on the live cd to run a check on the disc, but if it is your drive you will most likely have bad results with that even if the disc is ok. If you have another computer you could try the check on that maybe.

Anyways, I have a very finnicky optical drive in an older machine - it would often give me those types of errors on discs that worked fine on other machines.

---

### Post by Nano Geek on 2006-07-11
> **blitzd said:**
> Sounds like it may be your CD drive more than the files. If you have any compressed air or a lens cleaner for your optical drive maybe try blowing it out or giving the cleaner a run through. There should be MD5 sums which you can use to verify the checksum of any images you download as well. I don't know the specific command line args to do that, but I'm sure someone here can point you in the right direction (anybody?)To find the checksum type **md5sum *filepath***.

---

### Post by Maheriano on 2006-07-11
This is weird. Here are the results I got.

alternate/i386/iso file = the xxxxxx.deb file was corrupt after 2 separate downloads and 2 separate CD.

desktop/i386/iso = it wouldn't even read the disc and I tried this one 3 times.

I'll try burning it slower, but that's all I have left.

---

### Post by Maheriano on 2006-07-12
I'm starting to think the burn speed is not related to this problem. If the file is corrupted, then burning it slower is not going to fix that. I'm downloading the Canada iso images, can anyone confirm a specific series of ilnks on this website to get to a working file I can download? I have a regular cheapo motherboard and processor, x86.

---

### Post by SigmaX on 2006-07-12
It has to let you boot from the CD somehow -- the BIOS setup key isn't always delete thought.  What brand is it?

SigmaX

---

### Post by Maheriano on 2006-07-12
I have it booting from the CD, that's old. I make it all the way to the CD menu and then have the above problems.

---

### Post by Maheriano on 2006-07-13
Got it. I picked up a 6.06 boot CD off someone else.

---

### Post by Maheriano on 2006-07-13
It works fine but when it boots up, it can't finish checking the filesystems. It wants me to repair them manually. Man, I thought Gentoo was a pain!

---

### Post by Nano Geek on 2006-07-15
It must be something with your cd drive, I have never had a problem like that and if that is your second disk to try the cd is probably not the problem.

---

### Post by Maheriano on 2006-07-15
No, I have everything installed, I'm using Ubuntu. But if I reboot, it can't finish checking the file systems and gives me the command prompt to fix it. If I hit CTRL+D, it skips it and loads into Ubuntu desktop environment.

---

### Post by Maheriano on 2006-07-15
A reinstall fixed it. Working now.

---

### Post by Nano Geek on 2006-07-16
I'm glad you were finally able to install Ubuntu!

---

### Post by Maheriano on 2006-07-16
Ha, still wrestling with the simplicity! I tried to su to root....finally got that working. I tried to emerge a program....ya, that didn't work! This is cool though, much easier. Still trying to get a peer to peer program going and a better resolution out of my video card.

---

