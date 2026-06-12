---
title: "stuck at gdm"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by devilsadvocate1987 on 2006-11-09
I've been having a weird problem. GDM doesnt let me log in to an X session. Rather, it does, but then I get logged out instantly. Its almost as if X is crashing on me each time i try to log in.

I have Gnome, fvwm, fvwm-crystal, e17, and fluxbox installed. All of them do the same thing.

I am able to go to one of the other virtual consoles and login to the command line, though.

Any suggestions?

I'm on a really old Sony Vaio, Intel 82815 Graphics, 384 MB of RAM, PIII 800 MHz

---

### Post by Ecthelion on 2006-11-10
Did you once have the login etc working?

Do you suspect something you did to be the reason of this?

Or could you never login in Edgy?

btw, I'm not sure if it's a good idea to put edgy on a real old computer...
Maybe it would be a better idea to use Dapper (just a suggestion)

---

### Post by devilsadvocate1987 on 2006-11-10
I've been using edgy since knot2

I think its logging me in. I had this problem once before which I think was caused due to the fact that I had no hard drive space left. It started working after I deleted stuff from the console. Not this time though. I removed a lot of large files using ```
rm <filename>
``` from the terminal. Still no luck.

---

### Post by Ecthelion on 2006-11-11
You can try 
```
df
```
to see if one of your disks ran out of space...

Also, when I want to log in, I can change session and one of the choises is to use the "failsafe"...
Did you tried this?

Since you get the login screen this isn't a driver problem...

---

