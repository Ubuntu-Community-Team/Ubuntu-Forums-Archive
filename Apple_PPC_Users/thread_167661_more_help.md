---
title: "more help"
date: 2006-04-28
forum: Apple PPC Users
---

### Post by Goemon4 on 2006-04-28
ok i installed kubuntu and everything. the problem is i stored all of my files (music, photos, docs) onto my 30 gig hfs formatted ipod  ](*,) ...im wondering how i can get them off of my ipod and onto my mac???

thanks
  -Goemon4

---

### Post by Gannin on 2006-04-29
Your kernel might already have HFS support compiled into it.  Does nothing happen when you plug your iPod in?  Have you tried to mount it manually?

---

### Post by Goemon4 on 2006-04-29
when i plug it in it says 

An error occurred while loading media:/sdb4:
The file or folder media:/sdb4 does not exist.

what doesx that mean?

---

### Post by Goemon4 on 2006-04-29
when i mmont it (or try to) it  says

An error occurred while loading media:/sdb4:
The file or folder media:/sdb4 does not exist.

---

### Post by Gannin on 2006-04-29
What commands are you typing when you try to mount it manually?

---

### Post by Goemon4 on 2006-04-29
i typed mount hit enter

then it showed everything mounted and it included the ipod, but it just wouldnt read it...

---

### Post by Gannin on 2006-04-30
Try plugging in your iPod and then type &#8220;sudo mount /dev/sdb4 /mnt&#8221; and hit enter, and see what messages it gives you.

---

### Post by Goemon4 on 2006-04-30
i will but i neeed to re-install it kubuntu i had to reinstall the mac osx, ill try it tomorrow...thanks

---

### Post by 3rdalbum on 2006-05-01
[QUOTE=Goemon4]i will but i neeed to re-install it kubuntu i had to reinstall the mac osx, ill try it tomorrow...thanks[/QUOTE]

Are you saying that you're re-installing Kubuntu to get the yaboot menu back? If so, you don't need to do that. Just boot into Open Firmware, type "boot hd:x,yaboot" where x is the number of your Yaboot bootstrap partition (guessing won't hurt your computer), then when you're in Ubuntu run ybin from the command line.

You may also want to consider doing a

```
sudo apt-get install hfsutils hfsplus
man hfsutils
```

And once you know how to use those command-line utilities, use them to copy the stuff from your iPod.

Alternatively, add your iPod's device address to your fstab file and do "mount -a" to get it on your desktop?

---

