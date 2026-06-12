---
title: "made command in term messed up"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-10-28
i was trying to get my sound to work right did this

sudo pico /etc/modprobe.d/options

and added this
options snd-hda-intel position_fix=1 model=3stack 

now i have nothing how can i undo thos commands

---

### Post by Daveth on 2007-10-28
cannot you just open the file using your first command, then delete the new line or return it to its previous value or comment it out, then save the file over itself?

---

### Post by Delkster on 2007-10-28
> **trucker33377 said:**
> now i have nothing how can i undo thos commands

Do you mean that you can't even boot the system properly?

You might want to try single user (recovery) mode from the boot-up menu, or booting from a live CD if that doesn't work. That way you should be able to get the system up and running at least to some degree, and could then edit the file again to revert the changes.

If you boot from a live CD you'll have to mount the hard disk partition containing your Ubuntu installation so that you can access the files on that partition. You can then open the file again in an editor and change it back. Try booting normally after that.

---

### Post by trucker33377 on 2007-10-28
1st when i retry that command the added option is not there.

2nd yes sys boots but sound slider is not there if i go to sound options to test i get 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: no element "gconfaudiosink"

---

