---
title: "how do you play games with wine?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by iidestined on 2007-03-25
this must be a complete newbie question. but i guess this would be the place for them. I installed wine last night and i would like to install starcraft broodwars. starcraft seems to be compatible with wine so how do i actually install and play starcraft? thanks for any help.

---

### Post by Lord Illidan on 2007-03-25
Try these links : [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Starcraft](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Starcraft)

[http://koti.mbnet.fi/~hoppq/sc-howto.html](http://koti.mbnet.fi/~hoppq/sc-howto.html)

Post here if you have any more queries..and search the forums and google.

---

### Post by iidestined on 2007-03-25
thanks a lot. that should be very helpful for this newbie.

---

### Post by iidestined on 2007-03-25
when i open wine i get an warning message:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.

and i can't seem to access the cd rom drive from the terminal. it should be the d drive.

---

### Post by halitech on 2007-03-25
works like a charm. My nephew will be very happy that he can still play Starcraft when I move him over to Xubuntu.

---

### Post by halitech on 2007-03-25
> **iidestined said:**
> 
and i can't seem to access the cd rom drive from the terminal. it should be the d drive.

Linux doesn't use drives so if you are entering d:\ expecting to see the drive, it won't. you need to point it at the mount point. try

```

cd /mount/cdrom0

```

---

### Post by iidestined on 2007-03-25
> **halitech said:**
> Linux doesn't use drives so if you are entering d:\ expecting to see the drive, it won't. you need to point it at the mount point. try

```

cd /mount/cdrom0

```

doesn't seem to work. 
this is what the wine looks like.

[img]http://uploader.ws/upload/200703/Screenshot_5.png[/img]

---

### Post by Patrick K on 2007-03-25
I suggest typing "winefile" in a terminal window (to open wine's file manager) then navigating to the CDRom and double clicking on the setup file.

---

### Post by iidestined on 2007-03-25
that worked until i typed in the cd key and then it gave me a "path not found" error

---

### Post by Patrick K on 2007-03-25
I see an error on the drive assignment. Notice that the Drive letter "C" points to the cdrom. It should point to "../drive_c". This is the fake C:\ drive wine provides for MS programs to reside in. See how mine is. 

Try autodetect again. If that doesn't correct the situation, you'll need to manually assign the correct drives letters to the device. .

---

