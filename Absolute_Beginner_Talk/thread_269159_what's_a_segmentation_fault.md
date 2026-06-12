---
title: "what's a segmentation fault?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by wog on 2006-10-01
I have a segmentation fault in firefox (I'm on my XP laptop). What is it and how do I solve this?

I'd considered uninstalling and then reinstalling firefox, but then I'll lose all my bookmarks, right?

---

### Post by meng on 2006-10-01
[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)
(not helpful? I didn't find it very helpful either, so that makes two of us!)
Actually, uninstalling/reinstalling firefox shouldn't wipe your bookmarks, as they should be saved in a hidden folder in your home directory, which won't be deleted with an uninstall. However, if you want to be really safe, just export your bookmarks to a HTML file (choose File > Export ... from Bookmark Manager).

---

### Post by wog on 2006-10-01
Uninstalling/Reinstalling firefox didn't work. I still get a seg fault error.

Trying complete removal and restart next.

If this doesn't work, my only other option is Konqueror.

---

### Post by wog on 2006-10-01
Nope. Firefox is dead. It won't run at all. Segmentation fault.

I don't know what it's attempting to access, but whatever it is, firefox accesses it just to get past the little "Starting Firefox" stage. ](*,)

---

### Post by grayhorse on 2006-10-01
These are the symptoms I'm getting with evolution!! Is there a pattern emerging?

Ross

---

### Post by sbergman27 on 2006-10-01
This is likely a problem with your FF profile.

In a terminal:

```
firefox -ProfileManager
```

Then create a new profile and use it.  Yes, it's a pain.

So it might be a good time to just:

```

apt-get install epiphany-browser epiphany-extensions

```

which is the default Gnome browser and its default extension set, and which doesn't have these problems.  And it *might* allow you to import the bookmarks from your FF profile.

Why people put up with the ongoing FF lockfile and profile problems is beyond me...

---

### Post by wog on 2006-10-01
The "-ProfileManager" switch doesn't work in my case. I just get the same "Segmentation fault" error.

Thank you for the different web browser option, though. I was really, really hoping I wasn't going to have to go to either Opera or (shudder) Konqueror. :)

---

### Post by wog on 2006-10-01
Hmmm.

Epiphany crashes, too. At least it gives me a message box before it crashes out, but no options help, whether loading the profile or just restarting.

Opera also doesn't work. Segmentation fault, same as Firefox.

Konqueror doesn't work either. Segmentation fault.

So why do Lynx and Elinks work, but no graphical browser will?

Anyone out there think my copy of Ubuntu is hosed and I need to reinstall, or can anyone think of a fix?

---

### Post by Palmyra on 2008-05-10
I'd love to know what a segmentation fault is because I've been getting it as an error for quite a while from all sorts of applications.

---

### Post by bobnutfield on 2008-05-10
Hello, not being a programmer, I cannot tell what is causing your seg faults, but I can tell you that segmentation faults occur when an application attempts to access a portion (address) of your memory that is either occupied already by some other app or it is just simply not supposed to be accessing.  Seg faults are roughly equivilent to the Windows BSOD.

The kernel is involved here, and if you are getting seg faults in a number of applications, namely all web browsers,  I am almost certain it will be network related.  Seg faults in network software is fairly common, but I unfortunately cannot help you diagnose it with regard to your web browesers.  This is a prettly low-level problem and may necessitate a re-install.  Hopefully, a programmer with adequate experience will see this post.

Regards

Bob

---

### Post by Lux Perpetua on 2008-05-10
> **bobnutfield said:**
> Seg faults are roughly equivilent to the Windows BSOD.Actually, the Windows equivalent of a segmentation fault would probably be an "illegal operation" or something like that. A BSOD ("blue screen of death") is a systemwide crash. A segmentation fault wouldn't crash your computer (unless it were in a critical program), but the program that generated it would crash.

---

### Post by bobnutfield on 2008-05-11
> **Lux Perpetua said:**
> Actually, the Windows equivalent of a segmentation fault would probably be an "illegal operation" or something like that. A BSOD ("blue screen of death") is a systemwide crash. A segmentation fault wouldn't crash your computer (unless it were in a critical program), but the program that generated it would crash.

Thanks for correcting that.  I had been informed wrongly.  But, it would be nice to be able to help these posters because seg faults are an irritating problem (experienced them myself) but it would be beyond my knowledge.  

Bob

---

### Post by Enfenion on 2008-05-11
A seg. fault is that a program tries to access a part of the RAM that it does not have access to (f.ex. the part where the operative system is) to secure that no vital part of the system is corrupted when a badly written program or similar hangs (or destroys) the system. It also protects against some viruses.
This is a very wide problem, and could have very many different sources (sw: bad driver, missing files, wrongly configured files, error in program, +++ hw: corrupt RAM, HDD, +++)

To your (or similar) problems:
Do you experience the problem with any other software than the graphical browsers?
Do you experience the problem if you boot from a live disc?

---

### Post by beanco on 2008-05-18
> **Enfenion said:**
> A seg. fault is that a program tries to access a part of the RAM that it does not have access to (f.ex. the part where the operative system is) to secure that no vital part of the system is corrupted when a badly written program or similar hangs (or destroys) the system. It also protects against some viruses.
This is a very wide problem, and could have very many different sources (sw: bad driver, missing files, wrongly configured files, error in program, +++ hw: corrupt RAM, HDD, +++)

To your (or similar) problems:
Do you experience the problem with any other software than the graphical browsers?
Do you experience the problem if you boot from a live disc?

I am having this segmentation fault problem in Evolution, FF and Epiphany.

I do not have a live CD here to try...

any suggestions

robi

---

