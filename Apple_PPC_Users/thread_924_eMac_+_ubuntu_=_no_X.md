---
title: "eMac + ubuntu = no X"
date: 2004-10-16
forum: Apple PPC Users
---

### Post by miansancor on 2004-10-16
Hi every one :) Greetings from Granada (Spain)

Really this ppc linux distribution is with difference the best! Mostly 'cause  the nice helpfull community!  :D Although mine is not yet solved  :( 

Well here is my problem:
I have a nvidia geforce 2 Mx video card and I do not find the way to make it to work :oops:
  
Any of you have succeded in that matter? Or aware of any eMac linux x.conf that works.

Thanks for any help! :lol:

---

### Post by bakunin74 on 2004-10-17
Hi!

I searched around a bit and found a XF86Config file from a brazilian Mandrake PPC User...
...changed some parameters (you schould change the keyboard layout from "de" to "es") and finally it worked and still does on my eMac with his lame GForce 2MX. Maybe there could be done some optimization but i am not that kind of an X-pert...
You can download the file from:

[http://homepage.univie.ac.at/georg.koe/XF86Config/XF86Config-4.emac700nvidia.working](http://homepage.univie.ac.at/georg.koe/XF86Config/XF86Config-4.emac700nvidia.working)

How to install:

Boot into ubuntu, The xserver will go down and you fall back to the shell. login and then type

% sudo -s

again provide your password

% cd /etc/X11

backup your old conf-file

% mv XF86Config-4 XF86Config-4.old

download the new config

% wget [http://homepage.univie.ac.at/georg.koe/XF86Config/XF86Config-4.emac700nvidia.working](http://homepage.univie.ac.at/georg.koe/XF86Config/XF86Config-4.emac700nvidia.working)

rename it

% mv XF86Config-4.emac700nvidia.working XF86Config-4

reboot your system (not necessary but who knows)

now it should work

---

### Post by miansancor on 2005-01-26
Thanks a lot because your replay finally I can have X on my eMac

---

### Post by jjramsey on 2005-02-05
If you are running an eMac with ATi graphics, bug [4297](https://bugzilla.ubuntu.com/show_bug.cgi?id=4297) may hit you. I follow the advice in [comment #5](https://bugzilla.ubuntu.com/show_bug.cgi?id=4297#c5) of the bug and got things working.

Posting from Hoary LiveCD (array-4).

---

### Post by HBomb187 on 2005-08-05
one note on the above mentioned post, this does indeed work, but in the newest version of ubuntu (5.04 Hoary) but the x server will not kill itself, you have to invoke a new login prompt (control+apple+f1) and follow the rest of the instructions up until the point of actually naming the config file, the name differs in this release, it is xorg.conf, this does indeed remedy the issue of no video in x, because it is obviously still an issue on the eMac

---

