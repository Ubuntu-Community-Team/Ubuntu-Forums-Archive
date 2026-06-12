---
title: "WARNING for Windows 8 Dual-Booters"
date: 2012-04-06
forum: Any Other OS
---

### Post by Mars11 on 2012-04-06
After several weeks of searching for why my files would disappear after booting into Windows 8 I found out why. I have a Media partition that I use to store my music, pictures, videos, movies, documents, downloads, and pretty much anything I want on both OS's.   It was fine when using Windows 7, but Windows 8 has a new way of shutting down. It puts itself into a hybrid hibernation/off state. While this makes boot times extremely fast (less than 10 seconds on a HDD) it deletes all my files because it's restoring it to the pre-hibernation state. (Explained better [here]("http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot").) I'm doing this as a warning to anybody else planning on, or that is currently dual-booting Windows 8 with any other OS. Instead of shutting down, restart. The boot times are longer, but it's better than losing several hours of hard work.

---

### Post by shuttleworthwannabe on 2012-04-07
Another of Windows 8 features to not allow dual boot systems. Wise.

---

### Post by sffvba[e0rt on 2012-04-07
> **shuttleworthwannabe said:**
> Another of Windows 8 features to not allow dual boot systems. Wise.

I doubt that this was the intention.


404

---

### Post by Mars11 on 2012-04-07
> **shuttleworthwannabe said:**
> Another of Windows 8 features to not allow dual boot systems. Wise.
Who, outside of Microsoft, knows? I'm pretty sure they didn't even think about it, that's MS for ya.

---

### Post by leopoldbirkholm on 2012-04-07
Thank you for the warning.

What I have read is that the thought of Windows 8 is that you will not need any other system. And if you do, you know enough to fix a work-a-round yourself.

Just my thought of the "bug"...

Other then that bug, what do you think of Windows 8? 

Myself, I think it will be great for my mother with the Metro. Point, click and voila! you have your favorite program open mommy!

But for me, it is just annoying jumping from Metro and to desktop and back.

---

### Post by Mars11 on 2012-04-07
I'm liking it, though I still find myself in Ubuntu more.

I love the lock screen, I want Ubuntu to get something similar and hopefully that will happen when they move into the tablet/phone space.

I actually like the look of Metro, because I like things to be minimalist. Though I wouldn't use it all the time, it's been almost too simplified, to the point where you can't be very productive.

The hot corners are nice, I prefer them more than buttons for quick tasks.

The ribbon interface is also nice for Explorer, I can access some settings faster than if I right-click.

I don't know why, but it doesn't bother be to switch between Metro and the Desktop, the Metro "Start" is similar to Unity's Dash when set to taking up the entire display.

The hot corners are nice, I prefer them more than buttons for quick tasks.

Anything other than that I either don't like, don't care about, or was in Windows 7. I still have a hard time functioning without Workspaces on Windows. I always flip the screen around. :P

---

### Post by Basher101 on 2012-04-07
thanks for the warning..i planned to get the beta for some tests

---

### Post by F.G. on 2012-04-07
> **not found said:**
> I doubt that this was the intention.


404
if they simply didn't test this part of the functionality that seems far more worrying.

---

### Post by sffvba[e0rt on 2012-04-09
> **F.G. said:**
> if they simply didn't test this part of the functionality that seems far more worrying.

I (again) doubt that MS cares if you can or can't dual boot their OS... they care if you can install and use Windows.


404

---

### Post by flurospar on 2012-04-09
First of all, [Secure boot will prevent running alternate OSes]("http://linux.slashdot.org/story/11/09/21/062231/how-microsoft-can-lock-linux-off-windows-8-pcs"), and BTW, Microsoft's new hibernating shutdown will also make it a better place for viruses. The viruses can be kept in memory for ever, and ever...

To forcefully shutdown, IIRC, one can use:
```
shutdown /s /full t 0
```

---

### Post by haqking on 2012-04-09
> **flurospar said:**
> First of all, [**Secure boot will prevent running alternate OSes**]("http://linux.slashdot.org/story/11/09/21/062231/how-microsoft-can-lock-linux-off-windows-8-pcs"), and BTW, Microsoft's new hibernating shutdown will also make it a better place for viruses. The viruses can be kept in memory for ever, and ever...

To forcefully shutdown, IIRC, one can use:
```
shutdown /s /full t 0
```

That is old news now.

only if OEMS choose to and only effects if you buy a OEM with windows on it.

Also there will more than likely be a option to disable it.

And secure boot was cracked last year with bootkit.

[http://www.zdnet.com/blog/bott/linux-wont-be-locked-out-of-windows-8-pcs-but-fud-continues/4343](http://www.zdnet.com/blog/bott/linux-wont-be-locked-out-of-windows-8-pcs-but-fud-continues/4343)
[http://www.extremetech.com/computing/114173-windows-8-secure-boot-calm-down-microsoft-is-simply-copying-apple](http://www.extremetech.com/computing/114173-windows-8-secure-boot-calm-down-microsoft-is-simply-copying-apple)

---

### Post by sffvba[e0rt on 2012-04-09
> **flurospar said:**
> First of all, [Secure boot will prevent running alternate OSes]("http://linux.slashdot.org/story/11/09/21/062231/how-microsoft-can-lock-linux-off-windows-8-pcs"), and BTW, Microsoft's new hibernating shutdown will also make it a better place for viruses. The viruses can be kept in memory for ever, and ever...

To forcefully shutdown, IIRC, one can use:
```
shutdown /s /full t 0
```

The point that was being made was that this new pseudo shutdown that Windows 8 does is yet another way that it prevents (or at least makes it very hard) to dual boot the system.  Most are aware of the secure boot issue.

If the virus is/was in memory already or gets loaded there directly after restart makes little difference to its effectiveness I would imagine.  Except that it may become unstable over time and stop working which would be a plus ):P



404

---

### Post by Dlambert on 2012-04-09
I dualed windows 8 with no problems. Didn't share partitions though. Also MicroSoft has prevented linux or any other OS from running on their ARM devices.

---

### Post by Basher101 on 2012-04-09
> **flurospar said:**
> First of all, [Secure boot will prevent running alternate OSes]("http://linux.slashdot.org/story/11/09/21/062231/how-microsoft-can-lock-linux-off-windows-8-pcs"), and BTW, Microsoft's new hibernating shutdown will also make it a better place for viruses. The viruses can be kept in memory for ever, and ever...

To forcefully shutdown, IIRC, one can use:
```
shutdown /s /full t 0
```

hm i won't have to ever worry about that since i built 2 pcs already and will continue to make my own. But this can become quite a problem for the less technical expirienced.

---

### Post by kurt18947 on 2012-04-09
> **Basher101 said:**
> hm i won't have to ever worry about that since i built 2 pcs already and will continue to make my own. But this can become quite a problem for the less technical expirienced.

Or notebook-type machines where one does not have a choice of BIOS or motherboard.  I'm certain there'll be desktop motherboard manufacturers who will  have an easy opt-out for secure boot.  Let's hope notebook manufacturers can resist any Microsoft 'recommendations' about locking secure boot on.

---

### Post by linuxmaniack on 2012-04-09
This is why windows 8 will fail, RIP ubuntu users who will use windows 8

1) Metro. Metro is a MOBILE operating system

2) Crappy interface

3) How the hell are you ment to use a touch screen interface with keyboard and mouse?

3) Windows 8 is a tablet OS.

4) Cant dual boot with linux and windows 8

5) Non apple tablets are not a succsess, as people who dont really know about computers don't know there are other tablets that are not apple.

6) No good for business 

7) Getting rid of the classic desktop.

8) Internet explorer. I mean like, who would want to use a mobile internet browser. Its like using the android browser on your pc. It will not work.

9) Getting rid of the start menu. I mean like, we have used the start menu since 1995, now we need to use a different start menu when the old one is fine?

10) Windows 8 is for the type who only like microsoft and think its the only operating system

---

### Post by Mars11 on 2012-04-09
> **linuxmaniack said:**
> This is why windows 8 will fail, RIP ubuntu users who will use windows 8

1) Metro. Metro is a MOBILE operating system

2) Crappy interface

3) How the hell are you ment to use a touch screen interface with keyboard and mouse?

3) Windows 8 is a tablet OS.

4) Cant dual boot with linux and windows 8

5) Non apple tablets are not a succsess, as people who dont really know about computers don't know there are other tablets that are not apple.

6) No good for business 

7) Getting rid of the classic desktop.

8) Internet explorer. I mean like, who would want to use a mobile internet browser. Its like using the android browser on your pc. It will not work.

9) Getting rid of the start menu. I mean like, we have used the start menu since 1995, now we need to use a different start menu when the old one is fine?

10) Windows 8 is for the type who only like microsoft and think its the only operating system

I disagree:
1) Metro works well on any device I've tested it on. The live tiles are amazing.

2) An opinion, I quite like the minimalist look

3a) It works quite well with a keyboard and touchpad, not as well with a mouse, but still very usable.

3b) Windows 8 works just fine on my laptop.

4) I'm dual booting. I just can't use the shutdown option in the charms bar.

5) Not so far, but they might very soon. Almost everyone knows what Windows is.

6) True, but that's not what they're aiming for.

7) I can still use the desktop with windows, I'm not sure what you're talking about.

8) Internet Explorer 10 is actually pretty nice.

9) Using the Metro UI as a Start Menu is a change, but once you get used to it, it's actually quite nice.

10) Pft, yeah right. Microsoft is defiantly low on my favorite companies list. I *KNOW* Windows isn't the only OS.

But this tread isn't about whether or not Windows 8 will be successful, it's a warning to people sharing partitions while dual-booting Windows 8 with any other OS.

---

### Post by sunfromhere on 2012-04-12
> **kurt18947 said:**
> Let's hope notebook manufacturers can resist any Microsoft 'recommendations' about locking secure boot on.

I can see that happening... no. HP doesn't even let you chose between graphic cards in BIOS, rendering all those Radeons across some models unusable*. It would be a real shock to me if they added a switch to BIOS for secure boot.

*This is a small personal grudge I have with HP :)

---

### Post by YannBuntu on 2012-09-21
**@all:**
please see
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)
[https://bugs.launchpad.net/wubi/+bug/1042159](https://bugs.launchpad.net/wubi/+bug/1042159)

---

### Post by Uncle Spellbinder on 2012-09-21
Hybrid boot (fast startup) can be disabled within Windows 8 easily...

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by tux-gamer on 2013-02-27
> **Uncle Spellbinder said:**
> Hybrid boot (fast startup) can be disabled within Windows 8 easily...

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)


Thanks, nice info...
I just buy Asus X201E, and it have Ubuntu 12.04.02
Ubuntu is great, but, recently i have try windows 8 premium trial.
and want to dual boot.

---

### Post by UltimateCat on 2013-03-01
Here's a workaround for the Windows 8 UEFI and How To :

[http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/](http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/)

It certainly (seems) as tho one would have to be a rocket scientist to understand this documentation-

---

