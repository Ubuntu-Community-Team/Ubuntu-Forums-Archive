---
title: "MPlayer problem.. and How to get ntfs HDD to write?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Twisted1616 on 2006-05-19
Hi, folks
My problem is that when I play a movie in MPlayer it works alright.. but when I want to make it double size or fullscreen the window grows bigger (or fills the screen) but the picture size stays the same and the colour  blue  fills the rest of the window (or screen).. Why? And how can I fix that?

And another thing... How can I write stuff to an ntfs formatted HDD?  I read I needed to install something...  Can I get that through the Synaptic Package Manager? And if so, what is it called?

I'm using Ubuntu  and I just got it couple days ago and have never used Linux before.

Thanks in advance.

---

### Post by joshrobinson on 2006-05-19
[QUOTE=Twisted1616]Hi, folks
My problem is that when I play a movie in MPlayer it works alright.. but when I want to make it double size or fullscreen the window grows bigger (or fills the screen) but the picture size stays the same and the colour  blue  fills the rest of the window (or screen).. Why? And how can I fix that?

And another thing... How can I write stuff to an ntfs formatted HDD?  I read I needed to install something...  Can I get that through the Synaptic Package Manager? And if so, what is it called?

I'm using Ubuntu  and I just got it couple days ago and have never used Linux before.

Thanks in advance.[/QUOTE]

for the mplayer problem i would just try to remove it and reinstall it and see what happens. what video card are you using?
you can always try to install it from source code

as for ntfs write you can use captive
[http://www.jankratochvil.net/project/captive/]("http://www.jankratochvil.net/project/captive/")

but ntfs write isnt the best thing in the world to use, it can cause lost data, and can mess up the ntfs parition (so ive heard)
you are better off backing up the data on it and converting it to fat32.. as long as you dont have any files bigger then 2+gb becuase fat32 has a filesize limit

---

### Post by cilynx on 2006-05-19
With mplayer, put "vo=xv" into your ~/.mplayer/config

Writing to NTFS in Linux is --not-- mature.  I don't want to give a quick answer because you're likely to damage your NTFS partition.  Throw it at Google and read for a while.  It is possible, just not safe/easy.

---

### Post by Ptero-4 on 2006-05-19
You need the captiva driver (or something like that) to write to a ntfs drive. But it's quite experimental and will likelly corrupt dataa in your ntfs drive.

---

### Post by joshrobinson on 2006-05-19
[QUOTE=cilynx]With mplayer, put "vo=xv" into your ~/.mplayer/config
[/QUOTE]

couldnt you also launch it with gmplayer -vo xv  ? that should work shouldnt it?

---

### Post by Klaidas on 2006-05-19
Here's some information I've found on the wiki: [https://wiki.ubuntu.com/NTFSReadWrite](https://wiki.ubuntu.com/NTFSReadWrite)

However, it is experimental ant NOT recommended

---

### Post by cilynx on 2006-05-19
[QUOTE=joshrobinson]couldnt you also launch it with gmplayer -vo xv  ? that should work shouldnt it?[/QUOTE]

Yeah, that should work too.  I just prefer the config file as I always forget my command line options.

---

### Post by tonyr on 2006-05-19
Here are a couple of links for further exploration of the NTFS issue.
[URL="http://www.ubuntuforums.org/showthread.php?t=142481"]
http://www.ubuntuforums.org/showthread.php?t=142481[/URL]
[http://www.linux-ntfs.org/]("http://www.linux-ntfs.org/")

Ditto on the "experimental warnings.  If you're gonna do it anyway, be prepared for
unhappy surprises.

---

### Post by Twisted1616 on 2006-05-19
Thanks a mill for your quick replies.
I tried reinstalling MPlayer but same prob.  Anyway I found another player I reconised.. VLC.. He works perfectly so I'll just be using VLC from now on.

As for the ntfs writing.. if it is so risky I think I'll just skip it.

Again, thanks so very much. :)

---

### Post by joshrobinson on 2006-05-19
[QUOTE=Twisted1616]Thanks a mill for your quick replies.
I tried reinstalling MPlayer but same prob.  Anyway I found another player I reconised.. VLC.. He works perfectly so I'll just be using VLC from now on.

As for the ntfs writing.. if it is so risky I think I'll just skip it.

Again, thanks so very much. :)[/QUOTE]

vlc is a decent program on linux (better in windows codec wise) you will probibly have better luck with codec's in mplayer if it works fine
try typing this in terminal and see if it plays a video fine in double or full screen

```
gmplayer -vo xv
```

if it does you can edit the config file as cilynx said:

[QUOTE=cilynx]With mplayer, put "vo=xv" into your ~/.mplayer/config[/quote]

---

