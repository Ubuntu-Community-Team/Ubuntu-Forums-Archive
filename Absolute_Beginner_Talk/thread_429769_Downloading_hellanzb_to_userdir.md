---
title: "Downloading hellanzb to userdir"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Norway on 2007-05-01
Hi!

I'm trying to download a hellanzb to my userdir.  See this link [http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb)
Ubuntu is a new thing for me so I have problems with downloading hellanzb to the userdir. I have downloaded it to my desktop, but I can't move it to the userdir because I don't have permission to do it. 
Are there different or better ways do it? If there are, how do you do it?

Greetings from Norway:)

---

### Post by taurus on 2007-05-01
Applications -> Accessories -> Terminal
```
**sudo** cp filename destination
```
Or
```
gksudo nautilus
```
and drag 'n drop it to where you want it to be.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by qamelian on 2007-05-01
> **Norway said:**
> Hi!

I'm trying to download a hellanzb to my userdir.  See this link [http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb)
Ubuntu is a new thing for me so I have problems with downloading hellanzb to the userdir. I have downloaded it to my desktop, but I can't move it to the userdir because I don't have permission to do it. 
Are there different or better ways do it? If there are, how do you do it?

Greetings from Norway:)
Never mind. Taurus types way faster than me!

---

### Post by Norway on 2007-05-01
Thank you!
Worked fine:)

---

