---
title: "[SOLVED] which cd is this???"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by aliencam on 2007-10-26
okay i feel like an absolute idiot right now, i've been usung ubuntu exclusivly for about eight months, but i've never had a problem like this before... 

I reformat often, I have one hard drive on which i just install operating systems and switch them out all the time, and on another hard drive i store all my configurations and data. 

Right now I have about six ubuntu cds on my desk.  I hand them out and install ubuntu on people's computers as often as possible, but these are usually the i386 version.  One of the cds on my desk is an x64 bit versoin, and currently there is no operating system installed on my computer.  I would like to install this x64 bit version of gutsy. 

I think I have it in the drive right now, I am using the Live CD, but I don't know how to tell.  

cat /etc/issue  just says 7.10, and so does system>about ubuntu 

What I tried was to go into the sources list, but there is no /etc/aps/sources.list
 on the live cd i guess...  

When I look up software to install in the add/remove programs menu, i can see Helix and Wine, and as far as I know there are no helix or wine version for x64, but this could have changed in gutsy... 

anyway, i put this here since i don't really need support, its just kind of a stupid question.

---

### Post by LowSky on 2007-10-26
there is wine, i know because i installed it but as for helix... i dont know, and i'm not near my ubunutu machine.

there got to be something listing it as 64 bit in about ubuntu under system..?
 if you have a x86 machione laying around try all the discs in that, the one that doesn't work it is the 64bit version

---

### Post by ddrichardson on 2007-10-26
What about uname -r, will that not give a x64 kernel if running x64?

---

### Post by aliencam on 2007-10-26
uname -r just says 2.6.22-14-generic

i don't have a x86 computer around here... and nothing in about ubunu says x86 or x64... 


I just thought of this: firefox should have different versions in the "about" menu.  Mine says  " Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6" 

which makes me confused because it is not i386, but its says i686, so i dunno... can anyone tell me what their "about> mzilla firefox" says??

---

### Post by Maestro23 on 2007-10-26
> **aliencam said:**
> uname -r just says 2.6.22-14-generic

i don't have a x86 computer around here... and nothing in about ubunu says x86 or x64... 


I just thought of this: firefox should have different versions in the "about" menu.  Mine says  " Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6" 

which makes me confused because it is not i386, but its says i686, so i dunno... can anyone tell me what their "about> mzilla firefox" says??

> uname -a

I running 64-bit Gutsy, here's my output from that command:

>  2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 **x86_64** GNU/Linux

---

### Post by aliencam on 2007-10-26
dang, i must have the 32 bit version then. 

```
Linux ubuntu 2.6.22-14-generic #1 SMP Wed Oct 10 06:00:47 GMT 2007 i686 GNU/Linux
```


thanks everyone

---

