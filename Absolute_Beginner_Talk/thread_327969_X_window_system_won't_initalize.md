---
title: "X window system won't initalize"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2006-12-30
I have installed Ubuntu 5.10 on my PC. There are two partritions on one hard disk, one with Microsoft XP, the other with Ubuntu ( I can't delete XP, 'cause i'm not the only one using the PC ).
When i try to boot Ubuntu i get an error message that My X window System isn't configured properly. Here is the message i get :

( NOTE : i have written this with pencil, so there might be some typo's )

[i]
X Window System 6.8.2 ( ubuntu 6.8.2-77 20051010174525 [email]root@veradsky.buil[/email]dd )
Release Date : 9 Feb 2005
X Protocol version 11, revision 0, Release 6.8.2
Build operating system : Linux 2.6.10 i686 [ELF]
Current operating system : Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date : 10 Oct 2005
Module Loader present
OS kernel Linux version 2.6-12-9-386(buildd@rothera)(gcc version 3.4.5 20050809 ( prerelese ) ( Ubuntu 3.4.4 - 6ubuntu8 )) #1 Mon Oct 10 13:14:36 BST 2005
Markers: (--)probed, (**)from config file, (==)default setting,
[/i]

Also note, that when i insert the live cd, the same thing happens. ( But the problem isn't in CD's 'cause the live cd worked a couple of months earlier )

This is the first time i have tryed to install Linux distribution. I have exp with C++ and Java, so i'm not a complete beginner.

If someone had the same problem, please help!

---

### Post by jvc26 on 2006-12-30
Is there any reason why you're putting 5.10 on? You could try again with 6.10 (the newest distro) or try with the alternate install cd?
Il

---

### Post by Sasa_Ivanovic on 2006-12-30
5.10 version is all i have. I can't get 6.10 anywhere.

---

### Post by jvc26 on 2006-12-30
You can download it from [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)
 or you can order a cd from them of 6.06 if you wanted.
Il

---

### Post by Sasa_Ivanovic on 2006-12-30
I knew that. Still i want to install this version. Don't ask me to explain why, it's complicated.

---

### Post by slimdog360 on 2006-12-30
I couldnt notice anything special from that output you wrote (congrats on that to, most people wouldnt go to the trouble). Im guessing by the title that you managed to install ubuntu properly but it just isnt loading, is this right? If you are able to get to a console login try this (Im not to sure if this will work as I have a feeling it was introduced in dapper) ```
sudo dpkg-reconfigure xserver-xorg
```

If you cant download 6.10 you can always get a dvd from amazon, I think it comes with some extra packages so you shouldnt have to download to much.

---

### Post by Sasa_Ivanovic on 2006-12-30
> Im guessing by the title that you managed to install ubuntu properly but it just isnt loading, is this right?

Yes it is.
I'm gonna try that code right now!

---

### Post by sardion on 2006-12-30
Hate to say it but we're going to need the rest of the X server output....

Look for anything that starts with (EE) in the rest of the log and post that.

---

### Post by Sasa_Ivanovic on 2006-12-30
That is all i get in my log. I mean that's displayed on the screen. Is there any file i should open for a complete log or something ?

Also i have tryed the above command, here is what i did :
[i]
( Note : i have GeForce 7600 GT 256 MB )
1. I booted Ubuntu in recovery mode
2. then as a root, i typed the "sudo dpkg-reconfigure xserver-xorg"
3. i have followed the wizard
   - x server driver  = "nv"
   - bus indentifier = "PCI:1:0:0"
   - memory = "256000"
   - kernel framebuffer = "Yes"
   ( have i made a mistake in this config )
4. then i restarted
5. I booted Ubuntu normally
6. the same problem occured
[/i]

---

### Post by Sasa_Ivanovic on 2006-12-30
ok, i have an idea to why this problem is occuring :

When i tryed Live cd a couple of months earlier i had a diffrent computer.
The thing is : i had an older graphics card : "GeForce 5600 FX" which was supported by Ubuntu 5.10
But then i bought the new graphics card : "GeForce 7600 GT" whose driver wasn't present in the old Ubuntu 5.10

So i gues Ubuntu 6.10 supports this card, can i check this somewhere ?
Also, when is the new version of Ubuntu coming out ?

---

