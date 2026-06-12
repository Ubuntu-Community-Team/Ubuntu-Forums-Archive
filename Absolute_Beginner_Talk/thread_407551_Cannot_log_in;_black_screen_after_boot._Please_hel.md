---
title: "Cannot log in; black screen after boot. Please help."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by amosharper on 2007-04-12
Hi,

I've been using the Feisty Fawn beta, and I changed a logon setting (stupidly) without knowing what it was. Now, when I try to boot Ubuntu (any kernel, even in recovery mode - I'm dual-booting with Windows XP) it shows the loading bar, and when that's finished, it hangs on a black screen with the loading cursor.

Can I change this setting back from Windows (I'm using a program called Explore2FS which enables me to view change the Linux files using Windows) by editing a file somewhere or other? If you showed me a screenshot of the logon settings, I could show you which option it was. If not, can I recover the system, or will I need to format the sector?

Thanks in advance,

- Amos

---

### Post by FuriousLettuce on 2007-04-12
When the screen hangs, if you press Ctrl+Alt+F1 can you login to the terminal? In which case, can you find / tell us which file you edited so that we could help you edit it.

---

### Post by amosharper on 2007-04-12
> **FuriousLettuce said:**
> When the screen hangs, if you press Ctrl+Alt+F1 can you login to the terminal? In which case, can you find / tell us which file you edited so that we could help you edit it.

Thanks for replying, FuriousLettuce.

Yes, I can reach and log in with the terminal. However, it was in a login options dialog a bit like [http://people.ubuntulinux.org/~mako/docteam/images/loginscreenstartup.png](http://people.ubuntulinux.org/~mako/docteam/images/loginscreenstartup.png), not by editing a file, that I made the change. That screenshot's from Warthog, I think, and that particular dialog has changed a lot. The option I ticked (sorry to be so vague) was on a tab not featured there.

Thanks.

---

### Post by jputman01 on 2007-04-12
you can use a live cd to get in to ubuntu and mount your linux partition, from there you can access all the files (not much different from just logging into the terminal though) and use gedit or something to edit the files. I don't think you are going to be able to get to the graphical dialog box though, you will probably have to edit the file that feeds the dialog box. I could be wrong though

---

### Post by jvc26 on 2007-04-12
This the one you changed?
Il

---

### Post by FuriousLettuce on 2007-04-12
If you can, try to identify the tab / option you changed so we can help you change it back - it's much better to learn to fix stuff rather than having to reinstall every time you make a mistake :)

---

### Post by amosharper on 2007-04-12
Thanks for your responses.

> **Illuvator said:**
> This the one you changed?
Il

No, it wasn't that tab. I'll try what Jputman01 said... meanwhile, could someone be so kind as to post pictures of what the other tabs are? Thanks very much.

- Amos

EDIT: Hang on, it's easier for me to do what Jputman says through Windows as I mentioned in my first post, surely? And I'd still need to know what file/s the dialog was changing.

---

### Post by FuriousLettuce on 2007-04-12
IF you use the live cd, you can identify the tab / setting, then tell us / search to find the config file, which you can then edit however you please.

---

### Post by amosharper on 2007-04-12
Will try.

---

### Post by amosharper on 2007-04-12
I booted from the Live CD and ran a Disc Integrity check. I left it with the progress bar slowly going up, and when I came back 20 minutes later, it was on a console screen with repeated messages like the following coming up:
[PHP][1718027.920000] Buffer I/O error on device hdd, logical block 173297[/PHP]
The same happened after trying to Run/Install.

What does this suggest? I can still access the Linux partition from Windows, so there's no big disk error.

Thanks.

---

### Post by amosharper on 2007-04-13
Is it recoverable, do you think, or should I format?

---

