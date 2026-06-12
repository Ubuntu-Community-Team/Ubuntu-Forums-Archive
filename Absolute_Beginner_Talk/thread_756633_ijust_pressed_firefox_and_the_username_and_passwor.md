---
title: "ijust pressed firefox and the username and password screen popped up :/"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by ~L~ on 2008-04-16
can u help me? I just pressed firefox again on the tool bar and it prompted me to put username and pass again

---

### Post by cchester on 2008-04-16
Does Firefox run after you put in your username and password? Could be a permissions issue but it shouldn't ask for a username though. Did you change something?

---

### Post by Duckyspetrie on 2008-04-16
Your IP address could be set to your router or something of that ilk. What is your homepage set to?

---

### Post by ~L~ on 2008-04-16
it happens for reason . I havent changed anything, It has yet to happen again, but it'll probably happen again. When that happens, I put passwrod/ username and then it opens a new desktop and when I press FF or something that I had on use before that happened, it tells me its already open so I have to reboot. And no it's not on the other desktop  :)

---

### Post by jelkimantis on 2008-04-16
Things that might be useful to know for troubleshooting this problem.

It might be interesting to know if indeed another copy of FF is running.  We could learn this by:

```

ps -elf |grep firefox

```

Something else that might be interesting is if your FF is crashing related to a flash problem right before that.  When this happens it seems that FF does not completely (or correctly) shutdown and might be causing some user-level conflicts.

jsl

---

### Post by ~L~ on 2008-04-16
> **jelkimantis said:**
> Things that might be useful to know for troubleshooting this problem.

It might be interesting to know if indeed another copy of FF is running.  We could learn this by:

```

ps -elf |grep firefox

```

Something else that might be interesting is if your FF is crashing related to a flash problem right before that.  When this happens it seems that FF does not completely (or correctly) shutdown and might be causing some user-level conflicts.

jsl

when that happens again i'll post here, thanks

---

### Post by ~L~ on 2008-04-16
It happened again but this time I just pressed the minimize button.
Why does ubuntu crash : '<
Can I fix it..tell me what info might be useful for you and I will provide it.
EDIT:
First of all, is it a problem that I downloaded the CD of ubuntu (how do i see what type of linux I have anyway? I think I have ubuntu)
and I installed the Live CD first, then I deleted the windows partitions and fully installed the linux software ? Is this a problem, and could this be the reason behind my random crashes?

---

### Post by cchester on 2008-04-16
Did you grab Ubuntu 7.10 or Ubuntu 8.04? You can try and uninstall Firefox if you want or if you installed flash then try uninstalling it. Ubuntu is very stable. What have you did install after installing the fresh version of Ubuntu on your system. You might have to do some back tracking to figure out what is wrong by installing things that you installed that way if it stops happening once a program has been uninstalled then that would be the culprit. If this is a fresh install and nothing else was installed and you are having issues and say you did the updates only after installing maybe something got messed up when installed. If this is a fresh install and you don't have anything of dire importance on your system that you can't live without then just do a new fresh install and that could fix your issue too.

To answer your question though it doesn't matter cd vs dvd version of Ubuntu one is not more stable than the other. The only thing that will matter is if it is the stable 7.10 or the beta 8.04.

Hope this helps.

---

