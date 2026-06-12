---
title: "hard drive eating???"
date: 2005-02-14
forum: Apple PPC Users
---

### Post by redneckr1 on 2005-02-14
hi i have a small well nearly serious problem, i was reading on the forums (these ones) about ubuntu using up loads of temp room. and i have noticed i have very little hard drive space left. how can i go about freeing up some room as ive only got a 4 gig hdd and ubuntu is eating it all up.

thanks again

Red

---

### Post by cblack on 2005-02-14
You could try running:

```
sudo apt-get clean
``` 

Which will clean out the repository of downloaded debs in /var/cache/apt/archives.

Other than you can go about removing software programs you don't need and/or want.

---

### Post by redneckr1 on 2005-02-15
How?

i havent got the foggiest how to remove programs. i just barely know how to operate filemanager  :-?

---

### Post by Buffalo Soldier on 2005-02-15
[QUOTE=redneckr1]How?

i havent got the foggiest how to remove programs. i just barely know how to operate filemanager  :-?[/QUOTE]

cblack has told you earlier on how to do this.

Look at the **top panel** (or taskbar as MS Windows calls it). Go to **Applications -> System Tools -> Terminal**. And then you will see a window pops up. Type **sudo apt-get clean** into that window and press **ENTER**. It will then ask for a password, just enter your usual password that you use to log in, then press **ENTER**.

---

### Post by redneckr1 on 2005-02-17
i know how to operate terminal thanks for the walk through. did come in handy talking my mum through it.

i meant the program removal that was my question, i have python etc.. which i really dont need as my nixmac is a glorified office machine which plays mp3s. (quite well in fact)

anyone?

---

### Post by val1984 on 2005-02-17
Use synaptic to uninstall software...

---

### Post by Buffalo Soldier on 2005-02-17
[QUOTE=redneckr1]i know how to operate terminal thanks for the walk through. did come in handy talking my mum through it.

i meant the program removal that was my question, i have python etc.. which i really dont need as my nixmac is a glorified office machine which plays mp3s. (quite well in fact)

anyone?[/QUOTE]
 Sorry about that :) Though you were asking how to sudo apt-get clean. My mistake.

There are two ways that I use to remove a program.

1) sudo apt-get remove *program*

2) run synaptic, right click on the program to be remove and select **Mark for Removal** or **Mark for Complete Removal** and then click **apply**.

---

### Post by redneckr1 on 2005-02-21
thanks.

now to get synaptic working :/

---

