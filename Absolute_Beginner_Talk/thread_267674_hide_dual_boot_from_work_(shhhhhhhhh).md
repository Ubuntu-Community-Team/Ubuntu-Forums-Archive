---
title: "hide dual boot from work (shhhhhhhhh)"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by k9brand on 2006-09-28
my place of employment bought me a nice new laptop which I would like to dual boot with ubuntu for when I am home and need to get some *real work done.  Is there a way to have windows boot up and not have to choose my operating system at the start?

I would like to be able to press a button at the correct time and get to grub, but other then that, have it act like windows only (not even the 3 seconds where it says "press blah blah to get to grub)...

can anyone point me in the right direction?

---

### Post by jordanmthomas on 2006-09-28
You can change the timeout option in /boot/grub/menu.lst to 0.  
Then, set the default OS to match Windows (start counting at 0 and include the separator between Ubuntu and Windows...labeled "other" I think)
On my computer at home, my mom hasn't even asked me about anything unusual, so I guess she hasn't even seen the menu.

---

### Post by k9brand on 2006-09-28
that'll teach her!!! sneaky! thanks, I will try this.

---

### Post by jordanmthomas on 2006-09-28
If you need help figuring out what to put for default OS, just post the output of this and I can help out.
```

cat /boot/grub/menu.lst
```
Not sure if you'll need it or not, but...whatever.  ;)

---

### Post by k9brand on 2006-09-28
Thanks..  I'm going into work tommorow and will probably install ubuntu this weekend.  But this thread is now subscribed, so if I run into anything I will post.  Thanks so much! They'll never know :twisted:

---

### Post by confused57 on 2006-09-29
You might want to install with the alternate cd and opt to install grub to floppy & you can boot Ubuntu with the floppy...without floppy, your system boots to Windows.  Also, with the alternate cd, you could install grub to the root partition and boot with a GAG(floppy or cd) or Super Grub Disk(CD):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
See the sections for GAG and Super Grub Disk.

There is always the possiblity of problems booting to Windows by installing grub to the mbr...they're rare, but possible.  You'd need the Windows installation cd to repair the mbr, if you had problems booting.

If you do install to the mbr, you could set the timeout to 1 second...probably not a good idea to set it to 0.

You might want to explore all your options, get some more input from other posters, before you start installing Ubuntu...sinces it's your employer's computer.

---

