---
title: "My pc restarts during the loading of Ubuntu"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-20
Hi there, awhile back I ordered Ubuntu discs ( version 6.06 ). I got them and was very excited to try them out. I quickly had one in my PC ready to go, but when my pc booted up to the Ubuntu installer, I clicked on "start/install Ubuntu" and it loaded the Kernel and then my pc restarts. I kept trying all the other options the disc had ( check disc for errors, etc. ) and it kept restarting my PC. The only ones that work are boot from harddrive ( boots xp ) and to test my memory.

I decided not to worry and just go about with my XP experience, which I dislike, and now I am back to use Ubuntu. I download Version 7.04 with high hopes of not experiencing the same problems i had with 6.04, however I do run into the same exact problems I had with 6.06 and now I would like help.

I decided to go to the irc channel and get quick help. I did:

One of the users told me:

Press f6 and type "add acpi=off noapic nolapic" to the boot options, I do this and then it loads and I'm happy my pc hasn't restarted yet. However I quickly get this message:

Please append a correct "root" or boot option - root device "<null>"
VFS: Cannot open kernal panic - not syncing: VFS unable to mount root FS on unknown - block (8,3)

------

I don't understand this, as you can see I'm pretty Linux illiterate. The only Linux experience I had was with Mandriva, and that was very briefly. 

------

Thanks in advance.

---

### Post by zenwalker on 2007-04-20
> VFS: Cannot open kernal panic - not syncing: VFS unable to mount root FS on unknown - block

I guess, some things wrong with your HDD detection.

---

### Post by Zaosyn on 2007-04-20
Darn :(

---

### Post by Pobega on 2007-04-20
Try booting the Ubuntu 6.06 CD with those parameters, and see if that works if you.

If that's successful you can dist-upgrade into Edgy and then Feisty.

---

### Post by Zaosyn on 2007-04-20
I got the same exact error as 7.04 gave me :(

---

### Post by Bachstelze on 2007-04-20
Try with an Alternate CD.

---

### Post by Zaosyn on 2007-04-20
I get it on all of them :( . Would you recommend Mandriva? The installer on it works. But I would really like to give Ubuntu a try as I can see it has such a big fan base.

---

### Post by Bachstelze on 2007-04-20
Madriva ? No way ! I hate it with all my heart !

Try Debian, Gentoo, Slackware, Arch, FreeBSD... but not Mandriva !!

---

### Post by Pobega on 2007-04-20
Debian is my personal choice, it is as easy as Ubuntu is to set up (In my opinion), and doesn't make any of the decisions for you.

FreeBSD is my next choice, ports is a very nice and mature package manager, I've even heard that it settles dependencies better than APT on some occasions!

Gentoo would be my final choice, since it's basically the Linux equivalent of FreeBSD; Portage isn't a bad package manager, although it isn't anywhere near as polsihed as ports is.

---

### Post by Zaosyn on 2007-04-20
Good news! I decided to boot up again with my 6.06 disc, but this time I decided to go in text mode instead of the gui interface. I Typed in " live noapic=off " and now I'm in the live disc!!! 

Befor I put my 7.04 disc back in and try it with that.

What should I type in after **Boot:** to install Ubuntu?


For example:

Boot: LIve noapic=off


Also I Forgot how I got into Text mode.. =[

---

### Post by AAM on 2007-04-20
Zaosyn,

if Mandriva works, use it! Be pragmatic, it is all linux and free. I have used Mandrake, Mandriva, Ubuntu, Knoppix, Kanotix, Xandros, SuSE, RedHat and PClinuxOS .... I think that is all!

They all have their pros and cons, and our buddy **HymnToLife** has an opinion. Personally I love messing around with Ubuntu, but having installed 3 computers with PClinuxOS in the last 4 weeks, I was very impressed. 3D effects and wireless were very easy, and more easily achieved than Ubuntu - by a long way! It's a Mandriva fork. I also liked the look and overhead of Mandriva Metisse but I couldn't get it to install to harddrive, despite the instructions.

---

### Post by Zaosyn on 2007-04-21
Any other opinions :(? I actually got it to boot up in Live mode, however since then it just restarts >.<

---

