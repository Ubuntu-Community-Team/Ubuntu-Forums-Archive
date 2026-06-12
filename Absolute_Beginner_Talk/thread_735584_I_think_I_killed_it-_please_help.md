---
title: "I think I killed it- please help"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by drunkardivan on 2008-03-25
OK, so for sad, work-related reasons, I had to re-install Vista on my laptop. Man, I'd just bought this thing a month ago- Vaio, 2GB RAM, 200GB hard drive, runs Vista well, so Ubuntu's just screaming fast and everything works.

Set it up to dual-boot, since my recovery discs wiped my Ubuntu install. No problem, backed up every necessary document, steeled myself, and just did it. Vista install? No problem (except for the fact that every little adjustment means a restart- I'd forgotten...) Ubuntu install? No problem. 

Until I pulled up my terminal and told it "sudo apt-get update" and then "sudo apt-get upgrade".

It hung up on me, and just sat there for about 15 minutes. So (and this is where I think I killed it), I did a force-quit. Now, any attempt to do much of anything in Ubuntu is met with cynicism and sarcasm from my box. It tells me I need to manually dpkg --configure -a, and when I tell it to do so, it just freezes.

Have I killed my fresh re-install? If so, what are my options?

---

### Post by jan quark on 2008-03-25
> It hung up on me, and just sat there for about 15 minutes. So (and this is where I think I killed it), I did a force-quit. Now, any attempt to do much of anything in Ubuntu is met with cynicism and sarcasm from my box. It tells me I need to manually dpkg --configure -a, and when I tell it to do so, it just freezes.

quiting during an update process is not a joy on ubuntu

and you say it freezes when you run
```
sudo dpkg --configure -a
```
what about running the update process again

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by scragar on 2008-03-25
I'd say run 
```
sudo dpkg --configure -a
```
along with something like top, so you can watch for it dieing(it's a very heavy process, if it takes a while or runs slow I wouldn't worry).

I would recomend adding system monitor to a panel as well, just because you can see CPU usage and HD usage which are the most likly causes of hanging applications.

---

### Post by drunkardivan on 2008-03-25
OK, I tried to "sudo dpkg --configure -a"

But Ubuntu doesn't recognize my wireless setup. Or my volume, for that matter.

This is a clean install, I have nothing invested in it. I have all my data backed up. Would it be simpler for me to wipe this install and do it again? And, if so, um... how do I do that?

---

### Post by jan quark on 2008-03-25
to wipe your linux partitions you can use gparted running through the live cd session
> 
OK, I tried to "sudo dpkg --configure -a"

But Ubuntu doesn't recognize my wireless setup. Or my volume, for that matter.

but is the problem solved now do you still get this first error message or can you update and install new applications without an issues?

---

### Post by drunkardivan on 2008-03-25
It didn't let me connect, so there's basically nothing I can do. I don't have the ability to connect to the router.

---

### Post by drunkardivan on 2008-03-26
Well, thanks, everyone, for the help. I hard-wired to the router this morning and tried your advice. Unfortunately, I didn't have much success.

On the bright side, I screwed this up early enough in the game that a fresh install wasn't too bitter of a pill to swallow.

Thanks all for your help.

---

