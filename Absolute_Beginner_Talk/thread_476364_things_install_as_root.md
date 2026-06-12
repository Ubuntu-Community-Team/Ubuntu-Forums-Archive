---
title: "things install as root"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by kyfho23 on 2007-06-17
Hello!
Kubuntu 7.04 on an Intel Core Duo box...

I'm trying to track down problems with Ktorrent, step by step. First step is to find out why KTorrent, and other problems, re-install as a program that can only be run as root, rather than as a regular user. Running a torrent application as root strikes me as a bit....insecure.

Back to the main point of this post: I gave up on my previous KTorrent installation, purged it, and re-installed it. During the purging, the kubuntu-desktop meta-program was uninstall. I reinstalled KTorrent, then the kubuntu-desktop meta-package (in that order). Now, KTorrent will only run with root privileges (kdesu ktorrent).

I've had this problem with other programs occasionally-usually, I use krusader to reset the ownership of the files. But I'm curious about what I'm doing wrong, and of course, how to fix it, both the existing KTorrent installation and any future programs that I install.

After that (or if you have any ideas on a further subject), I'll deal with why KTorrent, aMule, Frostwire, Azeureus, and every other p2p program can't connect even after I've opened up the ports in both Guarddog and my DSL modem....

Thanks in advance!

---

### Post by weel on 2007-06-17
> Now, KTorrent will only run with root privileges (kdesu ktorrent).


What exactly happens when you run ktorrent as a normal user? Do you get an error message? Which error message?

(In general, BTW, you will probably get faster and better answers to your questions if you specify exactly what you did, what you expected to happen, and what did happen. Even if the answers to one of those questions seems perfectly obvious, it may not be to whoever is trying to answer them, and the first reaction may often be to just leave the question to be answered by others rather than soliciting the missing information. I'm not saying this to be nasty, but just to be helpful. Trust me. Pretty please.)

---

### Post by kyfho23 on 2007-06-17
I know...i realized that after my first post.

Basically what happens is a quick flash of the GUI, then nothing. I DON'T get the " you must have root privileges to run this program" message.

& no, you're not being nasty. i omitted a crucial piece of information. my bad. i'm actually not that new here...i've posted very little since i can usually find someone else who's had the same problem & gotten it resolved here on the forums. search is a wonderful thing. :p

i HAVE cured similar problems before by changing ownership, as i originally noted. 

RESOLVED!!! ktorrent just opened normally from the menu.

Thanks for your time! i'm not sure what happened. this is another strange behavior i've noticed: sometimes, you have to open a program the second time before it will run. but this is tolerable, and i'm not going to waste time on it.

as far as ktorrent not being able to connect to the net, i'll start another thread later after i punch the holes i need thru my modem & the ip tables, and see if the problem still exists.

again, thanks for your time. the generosity of the linux community in general, and the ubuntu community in particular continue to amaze me.

chris

---

