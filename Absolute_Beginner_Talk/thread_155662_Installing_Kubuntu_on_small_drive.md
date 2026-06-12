---
title: "Installing Kubuntu on small drive"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by klichev on 2006-04-05
Hello!

I'm on my way to installing Kubuntu on a 2 GB drive (it's 10, but the rest is for WinXP). I have already deleted one of the logical drives and freed space.

The questions is that I read somewhere some option for Kubuntu install boot prompt, that instructs it not to cache the installation files on the drive.

(I really cannot find it, really)

Thank you in advance,
K. Lichev

P.P. Wish me luck and good fortune for my data ;-)

---

### Post by catlett on 2006-04-05
What's your question? Are you asking if 2gb is enough space or are you asking if there is a prompt that lets you choose not to cache installation files? As for 2gb it's enough space. If your XP is Fat32 you can put a folder on there for Kubuntu stuff, so you can make use of the space in the XP partition. If your XP is NTFS you can read/access everything on it but you can't write to it(at least not out of the box, I've seen some posts that mention new tools for Ubuntu to deal with NTFS but I don't know them myself). Good luck.

---

### Post by klichev on 2006-04-06
Well, I found it - on boot: prompt one needs to enter:

```
linux archive-copier/copy=false
```

which instructs the installer not to cache installation files on the hard-drive (saves about 300 MB)

---

