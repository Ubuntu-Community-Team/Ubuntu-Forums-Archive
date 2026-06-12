---
title: "LiveCD as diagnostic tool? Root capability?"
date: 2005-11-02
forum: Apple PPC Users
---

### Post by thearne on 2005-11-02
Hi- 

I would like to use LiveCD as  a tool for diagnosing, even potentially repartitioning my iMac.  Panther does not boot.  

Is there any way to get root privileges using LiveCD?  I have tried 'sudo -s -H' in the command window, but when trying to then open Konqueror (for example) I get error message:  xlib: connection to ":0.0" refused by server. xlib:  no protocol specified.

Can anyone help?

Thanks.
Tom

---

### Post by seatea on 2005-11-03
Look up a thread in the Breezy Badger forum "Desktop" titled "After installation: Ubuntu maintenance?" It might have the information you want.

---

### Post by Rinnan on 2005-11-10
Hmm, try this..

#1:  Before you sudo -- do 
```
xhost +
```
from any terminal.  Then, do
```
sudo su
```
I would check it myself, but am not at home.  However give it a try and if it does not work, then I'll try it out on my home machines (I've got liveCD's for x86 and ppc, and an ibook g3 700 as well as a mini-itx via epia)

I don't think it's either architecture or k/u (kubuntu/ubuntu) specific.

I know it's possible, I've routinely used the live CD's (ubuntu CD and DVD) for various system restore work, I've just forgotten the exact commands.  Must be muscle memory :razz: )

---

