---
title: "[SOLVED] Password rejected at login"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by psaulm119 on 2007-12-21
I have installed Ubuntu onto my laptop two times now, and both times, my password has been rejected.  I typed it in twice during the installation, so I know that this isn't just me.  What is going on here? I pressed ctrl-alt-F2 (someone wrote in a thread here to do that) but all that did was make my display twist into many different colors, forcing me to shut down.  

Suggestions?

---

### Post by Nikitas350 on 2007-12-21
I am not sure but you may have selected the wrong language to enter the password.

---

### Post by psaulm119 on 2007-12-21
Selected the wrong language? I know when I set up the installation that I selected English (the default settings, actually), and there was no problem with the keyboard when I typed in my username/computer name.  

OK so if your guess is right, how do I get logged in?

---

### Post by nowshining on 2007-12-21
did u make sure caps lock is NOT on, try typing is out one letter at a time to make def. sure ur typing it out right.

---

### Post by psaulm119 on 2007-12-21
Yes I tried everything--in fact, after several failed attempts, Ubuntu allowed me to see what I was typing (instead of the dots or asterisks that you normally see when you type in a password). I tried it with caps on, caps off,everything--with two separate installations.

---

### Post by Nikitas350 on 2007-12-21
Maybe the password has a problem... (but it is impossible) Did you give the same password the two times you installed the ubuntu? Try a simple password such as 123456 which has no problem with caps and languages...

---

### Post by nowshining on 2007-12-21
hmm so ur saying after some time, it showed the password letters as u were typing, can u try again at this, as this may be a security issue and may need to be reported to launchpad.net for further investigation.

---

### Post by adam.tropics on 2007-12-21
Give this a go...

[http://ubuntuforums.org/showpost.php?p=12862&postcount=1](http://ubuntuforums.org/showpost.php?p=12862&postcount=1)

---

### Post by psaulm119 on 2007-12-21
When I tried the editing the kernel line, I got nowhere. After asking it to boot up by pressing 'b', the computer would just go dead--nothing on the display, but the green power button was still on.

In that same thread you linked to, someone mentioned going to the command line menu. I was able to get to a grub command prompt, at which I typed in password *username*, and then it asked me to type in a password--once. Doing this got me Error 32: Must be authenticated.

Hey everyone, thanks anyways for your help. I'm outta here. Windows, with all the reboots and frustrations that its given me, has never locked me out of my own computer after a fresh install. Thanks again for your time--I do appreciate it.

---

### Post by PmDematagoda on 2007-12-21
Try changing the password, boot into Ubuntu Recovery Mode, then do:-

```
passwd username
```

This should allow you to change the password. After you change the password do:-

```
reboot
```

---

### Post by psaulm119 on 2007-12-21
OK after typing in my "I quit" letter, I found advice to use the recovery console.  I booted into recovery and got Grub (or whatever) to reset my password.  

I didn't realize this, but what was happening was that Ubuntu was forgetting to ask me for my USERNAME--so I would only type in my password.  After resetting it, I was surprised to see it ask for my username too. 

Thanks everyone.

---

### Post by PmDematagoda on 2007-12-21
I did not answer the problem simply because you said "I quit", it was all because I saw your thread at the right time, even if you had not said it I or someone else would still have given an answer, all you have to be is patient, some problems take longer than others do.

---

