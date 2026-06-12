---
title: "Yet another question..."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jordanae on 2007-12-08
I am trying to get a program called emesene (here: [http://emesene.org/trac/wiki/Installation](http://emesene.org/trac/wiki/Installation))
When I put the first line of code in this happens:

jordan@HP-Pavilion:~$ tar xvzf emesene*.tar.gz
tar: emesene*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Sorry about not having this in one of those boxes. How do I make those by the way?

---

### Post by taurus on 2007-12-08
Are you in the right directory?  Normally, you saved your downloads to ~/Desktop so change to that directory first before you try to unpack it.

```
cd ~/Desktop
tar xvzf emesene*.tar.gz
```

---

### Post by TeraDyne on 2007-12-08
Are you in the same directory as the tar.gz file when you run the command? That's the only thing I can think of.

---

### Post by jordanae on 2007-12-08
> **taurus said:**
> Are you in the right directory?  Normally, you saved your downloads to ~/Desktop so change to that directory first before you try to unpack it.

```
cd ~/Desktop
tar xvzf emesene*.tar.gz
```

Well I tried that but it didn't work for me.

---

### Post by taurus on 2007-12-08
What's the output of this command then?

```
ls -la ~/Desktop
```

---

### Post by jordanae on 2007-12-08
> **taurus said:**
> What's the output of this command then?

```
ls -la ~/Desktop
```

what's that?

---

### Post by caravel on 2007-12-08
Copy and past the command in to your terminal and hit enter, then copy and paste the results into your next post.  That way the files in that folder can be seen.

---

### Post by jordanae on 2007-12-08
This is what I got using all of the commands

```
jordan@HP-Pavilion:~$ ls -la ~/Desktop
total 48
drwxr-xr-x  3 jordan jordan 4096 2007-12-08 09:30 .
drwxr-xr-x 41 jordan jordan 4096 2007-12-08 11:03 ..
-rw-r--r--  1 jordan jordan  225 2007-12-07 18:12 HeroOnline.desktop
-rw-r--r--  1 jordan jordan  266 2007-12-07 18:12 Hero Online Web.desktop
-rw-r--r--  1 jordan jordan  248 2007-12-05 21:43 MySpaceIM.desktop
-rw-r--r--  1 jordan jordan 8313 2007-10-12 16:39 pidgin.desktop
-rw-r--r--  1 jordan jordan  284 2007-12-06 16:46 Trillian.desktop
-rw-r--r--  1 jordan jordan  777 2007-12-06 16:46 Trillian.lnk
drwxr-xr-x  4 jordan jordan 4096 2007-12-08 09:30 WoW-2.0.0-enUS-Installer
-rw-r--r--  1 jordan jordan  225 2007-12-07 18:40 Xfire.desktop
jordan@HP-Pavilion:~$ cd ~/Desktop
jordan@HP-Pavilion:~/Desktop$ tar xvzf emesene*.tar.gz
tar: emesene*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jordan@HP-Pavilion:~/Desktop$ ls -la ~/Desktop
total 48
drwxr-xr-x  3 jordan jordan 4096 2007-12-08 09:30 .
drwxr-xr-x 41 jordan jordan 4096 2007-12-08 11:19 ..
-rw-r--r--  1 jordan jordan  225 2007-12-07 18:12 HeroOnline.desktop
-rw-r--r--  1 jordan jordan  266 2007-12-07 18:12 Hero Online Web.desktop
-rw-r--r--  1 jordan jordan  248 2007-12-05 21:43 MySpaceIM.desktop
-rw-r--r--  1 jordan jordan 8313 2007-10-12 16:39 pidgin.desktop
-rw-r--r--  1 jordan jordan  284 2007-12-06 16:46 Trillian.desktop
-rw-r--r--  1 jordan jordan  777 2007-12-06 16:46 Trillian.lnk
drwxr-xr-x  4 jordan jordan 4096 2007-12-08 09:30 WoW-2.0.0-enUS-Installer
-rw-r--r--  1 jordan jordan  225 2007-12-07 18:40 Xfire.desktop
jordan@HP-Pavilion:~/Desktop$ 

```

---

### Post by taurus on 2007-12-08
Where did you save that file?  

```
find ~ -name emesene* -print
```

---

### Post by jordanae on 2007-12-08
> **taurus said:**
> Where did you save that file?  

```
find ~ -name emesene* -print
```

That code didn't tell me where. But I re-downloaded it and it says the location is just "/"

---

### Post by CaptainInsaneO on 2007-12-08
Then you need to do

```
cd /
```

and then untar it.

---

