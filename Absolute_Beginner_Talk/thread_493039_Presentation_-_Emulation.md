---
title: "Presentation - Emulation"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Durden10 on 2007-07-05
Hi

I don't know if this is the right forum, but anyway, I just installed Linux a few weeks ago and I'm having one small problem left. I used to work with a program called "Presentation" from Neurobs, a program for creating experiments. Unfortunately, it only runs on Windows. I was wondering if it would be possible to nevertheless run this program on linux using a emulation-like program.
Thanks,
Joe

---

### Post by kosmic on 2007-07-05
You can try using wine to run that program.

Just open synaptic and search for "wine" or in a terminal type

sudo apt-get install wine


more info about wine here - [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by meatpan on 2007-07-05
Some linux users can get programs to run using windows/linux compatibilty software called wine:  [http://www.winehq.org/](http://www.winehq.org/)

Wine is trying to accomplish a difficult task, so be patient and keep your expectations low.  If you have time and interest, you can help the linux community by informing the neurobs developers that you need linux support.

EDIT: see previous post

---

### Post by kuja on 2007-07-05
You could try to run it with WINE. It *may* work, may not. I don't see an entry for it in the wine application database.

---

### Post by Durden10 on 2007-07-06
Hi,

I tried it out, the only response I got was:

could not load L"c:\\windows\\system32\\pres.exe": module not found


Edit: It finally works now!

---

### Post by Durden10 on 2007-07-09
Hi

I successfully installed the program on my system, unfortunately after trying to insert an activation code, I repeatedly got this message: Error storing license information - error setting ACL
HRESULT: 120. ?????

---

### Post by snobby500 on 2007-07-09
sorry, i have no idea about the error, but you could try making a virtual windows, so that you can work with windows, while you are in ubuntu, that it,, unless you dont want to use any of windows whatsoever, which is fine too :)
here are two virtualisation programs i know of:
1) virtualbox [http://www.virtualbox.org/]("http://www.virtualbox.org/")
this one is very easy to set up, but it isnt able to do anything with 3d, as far as i know, or use direct draw.
2) vmware [http://www.vmware.com/]("http://www.vmware.com/") 
i dont know much about vmware, i think they have got 3d and direct draw working a little at least, but i think it is also more difficult to set up, again ill say i dont know much about them :)

just an idea, hope it helps :)

---

