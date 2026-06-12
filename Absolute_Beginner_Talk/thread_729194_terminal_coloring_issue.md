---
title: "terminal coloring issue"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by stainless_steel on 2008-03-19
alright, ive got a minor terminal issue:
it shows files and directories and stuff in nice convenient colors, but only on my main hard drive. when im in my storage hard drive all the directories are highlighted and impossible to read. see image:
any advice?
thanks!

oh btw: screenshot+GIMP=totally awesome!

---

### Post by Captainm on 2008-03-19
You could try changing terminals color scheme. "Edit > profiles > the profile you're using > colors".

---

### Post by stainless_steel on 2008-03-20
yeah, ive already messed around in there a  bit. thats how i set it to green on black. even if i go back to the default it still does the same thing.

---

### Post by OffAxis on 2008-03-20
would that be an NTFS storage drive?

---

### Post by Captainm on 2008-03-20
But what if you fiddle around with the palette?

---

### Post by stainless_steel on 2008-03-20
why, inspector monk, indeed it *IS* an NTFS.

---

### Post by stainless_steel on 2008-03-20
Dude! monkey island! that game was awesome!

---

### Post by Junglizer on 2008-03-20
If you don't mind editing text files, you should be able to change the listing output of dircolors which is actually the control of LS_COLORS which is what you're viewing.

---

### Post by Junglizer on 2008-03-20
Try an ```
slocate dircolors
``` to see where it is, though I believe it is located in */etc*.

---

### Post by stainless_steel on 2008-03-20
dave@dave-desktop:~$ slocate dircolors
/usr/share/man/man1/dircolors.1.gz
/usr/bin/dircolors

its an executable. not a text file

---

### Post by jordanmthomas on 2008-03-20
You should be able to fix this by changing the way you mount the external hard drive.
The reason these are showing up like they are is that **every** file on your ntfs partition is executable.  If you add 
```
dmask=000,fmask=111
```
to the options you mount the partition with (in /etc/fstab) then the directories will still be executable but not executable.

If your drive is automounted, you can edit HAL rules to make it do this.
(Sorry, arch wiki, but it should still work)
[http://wiki.archlinux.org/index.php/HAL#Allow_dmask_and_fmask_for_ntfs-3g](http://wiki.archlinux.org/index.php/HAL#Allow_dmask_and_fmask_for_ntfs-3g)

Hope this helps some and may lead you in the right direction

---

### Post by Junglizer on 2008-03-20
Yeah that would probably work better. I was just trying to get at the source so he wouldn't have the same issue with other drives later. Been a while since I did anything specific with dircolors anyways :P

---

### Post by stainless_steel on 2008-03-20
no change. could be conflicting with the defaults?

```
defaults,dmask=000,fmask=111
```

---

### Post by stainless_steel on 2008-03-30
bump

---

