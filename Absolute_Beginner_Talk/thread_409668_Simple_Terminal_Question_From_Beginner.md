---
title: "Simple Terminal Question From Beginner"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Frederick J. Harris on 2007-04-14
Just starting with Ubuntu.  The other day I'm almost sure I was able to open up a Terminal Window and change my current directory over to either of my Windows partitions on my harddrive (I have a dual boot setup with Win XP).  I thought I figured out something like this

fredharris@CODEWARRIOR: /$ cd /hda1 [ENTER]

or 

cd /main   (I have the volume named 'main')

I've tried a lot of combinations but somehow I can't remember what I did!  Or am I just imagining it.  How do you go to one of the other mounted 'drives' from root in Linux!

---

### Post by N Clement on 2007-04-14
Well, if you have mounted a drive, it could technically be anywhere, but the standard is to mount them in the /mnt directory.  In your case it would be:

/mnt/main

EDIT:

If you haven't mounted it yet, then you will have a choice.  If the drive is NOT ntfs, I would just do:```
sudo mount /dev/*drivename* /mnt/main
```

where *drivename* is the name of your drive, mine has partitions sda1-sda4.  You can check what yours is by looking in /dev

If your drive is ntfs (it probably is if it's a recent MS partition), then you will need to get the package ntfs-3g, which you can get from synaptic package manager (system->administration->Synaptic)

---

### Post by omgitsruss on 2007-04-14
My Ubuntu install mounts my NTFS (Windows) partitions by default in /media.

Try:
```

cd /media/main
```

Works fine for me.

Bear in mind, you will need to install the ntfs-3g package if you want write access to your NTFS partitions.

---

### Post by Frederick J. Harris on 2007-04-14
Thanks N Clement and omgitsruss!  Right after I read N Clement's reply I went down stairs, booted up Linux and tried CD /media/hda1 and it worked fine!!!!  I'll get this yet!!!  How do you mark a post as resolved?  Havn't figured that out yet  :confused: 

fred

---

### Post by Sef on 2007-04-14
> How do you mark a post as resolved? Havn't figured that out yet  

In your first post, click edit > go advanced > check 'This thread **IS** resolved' > save.

---

### Post by Skidpad on 2007-04-14
> **Frederick J. Harris said:**
> How do you mark a post as resolved?  Havn't figured that out yet  :confused: fred

Go back to your original post in this thread, click "edit",  "go advanced" and then you will see a place to tick a box to mark your thread resolved.  Once you've ticked the box, click "save changes"

:)


^^^ Sef...lol, posted @ the same time.

---

