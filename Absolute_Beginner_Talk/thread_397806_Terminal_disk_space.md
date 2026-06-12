---
title: "Terminal disk space?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-03-31
hi,

Is there anyway of checking how much disk space i have left and have used via a linux terminal?.

I have a server pc setup, and i ssh into it from another pc. It has a 10gb (i think)hard-drive for the linux installation, and another 20Gb hdd (sure on this one) setup for /home.

Thing is i installed Torrentflux on the box, set it up to use a folder etc. But it says i've used over 99% of the space and syas 180mb is left on the drive. There is about 16GB of backedup data being stored on a folder in my user name (shared via samba), a 1Gb folder in downloads, and a 200mb file being stored on the drive in downloads, there was also a btcurses file being downloaded which would be 1GB tops, and im unsure on how to kill that now.

So i would just like to be able to figure out what's going on with my disk usage, as i will be upgrading to a nice 200Gb hard-drive soon, but i want to know how to effectively manage it.

---

### Post by Pom2122 on 2007-03-31
df

---

### Post by lambros on 2007-03-31
Hi,

'df' is the command to use.  Also, 'df -h' will make the numbers more human-readable.

HTH,
Lambros

---

### Post by ben.s on 2007-03-31
If you're using a GNOME 2.18 machine locally (i.e., not your server), you can also use the new Disk Usage Analyzer on remote folders.  It can go in via SSH, WebDAV, Samba, FTP, and do a remote filesystem scan and give you a nice visual representation of where your space is going.  It's way cool and works on servers without a GUI quite nicely.

---

### Post by 13ojo on 2007-03-31
thanks df is working good i think, telling me the same as the program.
now the only other thing is... df doesn't work on folders :(, how can i check folders stats?.


would use the gnome thing, but alll pcs are still in windows land. ( for stuff that linux and windows both can do nicely, i have linux going on the server, its just better. but games and other stuff i need my windows)

---

### Post by lambros on 2007-03-31
Hi,

For folders, the 'du' command might be helpful.

Lambros

---

### Post by 13ojo on 2007-03-31
yep i found that by myself while ls ing lots of folders.

all terminal commadn would be in my /bin? folder
so if i ls it i could randomly check what each does?

---

### Post by lambros on 2007-03-31
Yes, there are some commands in the /bin folder.  But there's lots of stuff in /usr/bin as well, and other places.  You can get the full search-path using the command
```
echo $PATH
```
And that's not all - there are shell "builtins".  Use
```
help
```
to get a list of these.

Lambros

---

### Post by h0ax on 2007-03-31
additionally you can type 
> man commandname
to read the manual for each command
just push q when you're done.

---

