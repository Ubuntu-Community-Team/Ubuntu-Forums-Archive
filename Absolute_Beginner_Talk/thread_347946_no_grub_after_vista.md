---
title: "no grub after vista"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Skidlz on 2007-01-28
I started messing around with vista and came to find that grub wouldn't start. I looked over some things to fix it but nothing worked. I installed DSL with grub thinking I could go from there and add my other partitions but even that wouldn't work. I'm fine with totaly removing vista but I still wouldn't know how to get ubuntu or dsl to boot.  

Thanks!

---

### Post by benerivo on 2007-01-28
I can't really help as I've had no experience with the Vista, but here is a short article on the problems of dual booting Vista and Linux...
[http://desktoplinux.com/articles/AT2094892904.html](http://desktoplinux.com/articles/AT2094892904.html)

---

### Post by PixArtist on 2007-01-28
Couldn't you just set your linux partition back to boot?

---

### Post by hyper_ch on 2007-01-28
Use the live cd "recovery mode" (I think) to put grub back online :)

---

### Post by randiroo76073 on 2007-01-28
Here's a good tut on restoring grub from live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+from+live+cd](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+from+live+cd)
HTH

---

### Post by jpneal on 2007-01-28
Try Super Grub Disk. It's easy. Just choose the Automatic option.

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

... as recommended in the Ubuntu Guide.

---

### Post by Skidlz on 2007-01-28
Wow! Thanks for all the replies. I used one method with the live cd and I will try to reboot to hd. Fingers crossed :)

---

### Post by MkfIbK7a on 2007-01-28
vista apparently suppreses grub

some security caution the solution i read was to reset the bios...

EDIT: ahh heres the thread i saw
[http://www.ubuntuforums.org/showthread.php?t=106229&highlight=vista+grub](http://www.ubuntuforums.org/showthread.php?t=106229&highlight=vista+grub)

---

### Post by indytim on 2007-01-28
Installing Vista probably overwrote your MBR.  Re-installing GRUB should put everything right again so that both Ops can play nice.

IndyTim

---

### Post by RAV TUX on 2007-01-28
> **Skidlz said:**
> I started messing around with vista and came to find that grub wouldn't start. I looked over some things to fix it but nothing worked. I installed DSL with grub thinking I could go from there and add my other partitions but even that wouldn't work. I'm fine with totaly removing vista but I still wouldn't know how to get ubuntu or dsl to boot.  

Thanks!
There is a Linux Magazine out that gives specific instructions how to boot to Vista with grub....I believe Linux Pro....but go to your local bookstore and either copy the instructions or buy the magazine....if anybody has it please post here....I might try to go out and buy it myself

just know that there is a solution for this out already

---

### Post by Skidlz on 2007-01-28
vista is eeevil. My moto now is "If you need windows, wine and qemu are your friends." 
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+from+live+cd](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub+from+live+cd) 
is the link that worked for me. I gave it the proper partition (hd1,2) but it used (hd1,1) ?? but that was easy to fix. 

Again thank you for all the responses.

shame on you vista...

p.s. if you update to vista from xp the xp grub entrie will start vista.

---

