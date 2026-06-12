---
title: "[SOLVED] Loss of account privileges?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by XopherLorenz on 2008-01-17
This is kind of strange, and I'm fairly confident that I did something wrong to cause this (though for the life of me I can't think of what it is).  Under my System > Administration menu, there used to be a great deal of things there, like the ever-important synaptic package manager.  Now all that's there is the keyring, network tools, printing, system log, system manager and update manager.  There used to the the 'User Groups' thing, or something like that (I don't remember it's exact name), but if i remember correctly, it could be used to change what privileges an account had.  I no longer have that there so I don't know how to make myself able to get my administrative functions back.  Help please?

---

### Post by hyper_ch on 2008-01-17
can you still use sudo?

e.g.

```

sudo apt-get update

```

---

### Post by XopherLorenz on 2008-01-17
no.  It's extremely distressing :(

---

### Post by hyper_ch on 2008-01-17
then it's time to

(a) grab your live cd

or

(b) boot into recovery mode



If you select (a) then mount your drive (it may already be mounted somewhere, open the [/path/to/drive]/etc/group file and add your username at least to those groups here:

```

adm:x:4:hyper
dialout:x:20:hyper
cdrom:x:24:haldaemon,hyper
floppy:x:25:haldaemon,hyper
audio:x:29:hyper
dip:x:30:hyper
video:x:44:hyper
plugdev:x:46:haldaemon,hyper
scanner:x:104:hplip,hyper
lpadmin:x:108:hyper
admin:x:109:hyper
netdev:x:115:hyper
powerdev:x:117:haldaemon,hyper

```
"hyper" is my username. So just add yours accordingly. Although I think "admin" and "adm" are probably the essential groups...

if you select (b) you can do the same... or you can start x (I think recovery mode boots into shell) by issuing
```

startx

```
And then go to user administration and make your user admin again.

---

### Post by XopherLorenz on 2008-01-17
Thank you SOOO much.  You're a life saver.

---

### Post by DrMega on 2008-01-17
This happened to me once. I found advice on this very forum that suggested I boot in recovery mode, then run adduser but I can't remember the parameters I had to specify. One command did the trick though.

---

### Post by hyper_ch on 2008-01-17
Which path did you use? a or b?

---

### Post by XopherLorenz on 2008-01-17
I think i sort of combined the two.  I booted up in recovery mode and tried to edit the user groups and that didn't work for some reason, but when i issued startx it said that i had full privileges.  So i figured I'd made the changes to the groups file from there.  I didn't have permission to do it from the live cd or from my normal account.  But anyway, I did all that and am now back to normal.

---

### Post by Courtland on 2008-01-20
Ok ive totally broken this thing now...
I used nautilus to open my file system in root. then i went and changed the permissions and made my user name the owner. after that, synaptic, nautilus, and terminal would no longer work. I recieved the message that "user root does not exsist. so upon reboot it would load my hal and so i rean the system in recovery and ran :startx". I tried to change the permissions back, rebooted and no effect. then for some reason (call me stupid if I am) but I ran "fsck" which did not complete before my battery died...now it wont even give me the option for the boot menu, it just says:
Grub loading, please wait...
Error 17
and it doesnt go anyfurther than that...I reall messed this thing up pretty good and Im wondering if a fresh install would be in my best interest? Can someone please help me before I break it anymore? that is if there is anything left to break....

---

