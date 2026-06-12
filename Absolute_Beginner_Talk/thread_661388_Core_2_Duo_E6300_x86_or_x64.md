---
title: "Core 2 Duo E6300: x86 or x64??"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by asleekaizoku on 2008-01-07
When I tried out x64, i noticed that the loading screen (the orange loading screen with UBUNTU logo) is gone. 
Is this normal?
So if I have a Intel Core 2 Duo Processor I need to download the AMD64 version to install the x64 architecture?

Sorry I am really new on this stuff.

---

### Post by Xavieran on 2008-01-07
I installed ubuntu on my Core 2 Duo with x86...
That should work for you...

---

### Post by asleekaizoku on 2008-01-07
> **Xavieran said:**
> I installed ubuntu on my Core 2 Duo with x86...
That should work for you...

Yeah, x86 works just fine but everyone keeps talking that x64 will give you better speeds than x86 so, im just wondering.

---

### Post by Xavieran on 2008-01-07
x86 is optimised for Intel's 32bit processors whereas x64 is optimised for AMD's 64bit processors...that is probably why they said it would give you better performance ,*if* you were runnning an AMD chip...:)

---

### Post by asleekaizoku on 2008-01-07
> **Xavieran said:**
> x86 is optimised for Intel's 32bit processors whereas x64 is optimised for AMD's 64bit processors...that is probably why they said it would give you better performance ,*if* you were runnning an AMD chip...:)

So, to sum it all up, is there something to optimize Intel's 64bit processors (such as Core 2 Duos)?

---

### Post by p_quarles on 2008-01-07
> **Xavieran said:**
> x86 is optimised for Intel's 32bit processors whereas x64 is optimised for AMD's 64bit processors...that is probably why they said it would give you better performance ,*if* you were runnning an AMD chip...:)
Err, no. The 64-bit version of Ubuntu works with any Intel or AMD 64-bit processor. It's only named "AMD" because they developed the principles behind the architecture.

The benefits of 64-bit are simple:
1) You're not wasting CPU power
2) For certain CPU-heavy tasks (encoding, compiling, ripping) you'll see a noticeable gain in performance.
3) You're helping to encourage the development of 64-bit programs.

The only disadvantage is that it will take a few extra steps to correctly install 32-bit-only commercial programs. Currently, most of the popular apps (Opera, Flash, Skype, Java) are very easy to install.

---

### Post by asleekaizoku on 2008-01-07
But when I install the x64 architecture on my PC, it doesn't have any loading signs.
When I finish installing the OS it ejects the CD and leaves a blank screen. (Supposed to tell me to take off the disk and press ENTER on x86).
Sometimes when I shut down, my computer keeps beeping for some odd reason.

---

### Post by p_quarles on 2008-01-07
Did you check the integrity of the disk you used to install it?

---

### Post by asleekaizoku on 2008-01-07
> **p_quarles said:**
> Did you check the integrity of the disk you used to install it?

How do u do that?

---

### Post by p_quarles on 2008-01-07
Boot the disk, and select the option to "check integrity of the CD."

---

### Post by asleekaizoku on 2008-01-07
> **p_quarles said:**
> Boot the disk, and select the option to "check integrity of the CD."

Alright, ill try that right now.
If all else fails, im going back to x86 :KS

---

### Post by Xavieran on 2008-01-07
This should help:[http://wiki.sabayonlinux.org/index.php?title=Tips#Checking_your_MD5SUM]("http://wiki.sabayonlinux.org/index.php?title=Tips#Checking_your_MD5SUM")

:)

---

