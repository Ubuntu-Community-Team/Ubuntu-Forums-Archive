---
title: "Trouble compiling fluxbox from source"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Mairi on 2007-04-15
I hope this isn't too garbled. I tried the version of fluxbox in the repositories and really liked it. Then I stumbled across this guide. [http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759) . I thought, wow, I want to try that. I went and downloaded the latest development version. I tried to cd to it, and was informed there was no such directory on my desktop, even though I can see it when I run ls.
So, I try Xarchiver. It creates a file, but I get this error message. 

mv: missing destination file operand after `/home/mairi/Desktop/fluxbox-1.0rc3'

I try anyhow to cd into the file, because when I click on it, it looks like it contains all it needs. I read the mv help, but I guess either I'm not bright enough, or my Linux skills are not yet up to the point where I can make sense of what I need to do. I'll post any terminal output that is needed to be seen. I suppose I can always go back to the more stable version. It was nice, which is why I'd like to try to latest.

Thanks ahead of time for any help.:D

---

### Post by Bachstelze on 2007-04-15
Which Ubuntu are you running ?

---

### Post by Mairi on 2007-04-15
Edgy Eft, on an Optiplex GX 110, with a 1 Ghz Processor and 256 Ram. :)

---

### Post by Bachstelze on 2007-04-15
What does that give you ?

```
ls -l /bin/sh
```

---

### Post by Mairi on 2007-04-15
mairi@mairi-desktop:~/Desktop$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2007-03-29 16:09 /bin/sh -> dash

---

### Post by Bachstelze on 2007-04-15
Do this :

```
sudo dpkg-reconfigure dash
```

if will ask if you want to use Dash, say **no** and then try again. It's because of a stupid idea of Ubuntu's developpers to use Dash instead of Bash by default ; "because it's faster", they say. Not only is it not any faster but it also breaks an awful lot of things...

---

### Post by Mairi on 2007-04-15
Thank you SO much! Worked just fine. It still wouldn't cd into the tarball, even though I copy pasted it. But, Archiver extracted it just fine, without error. Yay you! I am now watching it compile, an entertainment that really begs for popcorn. 

Yeah, that's a somewhat strange decision on the developers part. I have no idea how I would have figured that out on my own. But, that's what so great about these forums. This community is amazing. Thank you once again! I'm going to figure out how to mark this RESOLVED, then go play with my new toy! :D

---

