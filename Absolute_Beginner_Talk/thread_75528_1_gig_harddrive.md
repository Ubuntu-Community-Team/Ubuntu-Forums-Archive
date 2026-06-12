---
title: "1 gig harddrive?"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by grimdaze on 2005-10-13
my sister has an old pc with a 1gb harddrive running w2k......if we went completely over windows would ubuntu fit on there?

---

### Post by Kapre on 2005-10-13
[QUOTE=grimdaze]my sister has an old pc with a 1gb harddrive running w2k......if we went completely over windows would ubuntu fit on there?[/QUOTE]

That's tough. If you really wanted to ditch M$ and use linux, I would suggest DSL (damn small linux) only 50MB and you've got the rest for the other stuff. I dont think even Mepislite would fit it in 1 gig. This is just my thought..there maybe some more who has a better idea.

K

---

### Post by Wolki on 2005-10-13
Default ubuntu wants about 1,8 gb of hard disk.

You use the server install to get a minimum system (command line only, about 350 mb needed) and then selectively install GUI programs to keep it below 1gb, but it's a little tight. I'd recommend using something like IceWM instead of gnome, for example.

---

### Post by grimdaze on 2005-10-13
alright thanks guys i'll check into those........but we'll probably just make an investment in a new comp

---

### Post by skoal on 2005-10-13
Ah, hold dem little horsies.  You need some XFCE lovin'...

1. Choose server install
2. Partition like this:

hda1, /boot - 32 MB (ext3)
hda2, swap - 128 MB
hda3, / - rest of hda

3. reboot. Login.
4. sudo apt-get update
5. sudo apt-get install x-window-system-core xfce4 synaptic
6. sudo dpkg-reconfigure xserver
7. startxfce4

...then, just use synaptic to add what you want.

If you don't want to type 'startxfce4' each time you login, you can:

8. sudo apt-get install gdm

I had firefox, Gimp, xscreensaver, and few other minor apps running XFCE4.2 all under ~600MB. Which should leave you ~300MB for a whole lot of other apt-get fun...

* My prior assumption about this install is that you at least 128MB.  Ubuntu should run just fine even on an older P2.  You'll love it!  Save the money you were gonna spend on a new computer for your next mortgage payment.

\\//_

---

### Post by fourchannel on 2005-10-14
```
 1. Choose server install
 2. Partition like this:
 
 hda1, /boot - 32 MB (ext3)
 hda2, swap - 128 MB
 hda3, / - rest of hda
 
 3. reboot. Login.
 4. sudo apt-get update
 5. sudo apt-get install x-window-system-core xfce4 synaptic
 6. sudo dpkg-reconfigure xserver
 7. startxfce4
 
 ...then, just use synaptic to add what you want.
``` 
thank you!

Skoal you are awesome..... this is the missing piece to the jigsaw puzzle that is my friend's mom's crappy computer's lagginess. =P

but really, thanks, that's gonna make it sooo much faster now.

---

