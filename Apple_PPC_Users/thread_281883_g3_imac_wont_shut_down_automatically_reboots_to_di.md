---
title: "g3 imac wont shut down automatically reboots to distorted screen"
date: 2006-10-21
forum: Apple PPC Users
---

### Post by cobelloy on 2006-10-21
hi, I have just reinstalled dapper on our slot loading g3 imac (350mhz/256meg), the first install ended up corrupted - the error it gave me was something about the hard drive being out of space (I cant remember, but I did fill up the tiny HDD) and it couldnt get past the login screen

before dapper it had hoary for ages with no problems - but software I wanted for hoary was no longer available available (missing dependancy for gcompris, oo.org 2.0 etc...) so I put dapper on it.

aside from the annoying problem with the live cd only booting to a blank screen due to incorrect video settings (which you have to edit with vi before it will work - lucky theres a good forum!) the install is terriffic, after installing the first time I installed xfce and rox for a lightweight desktop with icons, this time I installed xubuntu-desktop and rox

anyway the problem is this - when I try to shut down, either by choosing log out, then shut down, or by just choosing shut down, the computer shuts down then immediately reboots to a very badly distorted screen, the only way to shut it off is to hold in the on/off key until it dies

this is the same for standard ubuntu (before xfce/xubuntu) and for plain xfce or xubuntu, and it never happened with hoary, or with breezy which I tried briefly from a server install to which I added icewm (and rox).

I read a couple of posts that suggest there is some missing support for older imacs in dapper, that is found in breezy, so how do I fix this - can it be fixed or how about I reinstall breezy server and do apt-get install xubuntu-desktop ? would that give me the complete xubuntu system on top of the server install? all I really want on it apart from xfce + rox, are vlc (and codecs), gcompris and childsplay - since it is my 3yo daughters computer

---

### Post by cobelloy on 2006-10-23
well, no replies yet, maybe this is just happening to me then.

maybe some other g3 imac users might post here and let me know if their machines shut down normally?

perhaps the machine has developed some sort of internal problem since I installed dapper?

---

### Post by DirtDawg on 2006-10-24
Well, my g3 sounds very similar to yours, runs Xubuntu and shuts down fine. When booting up, usually half the screen turns into a garbled mess for a few seconds, but then it goes away and boots up normally. I ran Ubuntu Hoary and had no problems there either. Sorry.

Also, yes you can use
```
 sudo aptitude install xubuntu-desktop 
```
to install the Xubuntu desktop on a server install.

---

