---
title: "amaroK is running fine, but no music in the speaker"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by Mechonaj on 2006-03-13
Hello,

I began with kubuntu two weeks ago, most things are running fine. One problem is amarok. When I click on the play-button, the application links the stream, finds it and begins to buffer, from 0 to 100 percent, buffers again and again, but never starts to play.

What am I doing wrong, or which permission is missing?

Thanks
markus

---

### Post by shuttleworthwannabe on 2006-03-13
go to:
 settings.config amarok>engines>sound system and change to xine engine

if you do not have it installed use syntaptic and install amarok-xine (or something like that).

Good luck

---

### Post by Mechonaj on 2006-03-13
thanks shuttleworthwannabe,

but as I told, I'm a really really newbie. That means I even do not understand what your answer means. Sorry please. Could you write it down in an easy to understand kind of bulletin.

Thanks a lot, if possible.

Regards Markus

---

### Post by shuttleworthwannabe on 2006-03-13
Ok, my bad.

1. start amarok
2. in menu bar (under title), go to settings
3. configure amarok
4. In the side bar, click engine
5. choose an engine in the sound system drop down menu; choose xine engine

If you do nt have the xine engine installed (then follow these excellent wiki on how to set up multimedia in Ubuntu: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

when here just follow the step-by-step codes as they are written (cut and paste is what I did) in terminal window, and off you go, perfectly working multimedia support.

---

