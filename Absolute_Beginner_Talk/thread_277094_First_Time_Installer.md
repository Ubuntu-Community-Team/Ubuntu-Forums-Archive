---
title: "First Time Installer"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2006-10-14
So, I'm not new to Linux as I've been studying it over the years and had a few failed attempts to load it on some old machines. Ive been giving it some thought and am ready to give it another go with Ubuntu, but I do have a few questions. I currently do have an AMD 64 chip in my system, should I select the Intelx86 version or the 64-Bit pc? Currently I run Windows XP and only have the 32 bit edition, I see theres too many negatives to switch over to the 64 bit edition. Another question is if i should do anything special to prep my machine? I'm running an AMD x700 card so dispaly wise would I have any troubles? I plan on running a dual boot windows xp/ubuntu until I get it down and decide if I want all linux or all xp. Any help, tips, or advice would be greatly appreciated! Thanks!! :)

---

### Post by adwait on 2006-10-14
AMD = x64 version. The intel version is for the Itanium series of Intel processors which have a completely different architecture.

---

### Post by fern on 2006-10-14
Tumpster

Have a working machine running Windows XP? Is that your PC that you use daily for serious or semi-serious work?  Stick with Windows and leave it alone.

If you have another machine for which you don't have a licence to run Windows, THEN install Ubuntu on it, and you'll love it.

Ubuntu almost works "out of the box", browser, mail, Open Office and all.  But, as a user myself, I'd say I would NEVER risk my normal Windows machine and start creating partitions, dual boot confusion, etc.  Linux is not better than Windows by a long stretch, and it is really not going to buy you anything.

If what you want is to play with Linux, get a second,used machine, even a very modest one, because Ubuntu makes those sing!  I am running Ubuntu on an old laptop which, with Windows 98, was ssslllooowww, but it zips right along with Ubuntu!  I am so happy with it that I spend way too many hours trying to make it do things that Ubuntu doesn't do very easily, such as join your home network - there is challenge for you.  Or allow you to log in as the "root" user (got that just a few minutes ago).

As for which one to download, I'd try the 64 bit first, but you can download both and see which one installs.  They are free and burning a second CD is not that bad.

Fern

---

### Post by meng on 2006-10-14
> **fern said:**
> Tumpster

Have a working machine running Windows XP? Is that your PC that you use daily for serious or semi-serious work?  Stick with Windows and leave it alone.

If you have another machine for which you don't have a licence to run Windows, THEN install Ubuntu on it, and you'll love it.

Ubuntu almost works "out of the box", browser, mail, Open Office and all.  But, as a user myself, I'd say I would NEVER risk my normal Windows machine and start creating partitions, dual boot confusion, etc.  Linux is not better than Windows by a long stretch, and it is really not going to buy you anything.

If what you want is to play with Linux, get a second,used machine, even a very modest one, because Ubuntu makes those sing!  I am running Ubuntu on an old laptop which, with Windows 98, was ssslllooowww, but it zips right along with Ubuntu!  I am so happy with it that I spend way too many hours trying to make it do things that Ubuntu doesn't do very easily, such as join your home network - there is challenge for you.  Or allow you to log in as the "root" user (got that just a few minutes ago).

As for which one to download, I'd try the 64 bit first, but you can download both and see which one installs.  They are free and burning a second CD is not that bad.

Fern
Everyone's comparative experience of Ubuntu vs. Windows is different, for example I had huge problems setting up a Windows home network, and found an Ubuntu home network very straightforward by comparison. More generally, whether you find Windows better, or Ubuntu better, or both about the same, depends very much on your personal priorities, i.e. what you use your computer for! Sweeping statements suggesting that one is better than the other overlook the diversity of priorities that individual users have.

---

### Post by Tumpster on 2006-10-15
So I tried to run a live cd. I had no luck with that. I got the message "Failed To Start The X Server" and as I read through the log it came back with "ATI: PCI MACH64 In Slot 5:0:0 Could Not Be Detected," and also "ATI: PCI MACH64 In Slot 5:0:1 Could Not Be Detected." And so it shuts down ever time I try, anyone willing to help me trouble shoot this problem? Thanks!

---

### Post by pay on 2006-10-15
I have always had issues with the ATI drivers and ubuntu. You can try to load the liveCD in safe graphics mode and see if that works. Or you can download the alternative install iso that install in a text based environment and then you can install the ati (fglrx or radeon) drivers. There are thousands of guides on how to do that on the net.

---

### Post by Tumpster on 2006-10-18
> **pay said:**
> I have always had issues with the ATI drivers and ubuntu. You can try to load the liveCD in safe graphics mode and see if that works. Or you can download the alternative install iso that install in a text based environment and then you can install the ati (fglrx or radeon) drivers. There are thousands of guides on how to do that on the net.


Yes unfortunatly the safe graphics didn't work, it kicked my monitor off as it seemed to get no signal but I did hear the startup music and all that. Know of any decent guides that could help me install the proper drivers?? Thanks!!

---

### Post by ReaderRat on 2006-10-18
ATI - How to install the drivers
          [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by Tumpster on 2006-10-21
See problem is though, I can't connect up at all as I run wirelessly in my home and i can't even get into to start running ubuntu at all...nothing, no luck. Anyone have any way through the text interface to get my video card to work? I wait for it to count down the 30 seconds to run as a live cd and it loads everything up but then I get the X server failing message and thats as far as I go.  If it helps I'm using a live cd right now, what I would like to do is setup ubuntu on a seperate partition with windows running on the other so I can try linux and fully get into it and get used to it, but when I cant see anything that makes it a bit hard! :)

---

### Post by ReaderRat on 2006-10-21
As with anything important, Back Up Your Essential Files before you start messin with the partitions. 
[**Install Alternate CD**](http://users.bigpond.net.au/hermanzone/) (with pictures).

---

### Post by Tumpster on 2006-10-21
So yeah, I've loaded up ubuntu using the alternate iso but with the ATI drivers the xserver fails, when I used VGA drivers it fails, I change to VESA drivers and it dosent' fail but I don't get a signal, when loggin in before I get the login desktop screen it turns my monitor off like my monitor is getting no signal. Any way to fix it? It's like I set my monitor to a display it can't do, but I have monkied with this and it still does it, any ideas? Thanks!

---

### Post by arsenic23 on 2006-10-21
I had a problem like this about a year ago.  It turned out that the VESA driver was outputing at a refresh my monitor wouldn't display by default.  

I have no idea how to fix it though.

---

### Post by Tumpster on 2006-10-21
Anyone have any alternatives or ways to fix this???

---

### Post by Tumpster on 2006-10-21
Or maybe a way to get it to work????????????

---

### Post by raqball on 2006-10-21
> **fern said:**
> Tumpster

Linux is not better than Windows by a long stretch, and it is really not going to buy you anything.

Are you serious??? LOLOLOLOLOLOLOLOLOLOLOLOLOL

---

### Post by Tumpster on 2006-10-21
That dosen't actually help me, I'm looking to fix this...it's very frustrating, makes me wanna just whipe away the partition!!](*,)

---

