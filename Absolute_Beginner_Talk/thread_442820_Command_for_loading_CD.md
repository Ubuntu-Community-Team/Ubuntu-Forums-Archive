---
title: "Command for loading CD?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-05-13
I know that if you enter eject in terminal it will eject but how do you get it to load?

---

### Post by jfinkels on 2007-05-14
> **thelocust said:**
> I know that if you enter eject in terminal it will eject but how do you get it to load?

What do you mean, load? You mean putting the cd in? There may be a utility out there for some cd trays, but others (like the one on my laptop) have no electronic mechanism for moving IN, only for ejecting (i.e. I have to push it in myself).

---

### Post by vanadium on 2007-05-14
Indeed, for trays like these from laptops, there is no software way to close the tray.  Otherewise, cdrecord (wodim in Ubuntu) should allow you to close and eject the CD. Look up "man cdrecord" or "man wodim".

---

### Post by lakersforce on 2007-05-14
But there are some trays that can close machinically. I remember some windows programs that had this feature (not to mention the Mac). Are there any commands to close the tray?

---

### Post by Outrunner on 2007-05-14
I think he means mounting the CD.

```
sudo mkdir /media/cdrom0
```

to make the CD directory and then

```
sudo mount /dev/cdrom0 /media/cdrom0
```

to mount your CD.

---

### Post by thelocust on 2007-05-14
Sorry I meant a command to physically close the tray if you type eject it opens I'm looking for the opposite. I'm know this is possible because K3b can open and close the tray. Thanks.

---

### Post by Rinzwind on 2007-05-14
Add -t to the eject command:

eject -t /dev/cdrom


From the man-page: > 
LONG OPTIONS
       All  options  have corresponding long names, as listed below. The long
       names can be abbreviated as long as they are unique.

       -h --help
       -v --verbose
       -d --default
       -a --auto
       -c --changerslot
**       -t --trayclose**
       -x --cdspeed
       -n --noop
       -r --cdrom
       -s --scsi
       -f --floppy
       -q --tape
       -V --version
       -p --proc


NOT every cd player supports this tho.

---

### Post by thelocust on 2007-05-14
Outstanding thanks allot.

---

### Post by jfinkels on 2007-05-14
> **Rinzwind said:**
> Add -t to the eject command:

eject -t /dev/cdrom


From the man-page: 

NOT every cd player supports this tho.

Good call, Rinzwind!

---

### Post by Dr Small on 2007-05-14
I wrote a funny shell script :P
Go to the terminal and type:
```
sh cdtray.sh
```

Enjoy.

Dr Small

---

