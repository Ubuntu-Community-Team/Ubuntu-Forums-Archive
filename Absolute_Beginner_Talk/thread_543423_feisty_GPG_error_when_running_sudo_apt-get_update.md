---
title: "feisty GPG error when running sudo apt-get update"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by w1z4rd on 2007-09-05
I get this error today when running the sudo apt-get update command:

```
Hit http://za.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 14.4kB in 11s (1280B/s)
Reading package lists... Done
W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures were invalid: BADSIG 2D6CFB44DD800CD9 Treviño (3v1n0) <trevi55@gmail.com>
W: You may want to run apt-get update to correct these problems
r0x@b0x:~$   
```

I have also run the command:

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

And I get the same error :(

I know its for Trevino`s rep.. anyone got any idea whats up?

---

### Post by forestpixie on 2007-09-05
I got the same - I'm gonna try again later, maybe it's down

---

