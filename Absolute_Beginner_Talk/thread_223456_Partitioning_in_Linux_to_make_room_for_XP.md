---
title: "Partitioning in Linux to make room for XP"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by reykjavic on 2006-07-26
So, I just installed Ubuntu and xgl/compiz on my laptop, and it works perfectly! So i'm psyched.  However, I'd like to install XP as well, and to do this, I need to partition my HD, correct? (I=Neophyte).  So, if there was anyone who knew how to make this operation smooth, and how to partition my HD using linux, that would be great - I have an XP cd, so everything is ready to go, minus the partition.

Thanks a lot

---

### Post by FenrisAbraxas on 2006-07-26
> **reykjavic said:**
> So, I just installed Ubuntu and xgl/compiz on my laptop, and it works perfectly! So i'm psyched.  However, I'd like to install XP as well, and to do this, I need to partition my HD, correct? (I=Neophyte).  So, if there was anyone who knew how to make this operation smooth, and how to partition my HD using linux, that would be great - I have an XP cd, so everything is ready to go, minus the partition.

Thanks a lot

Ok, you can try to backup all your important data, remember that repartitioning a hdd is always risky and may cause data loss.

After that boot with the live cd and execute gparted (i think thats the program name, im a console man :P).

There make room for WinBlows XP and cross your fingers that your data is intact (i HAVE never had problems repartitioning but there's always the remote posibility of data loss).

Install WinBlows XP and after that you have to boot again using the live CD to reinstall grub so you can boot into Linux again.

If you need more help i'll be around.

Good Luck!

---

### Post by jd65pl on 2006-07-26
Note Windows XP tends to mess with the MBR (master boot record) its best to install XP then other distros.

---

### Post by FenrisAbraxas on 2006-07-26
> **jd65pl said:**
> Note Windows XP tends to mess with the MBR (master boot record) its best to install XP then other distros.

It's just a matter to install grub again in the MBR :S not that hard.

Also edit the menu.lst (takes 2 minutes to do it) to add:
```

title Windows XP
root (hd0,2) rootnoverify
chainloader +1

```

Just assigning random values for the HDD :P

---

### Post by jd65pl on 2006-07-26
You might find [these ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857")instructions useful

---

### Post by reykjavic on 2006-07-26
so, once I backup my stuff and put in the live cd, do I boot OFF the live cd? and then open terminal and type gparted? or is there something fancy i have to do - but thanks for the guide for the post xp installation linux recovery


hopefully this will work

---

### Post by jd65pl on 2006-07-26
**YOU SHOULD DEFINATELY BACK UP ALL YOUR INFO FIRST**

If you boot off the live cd once desktop is shown go to system then gparted. This application will do the partitioning for you and is fairly easy to follow.

Install XP

Re boot using the ubuntu live cd when desk-top is shown press ctrl + Alt +F1

Type "grub"

Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

Type "setup (hd0)", ot whatever your harddisk nr is.

Quit grub by typing "quit".

Reboot.
[URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857"]
CLICK HERE FOR SOURCE[/URL]

---

### Post by reykjavic on 2006-07-26
awesome, sounds great -- how do i find out what drive my /boot is on, and how that translates for teh grub command?

---

### Post by reykjavic on 2006-07-26
ah, my boot is on dev/sda1, so does that mean i'd have to type
root (hd0,0) ??

ty

---

### Post by jd65pl on 2006-07-27
That sounds about right.

Let me know if it all goes ok buddy

---

