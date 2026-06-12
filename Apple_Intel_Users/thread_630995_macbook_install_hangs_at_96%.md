---
title: "macbook install hangs at 96%"
date: 2007-12-03
forum: Apple Intel Users
---

### Post by ry4nolson on 2007-12-03
hi i'm trying to install Gutsy on my girlfriend's first gen 1.83Ghz macbook. I have tried both regular Gutsy and a Linux Mint 4.0 Install cd and both of the installations just hang up around 96%.

i put the lpj=7330000 in the boot options.

I don't know what's up with this. i have a first gen 2.0Ghz macbook and used the same process successfully.

any ideas whats causing it to hang up like this? could it be running out of memory or something? i didn't set up a swap partition.

---

### Post by wigglydiggly on 2007-12-04
Don't know but I believe that 96% is when the boot load its installed.  If I remember correctly I had to sync partition during the installation before it reached 96%.  Just an idea to look into.  

I'm not sure about the lack of swap issue.  Don't think that live cds use a swap so I don't see how that would be the problem.  It will be a problem later with hibernation though.

---

### Post by ry4nolson on 2007-12-04
yea that seems to be what the problem is. i finally just did a hard reset and the linux picture showed up on my refit menu but when you select it, it never goes past GRUB Loading Stage 2...  thanks for your help though. i just dont know why i didn't have to do that on my macbook installing gutsy, i actually remember doing that with the older versions.

---

### Post by cyberdork33 on 2007-12-04
> **ry4nolson said:**
> yea that seems to be what the problem is. i finally just did a hard reset and the linux picture showed up on my refit menu but when you select it, it never goes past GRUB Loading Stage 2...  thanks for your help though. i just dont know why i didn't have to do that on my macbook installing gutsy, i actually remember doing that with the older versions.
Just install manually and see what happens:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)
setup (hdX,Y)
quit
```You should replace the X and Y with the numbers found in the find command.

---

### Post by ry4nolson on 2007-12-04
what do you mean by install manually?

i ran those commands from the live cd and now i have 2 tux icons in my refit menu. one says linux from HD and one says linux from partition 3. and also another one for the livecd.

do i need to run those commands during the installation?

---

### Post by cyberdork33 on 2007-12-04
> **ry4nolson said:**
> what do you mean by install manually?

i ran those commands from the live cd and now i have 2 tux icons in my refit menu. one says linux from HD and one says linux from partition 3. and also another one for the livecd.

do i need to run those commands during the installation?

No. Try to boot the 'from partition 3' one. It should work.

---

### Post by ry4nolson on 2007-12-04
it doesn't. it does the same as the other one. it stays at "GRUB Loading stage2" forever and never changes

---

### Post by cyberdork33 on 2007-12-04
> **ry4nolson said:**
> it doesn't. it does the same as the other one. it stays at "GRUB Loading stage2" forever and never changes

Well, it may be that the grub in the MR is still the one being loaded, or the grub files on your linux partition are corrupted. 

Can you do the same thing to install grub manually, but for the last part, use (hd0) to install to the MBR instead of the partition, then try booting. Try both linux icons if one doesn't work. If that is still no good, then I would guess that the grub files are the issue.

---

### Post by ry4nolson on 2007-12-04
the other one just brings up a blank black screen with nothing on it. but the installation never finished it just froze at 96% so i had to hard reset i would assume this has something to do with it.

---

### Post by cyberdork33 on 2007-12-04
> **ry4nolson said:**
> the other one just brings up a blank black screen with nothing on it. but the installation never finished it just froze at 96% so i had to hard reset i would assume this has something to do with it. This is after trying to install to the MBR instead? If so, I am guessing that there are some files that didn't get copied or something after it hung.

---

### Post by ry4nolson on 2007-12-04
finally gave up and just tried fiesty and it installed perfectly.

---

### Post by Wintran on 2007-12-07
> **ry4nolson said:**
> hi i'm trying to install Gutsy on my girlfriend's first gen 1.83Ghz macbook. I have tried both regular Gutsy and a Linux Mint 4.0 Install cd and both of the installations just hang up around 96%.
I had the same problem, and I suspect the 512 mb memory is the issue - The installer did say that the lack of a swap partition could cause installation problems.

Did you try starting the live cd in safe graphics mode and install from there? It's one of the options you get when booting on the cd. Safe graphics mode did the thing for me, and the install went flawlessly, probably because it uses less memory (the install itself went much faster).

---

