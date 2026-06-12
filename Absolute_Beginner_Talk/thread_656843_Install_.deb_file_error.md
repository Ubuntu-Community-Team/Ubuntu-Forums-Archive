---
title: "Install .deb file error"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Skivache on 2008-01-03
I just downloaded AVG [from here]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl")
(i have a windows-Linux shared file partition) and ran ```
sudo dpkg --install avg75fld-r49-a1130.i386.deb
```
I then got ```

User@DL:~$ sudo dpkg --install avg75fld-r49-a1130.i386.deb
dpkg: error processing avg75fld-r49-a1130.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
avg75fld-r49-a1130.i386.deb
```
the file is on my desktop, i don't think this is in the repos so i can't get it with Synaptic.

---

### Post by Seti on 2008-01-03
mind if I ask you why you need to install an antivirus program?

otherwise it should be
 ```
dpkg -i --install 'name of the install file'.deb
```

---

### Post by mikewhatever on 2008-01-03
You need to either move the file to your home directory and then go on, or change to the Desktop directory with <cd ~/Desktop>. A simple double clicking would also be ok.

---

### Post by ~LoKe on 2008-01-03
If you absolutely want it...
```
cd ~/ && wget http://free.grisoft.com/filedir/inst/avg75fld-r49-a1130.i386.deb && sudo dpkg -i avg*.deb
```
Or, broken into multiple lines for readability...
```
cd ~/
wget http://free.grisoft.com/filedir/inst/avg75fld-r49-a1130.i386.deb
sudo dpkg -i avg*.deb
```

---

### Post by Skivache on 2008-01-03
I want the anti virus because i have a partition where i share files between Ubuntu and Vista.

---

### Post by Seti on 2008-01-03
"I want the anti virus because i have a partition where i share files between Ubuntu and Vista. "

Sounds like a good way to also scan that c:\ partition that might be pooched. If that's the case, you can even enable write to NTFS and remove the offending files --probably the only practical application of that-- otherwise its really not needed. Just install AVG on Windows and do your scans from there.

---

### Post by Skivache on 2008-01-03
Again you guys out click me.
Thank you ~Loke, that worked perfectly.
Mikewhatever, when i double click the file it opens it in archive manager.....
How can i open it in something else, just so i know?

---

### Post by Skivache on 2008-01-03
> **Seti said:**
> "I want the anti virus because i have a partition where i share files between Ubuntu and Vista. "

Sounds like a good way to also scan that c:\ partition that might be pooched. If that's the case, you can even enable write to NTFS and remove the offending files --probably the only practical application of that-- otherwise its really not needed. Just install AVG on Windows and do your scans from there.

I already have AVG on vista but switching to windows to do a security scan doesn't make much sense.

---

### Post by ~LoKe on 2008-01-03
> **Skivache said:**
> Again you guys out click me.
Thank you ~Loke, that worked perfectly.
Mikewhatever, when i double click the file it opens it in archive manager.....
How can i open it in something else, just so i know?

No problem.  The .deb should be opening in gdebi, the debian file installer.  Do you have it installed? (should be by default...)

---

### Post by Skivache on 2008-01-03
I may not have it installed as I am using DreamLinux (Debian based, KDE) right now not Ubuntu (i have both).
I am presuming i can get that in the repos?

---

### Post by ~LoKe on 2008-01-03
> **Skivache said:**
> I may not have it installed as I am using DreamLinux (Debian based, KDE) right now not Ubuntu (i have both).
I am presuming i can get that in the repos?

You could sure try:
```
sudo apt-get install gdebi
```

---

### Post by Skivache on 2008-01-03
Yup, the repos had it.
Thanks guys!

---

### Post by Skivache on 2008-01-03
New question for you,
how do you update AVG, because its a free version, it doesn't download from the program.

---

### Post by ~LoKe on 2008-01-03
> **Skivache said:**
> New question for you,
how do you update AVG, because its a free version, it doesn't download from the program.

The latest packages should have the latest updates, other than that I can't really suggest something never having used AVG in Ubuntu.

---

### Post by Skivache on 2008-01-03
I found the update section on their website.
Thanks again ~LoKe, i think i am done with the questions now.

---

### Post by ~LoKe on 2008-01-03
> **Skivache said:**
> I found the update section on their website.
Thanks again ~LoKe, i think i am done with the questions now.

Bah, this one was all you. ;)

And just so you're aware: we like questions! ^^;

---

### Post by Skivache on 2008-01-03
Great I'll keep asking em' :)

---

