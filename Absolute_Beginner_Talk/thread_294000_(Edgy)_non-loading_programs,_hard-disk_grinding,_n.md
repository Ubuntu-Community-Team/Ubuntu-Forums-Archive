---
title: "(Edgy) non-loading programs, hard-disk grinding, near useless IME"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by freshofftheufo on 2006-11-06
A few problems I'm battling with now, maybe someone can point me somewhere I can get help.

1) Programs frequently (20%?) simply don't run when I select them in the upper menu, especially administrative programs such as Language Settings. The "Starting administrative..." tab will often show, but after that the hard-disk just stops reading and nothing happens after the tab disappears. Is this a common problem? Usually the program will run properly if I try to run it again, but sometimes it won't even run after repeated trials. There is definitely a high likelyhood it's a memory problem, but I'd expect some sort of message "Not enough virtual memory" or "Unable to allocate..." instead of just disappearing from the screen. Maybe it's something else?

2) I am running with only 128MB RAM, and I expected/expect Edgy to be rather slow, but I didn't expect it to be *this* slow. Loading a program like Gnome Terminal often takes more than a minute, even when memory use is extremely low. I have a habit of clicking my mouse on the desktop and making squares while waiting for the memory grinding to "settle down", but even when there's nothing running, it never does. I can sit there clicking squares for 10 minutes, and each time I move or click the mouse the hard-drive starts grinding again. I've never had behavior like this in any other OS before, is the VMM or Edgy that bad, or is there something wrong with my configuration? Maybe there's a few easy tweaks I can do to optimize it for 128MBs?

3) Lastly, a completely unrelated problem. I need to use an IME to type in Japanese, and right now I'm using... scim with anthy, though I'm not really sure why I have to use both. scim works well enough when it does, though I can't say it compares to most of the ja IMEs that I've used in Japan, but (as everyone else says) it doesn't work in every application, and for the applications I'm using it barely works in any. It seems to me that it only works in applications that have been specifically configured to allow alternate input IMEs thought their context menus, and that doesn't include Firefox. scim works in every application I've tried, but I can't get it to do anything other than direct input, and since I don't use direct input for Japanese, that's useless for me. Not to mention that running two such programs makes it horrendus to control the input method, and both are prone to switching modes without any warning.

Why do these two programs have such an illogical split? How can I get an anthy-like IME that has support like scim, but still allows for advanced (only advanced on English systems, it's the standard input method here in Japan and has been for years) kanji input? I've been looking through the boards and all I can really find is a lot of talking about how to get them to work at all, not where to find a more logical system for Japanese input.

Thanks in advance for any responses.

---

### Post by moffa on 2006-11-06
Did you do an upgrade or a fresh install.  I did an upgrade and lost my swap partition. If you type "free" in a terminal, you can see how much free ram & swap space you have left.
If you lost your swap partition, just search for the solution, I found mine on the ubuntu bugs page.

---

### Post by freshofftheufo on 2006-11-06
I did a fresh install, and the swap partition was created during installation, though I admit I haven't actually checked since installing. I'll check when I get home.

---

### Post by freshofftheufo on 2006-11-06
Swap seems to be fine, and it's almost empty, even after opening Firefox and all of my basic applications.

---

### Post by jtaylor781 on 2006-11-19
> **freshofftheufo said:**
> Programs frequently (20%?) simply don't run when I select them in the upper menu, especially administrative programs such as Language Settings. The "Starting administrative..." tab will often show, but after that the hard-disk just stops reading and nothing happens after the tab disappears. Is this a common problem? Usually the program will run properly if I try to run it again, but sometimes it won't even run after repeated trials. There is definitely a high likelyhood it's a memory problem, but I'd expect some sort of message "Not enough virtual memory" or "Unable to allocate..." instead of just disappearing from the screen. Maybe it's something else?

I'm having this same problem on 2 different machines. One is my sister's etower with 128MB and the other is my Thinkpad with 256MB. Anybody know what's causing this?

---

### Post by ewl1217 on 2006-11-19
Ubuntu is definitely going to crawl with just 128 MB of RAM. You should use [Xubuntu]("http://xubuntu.org") instead.

---

### Post by suimon on 2006-11-23
> **freshofftheufo said:**
>  I need to use an IME to type in Japanese

with [this]("https://help.ubuntu.com/community/SCIM") you can get scim-anthy running rather smoothly, there is also a link to a scim alternative

> though I'm not really sure why I have to use both

anthy probably cannot run on its own

> for advanced (...) kanji input?

like what?

---

### Post by joe.turion64x2 on 2006-11-24
I am having the same problem, the one related the the speed with which programs are loaded. It started very recently, just yesterday , and I have been using Ubuntu 6.10 for several weeks.

At the very beginning I thought something was wrong with my hard drive since I noticed that the lack of responsiveness **was related to its activity**. For example, when I tried to open a document (and double-clicked it) the hard drive just remained foolishly stopped, only after a while it started to work and loaded the document. I forgave my hard drive when I noticed that it worked just fine under Windows (dual boot).

The facts here are that Ubuntu was working amazingly well before, and that I have a dual core processor with 1Gb of RAM so there is no hardware-related reason for that slow behavior (even Gnome takes about 3 minutes to fully start, it taked before about 30 seconds at the most).

A clue here could be the only 'new' thing I did with my system: at home it belongs to a LAN and yesterday I used SAMBA to share some documents with a Windows XP based PC.

I will try to use the Ubuntu installation cd to try to repair it, if it fails I will recompile Linux kernel and, if I can not find a solution will completely reinstall the system (another distro perhaps).

Good luck to you, and if you know anything please let us know.
Cheers.

---

### Post by joe.turion64x2 on 2006-11-25
I don't care any longer about of this since I am now installing Fedora Core 6 in my Aspire (I am writing this from my Sempron), Fedora 5 works fine and is very stable, I believe FC6 is fine too.
The fact that entirely drove my out of Ubuntu was that after some weeks using the system, it became unusually slow and, out of the sudden, it refused to work ("can not find tty" it said). Fortunately I was able to backup my files. According to several posts I read, that unusual behavior was **produced by the custom layout I kept for my partitions**. Unfortunate though because I can not afford to give all my hard drive to Ubuntu.
Cheers and good luck.

---

