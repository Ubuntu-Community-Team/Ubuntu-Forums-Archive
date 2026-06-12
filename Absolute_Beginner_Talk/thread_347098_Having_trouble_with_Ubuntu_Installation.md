---
title: "Having trouble with Ubuntu Installation"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by jammer84 on 2007-01-26
Hi,

I'm new here so hi. 

A mate of mine told me about ubuntu a couple of day's ago. I just got around to downloading it there a few minutes ago. Burned the iso to a cd and got ready to load onto my pc. i shrunk the partition of my windows in order to leave 100gb for the ubuntu installation and to play around with it. I'm not familiar with linux platforms but am anxious to learn. 

My problem lies after I choose to install Ubuntu. It extracts, loads kernal, throws up a screen saying Ubuntu and then it just hangs.

If anyone can help me get by this I would be very gratefull.

Thank You

---

### Post by taurus on 2007-01-26
Did you check the integrity of the ISO file before you burnt it?  Then, how fast did you burn it?  Make sure you burn it at a slow speed like 4x.  And before you hit the install/run from the CD, pick the scan CD option to make a quick scan of the CD to make sure everything is good before you install it.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Terry of Astoria on 2007-01-26
Have you taken the option on booting the cd of testing the cd? There is that option at first boot. You may have a bad burn or download.

---

### Post by jammer84 on 2007-01-26
I will burn another copy and reboot to test to see if it passes the test. I will let ye know in a while..

---

### Post by jammer84 on 2007-01-26
No joy, it sticks at this screen 

[[IMG]http://img262.imageshack.us/img262/3584/26012007043yt2.jpg[/IMG]](http://imageshack.us)

while checking the cd also.

Any ideas?

---

### Post by taurus on 2007-01-26
Do you have another computer that you can test out that CD to see if it boots at all?  Otherwise, I highly recommend you download and use the alternate CD to install Edgy on your machine instead.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

p.s.  What's the spec of your machine anyway?

---

### Post by jammer84 on 2007-01-26
am trying using the Cd burner xp and writing the disk at 2x to see if it helps cuz with nero it was being burned at 8x.

I have a FSC Scaleo H,
250 + 500GB HDD,
1.5 GB RAM,
Athlon 64 x2 3800+
nvidia radeon 1600 Graphics Card,
Wireless built in,
ASUS A8NE-FM M/B

---

### Post by taurus on 2007-01-26
> **jammer84 said:**
> am trying using the Cd burner xp and writing the disk at 2x to see if it helps cuz with nero it was being burned at 8x.

I have a FSC Scaleo H,
250 + 500GB HDD,
1.5 GB RAM,
Athlon 64 x2 3800+
**_nvidia radeon 1600 Graphics Card_**,
Wireless built in,
ASUS A8NE-FM M/B

Am I missing something?  I thought radeon is ATI and nvidia is nVidia!

---

### Post by OldTimeTech on 2007-01-26
Your right Taurus.....Radeon is ATI

I even "googled" it to make sure....LOL!!

---

### Post by jammer84 on 2007-01-26
Sorry it's an ati radeon 1600 graphics card, it's a nvidia nforce chipset on the motherboard

---

### Post by jammer84 on 2007-01-26
still no joy after burning at 2x and testing iso before burning... I dunno

---

### Post by taurus on 2007-01-26
See if you can boot the same CD with another computer.  Are you burning the x86 or x86_64 version?  From the screenshot, looks to me like  Kubuntu (KDE)...

Have you tried the alternate CD or even the x86 version if you haven't already done so?

---

### Post by jammer84 on 2007-01-26
This is the one i've been trying

[http://ftp.esat.net/mirrors/releases.ubuntu.com/releases/edgy/](http://ftp.esat.net/mirrors/releases.ubuntu.com/releases/edgy/)

then,
64-bit PC (AMD64) desktop CD

---

### Post by Keltazz on 2007-01-26
Hi - i put ubuntu on a couple months ago and resized the wrong way and wiped out windows. seems like it would be a simple thing to have a pointer that says this will be your ubuntu, this your windows. i had to reinstall windows. then i got it on and was having a real good time with gimp - the  image program, much better than windows paint. i found a free download photo program thats better than windows, but not as good as gimp. anyway, then windows would not see the dvd drive as a write dvd so i had to reinstall again. then when i tried to put ubuntu on again, i got a disk write error message, and i could not access windows. i think ubuntu was unavailble also. so ive reinstalled windows again and got a new disk i the mail - downloading is just too slow for me, since i go to the library. so now im getting up my courage to use the dev sda parttion window during the ubuntu install - as this disk doesnt have the easy bar graph tool. i am at this forum  trying to find the beginers walk thru. i just want to tell you that these computers will drive you crazy, ubuntu or windows, there are always problems! ps - i predict that there will be some serious problems with vista - buy apple stock if you can! pps- used to be on apple and liked it better than windows - but still ran into weird computer stuff - like, one of my favorites, you have a file on the desktop and you do a search and it says its not there! was this too wordy? Keltazz

---

### Post by jammer84 on 2007-01-26
i know the joys of computers. dying to get a look at this ubuntu but at the moment it just doesn;t want to install on my machine. I used partition magic and free's up 100gb to use for the ubuntu. it's the easiest way to do it. if i get this up and running it will be happy days...

---

### Post by Pobega on 2007-01-26
The 64 bit version *should* work, but I've also heard a lot of bad things about ATI video cards and LiveCDs. I would say to just burn an Alternate Install CD, since those will run on almost any hardware.

---

### Post by gn2 on 2007-01-26
> **jammer84 said:**
> I used partition magic and free's up 100gb to use for the ubuntu. it's the easiest way to do it. 

 Are you trying to install into partitions created by Partition Magic, or just into unallocated space?
 
Partition Magic is notorious for difficulties creating Linux partitions to install to, best to leave unallocated space and install into that, and let the Ubuntu installer create the partitions.

Also, have you tried the F6 boot options?

---

### Post by jvc26 on 2007-01-26
Did you make sure you did an md5 checksum on the disk - you may have no burn errors, but with a faulty md5 then you wont get anywhere anyway.
Il

---

### Post by jammer84 on 2007-01-27
I will try an alternate disk today. i done the checksum and the .md5 passed ok. Ya i've left the 100GB unallocated.

---

### Post by jammer84 on 2007-01-27
with the alternate cd and verifying the md5 and burning at 2x i get stuck here now

[[IMG]http://img237.imageshack.us/img237/750/27012007044br8.jpg[/IMG]](http://imageshack.us)

Any ideas?

---

### Post by jammer84 on 2007-01-27
sry, taught the image shrunk on uploading

---

### Post by jammer84 on 2007-02-01
got it working after adding in the commands --> noapic nolapic

---

