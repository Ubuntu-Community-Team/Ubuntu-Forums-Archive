---
title: "&quot;How to&quot; rip XP cd to HD as .iso"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by longboneslinger on 2007-11-24
[SIZE="4"][COLOR="DarkOrange"]Ok. im using 7.10 and I just set up VMWare and I want to rip a copy of the xp home cd to an .iso on my HD so I don't need it in the cdrom. It runs fine, I just need the .iso.
I followed a tutorial at LinuxGamers that didn't work. I even tried PowerISO. The terminal says 'poweriso command not found but ./poweriso -? gives this as the starting command.
I tried k3b but it only seems able to make a temp copy and wants me to burn it to a cd/dvd. 
Ubuntu is great but my wife keeps rebooting to xp. It's driving me nuts so I gotta get this straightened out.
Come on oh gurus, toss a noob some help! Please?
Many thx in advance,
bone [/COLOR][/SIZE]

---

### Post by jordanmthomas on 2007-11-24
```
dd if=/dev/cdrom of=my_cd_image.iso
```
Then, once it's done, you'll have a file called my_cd_image.iso
This does a raw copy of what's in your cdrom (if) and puts it into a file (of)

---

### Post by Flying caveman on 2007-11-24
Have you tried putting the CD in the optical drive?

I think a little box pops up and askes you want to do.

you might want to pick someting like save disk as image or something :confused:

---

### Post by gn2 on 2007-11-24
Use VMWare Server and install XP into a virtual PC using the CD.

---

### Post by fidge on 2007-11-30
dd if=/dev/cdrom of=my_cd_image.iso

this code works heaps well for any CD. i used it for ms office 07 enterprise (i know:mad:) 

thanks

---

### Post by fidge on 2007-11-30
thanks heaps for the above code jordanmthomas

---

### Post by travnewmatic on 2008-01-29
> **jordanmthomas said:**
> ```
dd if=/dev/cdrom of=my_cd_image.iso
```
Then, once it's done, you'll have a file called my_cd_image.iso
This does a raw copy of what's in your cdrom (if) and puts it into a file (of)

Thanks so much.  This is retardedly easy.  No more Roxio or Nero for me.

---

### Post by jordanmthomas on 2008-01-29
That's one of the best things about Linux (GNU/Linux really, but let's not get into that here).
There's lots of tools that do one thing extremely well.  Nero does LOTS of things, sure, but I'm a keep it simple stupid kind of person.

---

