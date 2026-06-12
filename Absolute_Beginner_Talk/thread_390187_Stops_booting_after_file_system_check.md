---
title: "Stops booting after file system check"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Degeim on 2007-03-21
My Edgy Eft suddenly met some problems during boot sequence. 

Before it occured, I edited /etc/event.d/rcS and /etc/init.d/rcS (trying to install splashy), but I'm quite sure I've redone the changes in those files now. Still the same problem:

It boots, and the Ubuntu logo with progressbar shows up, and the progressbar finishes. After that, the logo and bar disappears, and following lines are coming up:

```
Activating swap...  done.
Checking root file system...fsck 1.39 (29-may-2006)
/dev/hda1: clean, 181580/2959712 files, 3286101/5927977 blocks
done.
Checking file systems...fsck 1.39 (29-may-2006)
done.
```

And nothing more happens.

Whats wrong?

---

### Post by twikletoes on 2007-03-21
Have you tried to press ctrl + alt + F7? (May want to press F2-F6 if F7 doesn't pop anything up but try F7first.)
That could get you somewhere.

---

### Post by Degeim on 2007-03-22
I can access the virtual terminals, which I have done to undo my changes, but the F7 does not work.

More suggestions?

Thanks

---

### Post by twikletoes on 2007-03-22
What exactly did you change in those files? 
Tell me what you changed so i can help you out further.

---

### Post by Degeim on 2007-03-22
I actually don't know what caused the problem, but the uptime before they occured where relative short, so what I did can be enlisted here. But what I don't know is if I did anything the wrong way; perhaps I wrecked it with something totally different than what I was supposed to do.

 Anyway, those are all the changes I can remember to have done:

1: [http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_does_not_run_under_upstart_in_ubuntu_edgy_and_later_versions](http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_does_not_run_under_upstart_in_ubuntu_edgy_and_later_versions)
This is - as far as I know - undone.
2: [http://splashy.alioth.debian.org/wiki/doku.php?id=faq#i_don_t_see_any_image_at_boot_time](http://splashy.alioth.debian.org/wiki/doku.php?id=faq#i_don_t_see_any_image_at_boot_time)
This is undone (by running "update-grub")

And finally, the one I suspect caused it:
[http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_just_doesn_t_work](http://splashy.alioth.debian.org/wiki/doku.php?id=faq#splashy_just_doesn_t_work)
This was the last thing I done before rebooting.

If you need more to help me, I'll be glad to help you help me :wink: 


Thanks, 
Degeim

EDIT: After thinking a bit, I may have rebooted without problems between step 2 and the suspected step, which increases my suspicion against it. Did I remove something I shouldn't have removed?

---

### Post by twikletoes on 2007-03-22
can you tell me everything that it says in the file thing 


                             /etc/init.d/rcS

can you tell me exactly what you were trying to change in both file things?

---

### Post by Degeim on 2007-03-22
Thank you for your patience, but I finally got it working again, by reinstalling some packages (usplash, libdirectfb and libsysfs).

---

### Post by twikletoes on 2007-03-22
Thats good, I hope i help at all in any way

---

