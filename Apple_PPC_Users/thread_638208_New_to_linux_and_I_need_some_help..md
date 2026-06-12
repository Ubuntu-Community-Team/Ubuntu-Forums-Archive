---
title: "New to linux and I need some help."
date: 2007-12-11
forum: Apple PPC Users
---

### Post by K1CK1NVV1NG on 2007-12-11
So after extensive research through multiple Linux forums and Google, I have found my self to be stuck. My problem is with Wine, I am attempting to install it, I have tried doing the coded install with terminal, as well as the manual install with the downloaded file. When I try the coded install, I get this message: (The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.)

So after I got this message, I go searching for a solution, when doing so, I find out that I should download the copy of wine and try to install it that way. But when I do it this way, it tells me I have downloaded and attempted to install the wrong version. Now as far as I know there is only two version which are i386 and amd64. So if you do know a solution for me I would appreciate it greatly if you would tell me it.

---

### Post by raja on 2007-12-11
When attempting to install from the terminal, do an update of the repos first like this 
```
sudo aptitude update
sudo aptitude install wine
```
That should work !

---

### Post by DirtDawg on 2007-12-11
Have you tried the official step by step instructions? If not, try them:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by K1CK1NVV1NG on 2007-12-11
I did follow those exact instructions, but I haven't tried what raja posted so I will try that now.

---

### Post by K1CK1NVV1NG on 2007-12-11
So raja I tried what you told me to, and ended up getting a little farther. From what I can tell two things aren't installing if you need more of a description I can copy and paste what it says isn't installing.

---

### Post by frog_pilot on 2007-12-12
> **K1CK1NVV1NG said:**
> My problem is with Wine, I am attempting to install it, 

Wine isnt available for the ppc-architecture.

You can try [qemu]("http://qemulator.createweb.de/") to run windows on a ppc but its abit slow.

---

