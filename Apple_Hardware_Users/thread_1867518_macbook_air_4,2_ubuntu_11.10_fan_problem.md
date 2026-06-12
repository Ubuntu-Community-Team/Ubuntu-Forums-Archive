---
title: "macbook air 4,2 ubuntu 11.10 fan problem"
date: 2011-10-23
forum: Apple Hardware Users
---

### Post by charlies8282 on 2011-10-23
Good morning

I have installed ubuntu 11.10 (64) on a new macbook air, and run the post-install-script successfully as suggested in the wiki.

Now (and not from the "day one", but about two/three days later the installation) my macbook air's fan never stops. From the login moment (just from the "enter" command after digitizing my password), until the shutdown. 
No updates pending in ubuntu (with the exclusion of and mactel ppa that seems to be always offline).

I have installed gnome-shell, but even in unity there is no difference.

Thank-you,

CS

---

### Post by Ms. Daisy on 2011-10-24
While the fan is constantly running, open a terminal and type in "top".  This will give you a list of the running programs and how much CPU each is using. Post the results here.

---

### Post by charlies8282 on 2011-10-25
Thank-you!

the task using more cpu is xorg (but not more than 7%). :(

---

### Post by Ms. Daisy on 2011-10-25
I won't pretend to be an expert.  I had a problem where udisks used lots of CPU.  But that doesn't appear to be your problem.  Have you checked the specs of your computer?  You said it's a new macbook air, so it should far exceed the minimum requirements. But I suppose it's worth a look.

I believe I've seen several posts and solutions throughout the forum regarding fans running too much on laptops, not sure if it was in the apple forum or generally on all PCs. I'll see if I can find them again.  

EDIT: I found one of the threads that said "if you use Adobe's flash plugin, it has a long history of resource  over-usage on Linux, although I'm not sure of its current status."  May be worth looking into, but I'm afraid I don't know anything about it myself.

In the other threads I found, fans constantly running were related to laptops overheating.  Are you getting excessive heat as well? 

This thread could very well have the solution, may be worth a look: [http://ubuntuforums.org/showthread.php?t=1467062](http://ubuntuforums.org/showthread.php?t=1467062)

---

### Post by DrMeers on 2011-12-25
I found that I needed to exclude sensors 14 / 15 / 16 instead of 13 / 14 /15 in /etc/macfanctl.conf

Check the output of the `sensors` command to confirm. I think it is one-based indexing.

---

### Post by molineiro on 2012-05-01
Hi,

I have the same problem. As soon as I log in to Ubuntu on my macbook air the fan starts running and it doesnt stop. any ideas on how to solve this? 

thanks

---

