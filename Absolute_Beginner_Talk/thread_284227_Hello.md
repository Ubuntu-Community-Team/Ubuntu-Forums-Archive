---
title: "Hello"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by sharn on 2006-10-25
Hi this is, obviously Sharn. Anyhow, first thing I'd like to say is I LOVE Ubuntu. I'm only currently running it on VMWare on WinXP, and yet it still runs FASTER than XP. I was simply amazed.

It works perfect too, first time I booted up, it got on the internet, sound works, everything's great. I would have it installed on my old WinME PC, but when I try to dual boot it, it messes everything up. I think it's cause the hard drive is way to huge for ME's partitions. (250Gb) I don't mind for now though. Running it in VMWare is nice, cause I still have my XP when I need it.

Well, mostly just saying Hi. You'll probably be seeing me around. A couple questions:
First, this new version coming out, Edgy something (Just saw a topic on it, but.... I forgot already. >.<) Am I gonna be able to just update/upgrade, or is it going to be a complete reinstall? I  fell in love with Firefox 2, I used a script to update it in Hoary, but when I went to restart FF to test it, it was still running and wouldn't open. It was late and I forgot where the process manager was, so I haven't had a chance to test it yet...

Second, can I get an easy walkthrough on making Ubuntu play MP3's? I'm.... a little confused about it. But I have tons of songs, and messing with XP while in Ubuntu makes me lag bad, so I'd like to play them in Ubuntu.

I have to say great job on this awesome operating system. It's about 10x faster than Fedora Core 6 in VMWare, so I'm very happy. :)I'm hoping Linux eventually takes over the OS front. I'm happy to support it.

---

### Post by dca on 2006-10-25
You can try this:
 
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
 
Be careful, people been saying they have been getting errors when activating repositories on the third tab (I believe)
 
OR
 
[http://www.getautomatix.com/](http://www.getautomatix.com/)
 
Both are GUI-based shortcuts to installing codecs...

---

### Post by Bachstelze on 2006-10-25
Hi and welcome to Ubuntu :)

Yes, upgrading from Dapper to Edgy is perfectly possible, in two simple steps. I guess the Wiki has it all covered.

About your MP3s, I guess you missed the sticky at the top of that very forum ;)

---

### Post by Sef on 2006-10-25
> Second, can I get an easy walkthrough on making Ubuntu play MP3's?

Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by tubasoldier on 2006-10-25
Glad you like Ubuntu.

[www.ubuntuguide.org](www.ubuntuguide.org) has a lot of information about mp3 playback, movie playback, flash plugins, real player, adobe acrobat, ect... Its pretty thourogh. I would use that over EasyUbuntu or AutoMatix. Thats just my opinion anyways.

Hope this helps.

---

### Post by tubasoldier on 2006-10-25
> **Sef said:**
> Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

The Restricted Formats page has sure gotten a lot better since I first used Ubuntu. I remember back when it simply said that proprietary formats are not included with Ubuntu and why. It was rather helpful. lol.

---

### Post by Echo35 on 2006-10-25
I use Automatix, and it makes everything better. Easyubuntu also works well, but my prefrence is Automatix. As far as dual booting, it's quite simple. I've done it on a 300 GB hard drive and it's pretty easy. You will have to re-format (you can technically dual boot without re-formatting, but it's way too hard :) ) Simply put, it goes like this:
 
1) Boot off the Windows XP cd. When it goes into set up, you'll want to manually edit the partition table. It'll show your current XP partition. You are going to delete this partition and create a new one. It'll defualt to the entire drive, so you'll want to make it smaller by hand. Whatever size you want for Windows (remember that the Windows partition editor works in MB, not GB, so you'll want to calculate accordingly). Then, you are going to install Windows on this partition and leave the rest of the drive blank. 
 
2) When that's all finished (I have no idea why Windows takes longer to install less than Ubuntu takes to install more :-k ) put the Ubuntu CD in the drive and re-boot. When it loads, click the install icon on the Desktop. There will be an option to automatically format the remaining empty space left on the drive. Click that unless you want to edit the partition table manually. Whatever way you prefer.
 
As long as you install Windows first, it'll all work well. Windows likes to re-write the MBR (master boot record) so if you install it first, and then Ubuntu, the boot loader will work fine.

---

### Post by sharn on 2006-10-25
> **Echo35 said:**
> I use Automatix, and it makes everything better. Easyubuntu also works well, but my prefrence is Automatix. As far as dual booting, it's quite simple. I've done it on a 300 GB hard drive and it's pretty easy. You will have to re-format (you can technically dual boot without re-formatting, but it's way too hard :) ) Simply put, it goes like this:
 
1) Boot off the Windows XP cd. When it goes into set up, you'll want to manually edit the partition table. It'll show your current XP partition. You are going to delete this partition and create a new one. It'll defualt to the entire drive, so you'll want to make it smaller by hand. Whatever size you want for Windows (remember that the Windows partition editor works in MB, not GB, so you'll want to calculate accordingly). Then, you are going to install Windows on this partition and leave the rest of the drive blank. 
 
2) When that's all finished (I have no idea why Windows takes longer to install less than Ubuntu takes to install more :-k ) put the Ubuntu CD in the drive and re-boot. When it loads, click the install icon on the Desktop. There will be an option to automatically format the remaining empty space left on the drive. Click that unless you want to edit the partition table manually. Whatever way you prefer.
 
As long as you install Windows first, it'll all work well. Windows likes to re-write the MBR (master boot record) so if you install it first, and then Ubuntu, the boot loader will work fine.

Yeah, it would probably work if I started from scratch, but there's always lots of important files on that PC. And it's running on ME, because.... it's an OLD computer (5 years) We basically use it for storing large files over the network.

And thanks for the links, guys. Will check out when I get to play with it again. :)

BTW, never seen such an active forum IN MY LIFE. :P

---

### Post by Echo35 on 2006-10-25
Yeah, this is a pretty active and supportive community.

---

