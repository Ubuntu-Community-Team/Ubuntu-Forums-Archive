---
title: "getting libdvdcss from the closed sticky"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by pcrussell50 on 2007-08-19
when i follow all the steps in the feisty multimedia dvd thread, the one that's closed and was posted by the moderator, i get this on the final terminal screen:

:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

any ideas?

regards,
peter

---

### Post by Raptor45 on 2007-08-19
Doesn't look like you followed the steps correctly. Did you update?

I'd run through and try again.

---

### Post by mikewhatever on 2007-08-19
The packages you want are in Medibuntu repository. You must either add it to the sources list or manually download them from there.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Oh, and a link to the guide you followed is always more then helpful.

---

### Post by Raptor45 on 2007-08-19
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624) is what I'm guessing he used.

That should set up the medibuntu repo just fine, so I'm guessing some step wasn't followed quite right.

---

### Post by pcrussell50 on 2007-08-19
> **Raptor45 said:**
> [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624) is what I'm guessing he used.

That should set up the medibuntu repo just fine, so I'm guessing some step wasn't followed quite right.

yes, that link was the one i followed.  i'm glad somebody got it when i described it as the closed sticky that was posted by the moderator.

ok, i did it twice, but back to the drawing board, i suppose.

-peter

---

### Post by Raptor45 on 2007-08-19
```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 w32codec
```

Run those three lines.

---

### Post by pcrussell50 on 2007-08-19
ok gang, got it working.  i pasted in the terminal command from:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then did the final two steps from the mod's sticky:

sudo apt-get update

sudo apt-get install libdvdcss2 w32codecs

now it all works, thanks a bunch all.

-peter

---

