---
title: "google desktop is pissing me off"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by silent1643 on 2007-08-08
google desktop for linux so far has done nothing for me compared to google desktop for xp i use at work..

if i enter a simple filename to google desktop it shows me everything but the file im looking for!?

example i could enter xorg.conf or sources.list or whatever and it will not show me these files - even if i use  the gnome "search for files" it doesnt work, are these files hidden or made non searchable or something? i know i have google indexing my entire home folder

its just reallly annoying sometimes i forget where the system files are that i need to edit etc.. anybody else have these problems..

---

### Post by jkeyes0 on 2007-08-08
> **silent1643 said:**
> google desktop for linux so far has done nothing for me compared to google desktop for xp i use at work..

if i enter a simple filename to google desktop it shows me everything but the file im looking for!?

example i could enter xorg.conf or sources.list or whatever and it will not show me these files - even if i use  the gnome "search for files" it doesnt work, are these files hidden or made non searchable or something? **i know i have google indexing my entire home folder**

its just reallly annoying sometimes i forget where the system files are that i need to edit etc.. anybody else have these problems..

I'm not very familiar with google desktop, but that might be your problem (the bolded part). xorg.conf and sources.list do not reside in /home. xorg.conf is in /etc/X11/xorg.conf, and sources.list is in /etc/apt/sources.list.

---

### Post by ertrules22 on 2007-08-08
Well, I'm not sure if they are hidden, but I think they are, because when you try to edit them from terminal, you have to type, oh say,
```
gedit sudo /etc/apt/sources.list
```
and this will get you there.  So, if you are just trying to search, it may not find them, since they are system files.

---

### Post by Hospadar on 2007-08-08
try using tracker or beagle for your desktop search.  they are both very good and quick, and can search the entire filesystem.  you can either go to applications -> add/remove programs and search for "beagle" and install from there, or do a ```
sudo apt-get install tracker*
```
then go to Places->Search for files

gl!

---

### Post by eentonig on 2007-08-08
> **ertrules22 said:**
> Well, I'm not sure if they are hidden, but I think they are, because when you try to edit them from terminal, you have to type, oh say,
```
gedit sudo /etc/apt/sources.list
```
and this will get you there.  So, if you are just trying to search, it may not find them, since they are system files.

For one, you have the commands reversed. 
For second, "THOU SHALL NOT USE SUDO FOR A GUI!!!!"

If you need sudo power for GUI based applications, please always use gksudo.
So, your code should be:
**For GUI:**
> gksudo gedit /etc/apt/sources.list

or
**for CLI:**
> sudo vi /etc/apt/sources.list

---

### Post by ertrules22 on 2007-08-08
Well, I couldn't look at the correct order, and I have only been using Ubuntu for a few days anyway.  I was posting from Windows at the moment, so please forgive my blunder.
Anyway, I am sure they got the general idea.
And why not use sudo for a GUI, it works just fine.
Just wondering the reason for your outburst of anger.
:)

---

### Post by silent1643 on 2007-08-08
> 
try using tracker or beagle for your desktop search. they are both very good and quick, and can search the entire filesystem. you can either go to applications -> add/remove programs and search for "beagle" and install from there, or do a

thanks! going to remove google desktop tonight for sure

i dont think using sudo for gedit will hurt anything, i have been using it for awhile now.

---

### Post by Inxsible on 2007-08-08
> **ertrules22 said:**
> Well, I couldn't look at the correct order, and I have only been using Ubuntu for a few days anyway.  I was posting from Windows at the moment, so please forgive my blunder.
Anyway, I am sure they got the general idea.
And why not use sudo for a GUI, it works just fine.
Just wondering the reason for your outburst of anger.
:)

I dont think it was an outburst of anger. He was just trying to tell you something. But when using GUI applications it is not recommended to use sudo. This [link]("http://psychocats.net/ubuntu/graphicalsudo") details why

---

### Post by silent1643 on 2007-08-09
installed beagle search and added "/" to the index preferences
searched for xorg.conf
here are my results - why can't it find the file??

[[IMG]http://img380.imageshack.us/img380/9260/screenshotzf5.th.png[/IMG]](http://img380.imageshack.us/my.php?image=screenshotzf5.png)

---

### Post by Blofeld on 2007-08-09
Did you click on that green arrow at the top right?  You are currently only viewing 8 of 88 hits.

---

### Post by silent1643 on 2007-08-09
> **Blofeld said:**
> Did you click on that green arrow at the top right?  You are currently only viewing 8 of 88 hits.

no i didn't :oops: but i would think searching the exact file name should bring it up on the first page? eh
im at work now, i will find what page it displays on tonight.

---

### Post by qamelian on 2007-08-09
> **ertrules22 said:**
> And why not use sudo for a GUI, it works just fine.

No, it doesn't. It can mess things up with some graphical apps. Here's a more detailed explanation why it's a bad idea:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by ertrules22 on 2007-08-09
> I dont think it was an outburst of anger. He was just trying to tell you something. But when using GUI applications it is not recommended to use sudo. This link details why
Well, he could have said it like that.  I see what he means, but he could have said it in a more civilized manner at the very least, but all this is against the purpose of the thread.  But thanks to eentonig, now I know to use gksudo, so thanks, but if you will please use civilized speech for the next helpful comment, it will be much appreciated.  Thanks,
ertrules22

---

### Post by Inxsible on 2007-08-09
> **ertrules22 said:**
> Well, he could have said it like that.  I see what he means, but he could have said it in a more civilized manner at the very least, but all this is against the purpose of the thread.  But thanks to eentonig, now I know to use gksudo, so thanks, but if you will please use civilized speech for the next helpful comment, it will be much appreciated.  Thanks,
ertrules22

I am sure it was just a misunderstanding on both sides. The uppercase that eentonig used, might seem like he was shouting/angry(in internet speak), but (i think) he was only trying to "emulate" (for lack of a better word) the way the ten commandments are normally given/spoken. 
Maybe you weren't familiar with it, maybe you were. I don't know.

PS . the reason i think he wasn't angry was because he does use this line

> **eentonig said:**
> If you need sudo power for GUI based applications, please always use gksudo. which is pretty civilized and is a request.

Anyway...I think i digress too far from the thread topic so I shall end it right here :)

---

### Post by silent1643 on 2007-08-09
guess this thread is heading off into another direction..


why the hell can't sudo reconize if it needs to launch a program graphically or not

if there wasn't sudo i would still launch firefox or whatever the same way, why does sudo screw things up.:confused:

---

### Post by silent1643 on 2007-08-09
> **Blofeld said:**
> Did you click on that green arrow at the top right?  You are currently only viewing 8 of 88 hits.

okay to answer this, i am now on my linux system an no it did not have the xorg.conf file anywhere on the other results..

still no solution?

---

