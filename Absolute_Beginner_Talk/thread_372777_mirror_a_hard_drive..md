---
title: "mirror a hard drive."
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ktusyn on 2007-02-28
hey i don't know if this is something that is possible but... is there a way to mirror a hard drive from one computer to another.  i have a stand-alone pc that i use as a dummy to set up a web site and was wandering if there is an easier way to set up the server hard drive with the stuff i fixed/modified besides saving the files and placeing them in the right folder and changeing the settings.

---

### Post by punx45 on 2007-02-28
so you:

1. Set up webserver on "stand alone" PC..   (stand alone means not networked?) (what server? apache?)

2. Changed/fixed "things" on another PC.. (not sure what the "things" are, more detail would be helpful)

3. and now you want to move the "things" to the server?  and do "the settings" need to be changed? (again, more detail would be helpful)


yes you can do that.   change the settings if the settings require it.

---

### Post by c0nv1ct on 2007-02-28
do you mean mirror, as in, updated at intervals?  or just copy the entire contents of one PC over to another just once?

imaging one HDD to a disk, or series of disks, then applying that image to another computer is relatively easy.  But actually setting it up where one computer contacts another to copy the entire filesystem and then keep it updated at intervals would be somewhat difficult, but not entirely impossible.  It could be a security risk though, depending on how your network is setup.

---

### Post by ktusyn on 2007-02-28
sorry i run lamp on xubuntu,  i use it as a stand-alone that can be connected but only when i chose because i use it as a mock up for my real server. i do it this way so i can play around without worrying that if i screw something up it is just a mock up.  but  i have changed a lot around added phpmyadmin and a lot of the way it looks on the web pages and was wandering if there is anyway to send what i have done with out sending them over the network or using a cd and saving the files and putting them in the correct folder as i don't want to screw it up and crash the server

---

### Post by punx45 on 2007-02-28
for installing new software, just repeat the steps on the other machine to install that software.   for files like web pages etc. you should probably have the two machines on the same network so you can copy files from one to another either over FTP or NFS.  make changes to files on your test machine, then just copy them over to (and overwrite, backup first!) the files on the other.

---

### Post by ktusyn on 2007-02-28
thanx for the help will try that and see what happens


since i am in ext3 it shadows it's self right i mean i have it set up to so it should back it up when i transfer the file right

---

### Post by punx45 on 2007-02-28
not sure about that.

i would do manual backups to be safe.   either manual backups before you copy the new files over, or daily/hourly whatever works for you via cron or other backup software.

---

### Post by ktusyn on 2007-02-28
ok makes sense that would be better and safer thanx

---

