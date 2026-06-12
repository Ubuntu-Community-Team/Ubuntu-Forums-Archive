---
title: "Cant start after update"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by slkuhn on 2007-04-13
Hi everyone, 
I just installed some updates last night and I was told I needed to restart. When I restarted Ubuntu (Feisty), the progress bar wouldnt begin to go across the screen. ?? I think I screwed something up bigtime?? 
I have created a small partition, with edgy on it, and I have mounted my Feisty partition.
Will there be a log file hidden somewhere on my Feisty filesystem that might tell me whats wrong? I realize that I dont have specifics and that it could be about 1.2 million different thingsthat went wrong. If anyone could give me some guidance I would much appreciate it.

-slk

---

### Post by mesh_ok on 2007-04-13
the same thing! 

The new kernel is not the only trouble - when you try to load previous kernel, you find that X does not start - new nvidia drivers have newer interface than X :) 
I managed to startx after dpkg-reconfigure :)

---

### Post by slkuhn on 2007-04-13
I really hate doing this but I am desperate....bump.

can anyone help.

Is there a log file anywhere that would tell me what is going wrong on Startup?

btw: I tried logging into a different kernel (i think its called that, it was an 'older' one than I normally boot into) and it couldnt load X. 
i ran 
```

sudo dpkg-reconfigure xserver-xorg

```

but it still failed in that particular kernel

---

### Post by slkuhn on 2007-04-13
lol Wow are you my long lost twin or something lol !
same problem and all

---

### Post by mesh_ok on 2007-04-13
let's go to other guys :)
[http://ubuntuforums.org/showthread.php?t=408226](http://ubuntuforums.org/showthread.php?t=408226)

---

### Post by megavolt1 on 2007-04-14
I have exactly the same issue. Is there a way to uninstall the updates?

architecture

Mother Board - GA-M61P-S3
Processor - AM2 64
OS - Edgy Eft
Crashed Kernel - 2.6.20-15-generic
I can still boot on 2.6.20-14-generic, but sound does not work.
Chipsets - GeForce 6100
                nForce 430

Megavolt1

---

### Post by braindead_primate on 2007-04-15
This is slightly off topic, but related.

I seem to be too much of a noob to tell if I am using Feisty, Edgy, Pissy, or Moany.  I do know that I just updated to kernel 2.6.15-28-386, and immediately after was totally unable to log in.  However, I solved the problem.

Short Version:
I booted into recovery mode for the latest kernel and removed the bittorrent startup script from /etc/inet.d.  Successful login followed,

Long Version (how did I arrive at bittorrent?):
Does it really matter?  Probably not but I'm feeling wordy.

I knew I hadn't forgotten my password, but I acted as though I had, and found out how to mount my drive from the Live CD and edit /etc/shadow to clear the password (wish I could remember the link...)  With an empty password in my user account, I tried to login again, but it was no good.

In my many travels searching for an answer, I came accross a thread that mentioned bittorrent.  I didn't read the thread too closely because the author in question was whining incessently about the inadequacies of Ubuntu.  Instead, I filed that keyword away, avid CRPGer that I am.

I FINALLY read the freaking screen during the bootup process and discovered that hitting ESC within a 2 second window would get me to recovery mode.  It's been a long night, and I was constantly trying to hit 'e' during bootup because of some other forum I read.  Finally in a root console, I was able to attempt my bittorrent experiment.

- B

---

