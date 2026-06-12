---
title: "VMware Server - 3 Quick Questions"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-26
Hi folks !

I installed VMware Server and I set up an XP virtual machine (no more dual-booting from now on, hooray!!) for work and school stuff. 

My PC is a P3 one with 1 GHz CPU and 384 MB RAM. I assigned the virtual machine 160 MB RAM, as recommended, and a small virtual HDD of 3 GB, since I don't need too much stuff on it anyway.

I now have 3 questions I can't quite figure out, I thought someone might be able to clarify things for me.

*Quick question #1* - This one is kind of stupid, I know, but I just need a "verdict": I suppose that the virtual HDD that I assigned to my virtual machine acts like a real one, right? I mean... I still need to allow it a swap space of some hundreds MB free, don't I ?

*Quick question #2* - I need to use Borland's IDE and Turbo assembler, Borland C++ 3.11 to be more specific. Since this is a DOS-based app, I stumbled into a very strange thing: it doesn't... work. The install fails after a few seconds, i.e. the "cmd" window closes after a few seconds. The only way I managed to get it installed and usable was to use DOSBox. Sure, it runs fine under DOSBox... after I mount it, after I modify the environment variable PATH and after I alter the keymapper (I *don't* need DOSBox to kill itself when I hit Ctrl+F9, LOL, I just need that key combination for running my app within the IDE). My question to you is if this behavior is normal... ?!

* Quick question #3* - To be honest, I only need 2 things to run under XP: Borland C++ 3.11 for school and Macromedia Flash 8 for work (it runs through Wine, too, but not satisfactory enough, sorry)... ok, somehow they work, that's not the problem, but I was curious if I can get installed an old game, packed with a Win95 installer (it's called "Spaceward Ho"). The kit has only 2 MB or so and it ran ok on a real XP machine. Sure this isn't a big problem, but I was wondering... WHY doesn't the installer even start?! I mean, I double-click on "setup.exe" and nothing happens, and I can't even see the process in TaskManager, it's kind of odd, don't you think? I even tried to get it to run in compatibility mode for win95, but that doesn't help either.

Thank you for reading such a long and boring post :)

LLRNR

PS - If it helps, yes, I installed VMwareTools, too.

---

### Post by LLRNR on 2006-11-26
Gosh... do these forums move fast or what ? :D Page 3 already !! I'm sorry for my rudeness... :D

LLRNR

---

### Post by LLRNR on 2006-11-27
EDIT - Never mind, sorry for this last post, I managed to enable the USB flash drive... a USB controller had to be added first, of course, I should have known that. :D

---

### Post by gn2 on 2006-11-27
Isn't it going to crawl like a slug on that hardware? 
XPsp2 really needs about 512mb RAM

---

### Post by LLRNR on 2006-11-27
> **gn2 said:**
> Isn't it going to crawl like a slug on that hardware? 
XPsp2 really needs about 512mb RAM

Ummm... yes, you might be right, but that's all the RAM I have (384 MB) and, according to VMware's setup settings, 160 MB is the amount recommended.

Anyway, I just wiped off all my HDD and installed Edgy; clean; NO MORE NTFS !!! :lol: (ok, VMware, but at least it's a virtual machine, not a real install)

LLRNR

---

### Post by AndyCooll on 2006-11-27
I have VMware Server installed on one of my boxes and use an XP image on it and everything seem to run fine. When I logon to it I go full screen and simply treat it as if it's the only OS on the pc. True ...I only play FM2007 and therefore there aren't too many things that can go wrong since I don't have much installed on it. However, I've installed Samba on my file server, so my XP image can see my shared folders and printer. And because of this I've installed WinClam and the firewall, just in case!  

What you may need to to be aware of though is that your image isn't actually "seeing" your hardware. Rather it sees "virtual" hardware, i.e that built in to the VMware software. 

Q1. You shouldn't need to manually allocate that, rather the XP install process will do the work for you.

Q2. Not sure about this. Your XP VMware image should work in exactly the same way that it would work as if it were installed on the pc by itself. 

Q3. Have you tried starting it from the command line and seeing if that displays any errors.

:cool:

---

### Post by LLRNR on 2006-11-27
> **AndyCooll said:**
> 
Q2. Not sure about this. Your XP VMware image should work in exactly the same way that it would work as if it were installed on the pc by itself.

This is odd, I just wiped off my HDD and did a clean install of Kubuntu Edgy today (WITHOUT WINDOWS !!!); after I set up my system, I set up VMware Server too and installed Borland C++ 3.11 again. 

This time, the old DOS-installer crashed by itself with an internal error i.e. the "cmd" window did not close by itself... wow this was a step further indeed... but I still needed to install in properly with DOSBox.

Also, it runs through the command prompt without crashing, but I can't actually use it like this since it can't include it's headers, although I altered the settings for the PATH environment variable just as on any real XP install (it needed to have "c:\borlandc;c:\borlandc\bin" included in PATH). This simply doesn't work and I don't know why, but I can still use it with DOSBox.

> **AndyCooll said:**
> Q3. Have you tried starting it from the command line and seeing if that displays any errors.


Hey check this out !! This time, running VMware Server on Edgy instead of Dapper, the win95 installer started normally, the game is installed and it's actually playable / usable with no issues at all.

Am I getting close ? Is there really a significant difference in the way that some apps run on Dapper compared to Edgy ?... I would really like to hear some thoughts on that (after all, it might all be in my imagination!)

LLRNR

---

