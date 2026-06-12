---
title: "locking-up at login"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by bdwetzel on 2006-10-16
Greetings, 
OK, so I having been using windows forever, I dont like it, and havent liked it for a while...I have wanted to switch to linux for a long time, just didnt have the guts.  But, I did my research and landed on dapper ubuntu and would absolutely love for it to work.  I have tried liveCD amd64 and 386, alternate amd64 and 386--liveCD froze often times before i could even try to install, and if i could it would freeze.  Alternate versions both lock up at login.I have installed 386 on a friends computer(some 32bit intel i dont know specifics) but it worked right away :mad: of course.  I have done cd checks and memory checks.  I have intsalled amd64 server and it worked but i have no clue what i am doing so that is not helpful. Assume i know nothing and any help will be appreciated greatly
specs:
amd64 3000, gigabyte mb, nvidia3 chipset

---

### Post by Kateikyoushi on 2006-10-16
Most likely you have to set some kernel options at boot.
What is the chipset on that motherboard ? The forum has an A64 part where you might find a solution.

When the cd boots at the menu press F6 try out some of the options like.

Boot: linux noapic 
Boot: linux pci=acpi

---

### Post by elchinovi on 2006-10-16
Since you have the server working, have you tried to install the desktop from the command line?
Do you need instructions on how to do that?
Let us know.
Thanks!

---

### Post by bdwetzel on 2006-10-16
hey,
thanks for responding so quickly.  I have tried noapic already...and i would need some instruction for installing from the server version.  I was reading some other forum posts..and someone said if he pressed ctrl-alt-f1 at login before it freezes and then ctrl-alt-f7 at the terminal, and then it logs in ok...I want to see if that works.  that might help narrow down the problem.

peace

---

### Post by bdwetzel on 2006-10-16
OK, so that did not work...Probably could have guessed that. It just freezes there too...seems like after a certain preiod of time.  Though i dont know why that would be...

---

### Post by elchinovi on 2006-10-16
> **bdwetzel said:**
> hey,
thanks for responding so quickly.  I have tried noapic already...and i would need some instruction for installing from the server version.  I was reading some other forum posts..and someone said if he pressed ctrl-alt-f1 at login before it freezes and then ctrl-alt-f7 at the terminal, and then it logs in ok...I want to see if that works.  that might help narrow down the problem.

peace

To instal Ubuntu Desktop from the server, type this:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

The "ctrl-alt-F1/F7" is to open different consoles for different uses...
Remember that Linux is a true multi-user OS...

Anyhow, try installing the desktop version and see if it helps.
Good Luck!

---

### Post by bdwetzel on 2006-10-16
thank you so much, i am reinstalling server as i type this, so i will  try that and get back to you...

---

### Post by bdwetzel on 2006-10-16
OK, it is installing...
While I am waiting, I was wondering if someone could tell me why installing from the server might work when the other methods(liveCD and text) did not.  I am new to linux and I want to learn as much as I can, rather than just doing things because people say I should

---

### Post by petri on 2006-10-16
You may run to same problems I'm afraid and I really do hope I'm wrong. I have struggled by myself with these lockups and  what helped me was the right drivers to my ATI. Nvidias drivers with howto you'll find here [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper) I hope it's up to date.

I think you should install those drivers when you install the desktop but I'm not sure, maybe it's better to install desktop first and see if it works. If not you should be able to boot in recovery mode where you are a single user, a root. Then install Nvidia drivers. I'm sorry I can't give you any straight answers just suggestions.

---

### Post by elchinovi on 2006-10-16
> **bdwetzel said:**
> OK, it is installing...
While I am waiting, I was wondering if someone could tell me why installing from the server might work when the other methods(liveCD and text) did not.  I am new to linux and I want to learn as much as I can, rather than just doing things because people say I should

I think that It may work because the Server is the most basic of all installations...
It comes with no GUI, and just the basic stuff so you can start building your server with just the stuff you need and nothing else...IMO
Hope this works!

---

### Post by anaconda on 2006-10-16
You could try the 32-bit version of ubuntu. I have heard numerous problems with 64-bit versions.. mostly about drivers and programs, but 32-bit version could work better for you..

---

### Post by bdwetzel on 2006-10-16
I have already tried 32-bit livecd and alternate...anyway, i just finished installing desktop from the server...it asking me something about postfix config-->no config|Internet Site|Internet Site with smarthost|Satellite system| Local Only|...it took so long to install i dont want to have to do it again. :., i want to be careful in setting it up...what should i choose...I just want to run the desktop ( though i would like to set up LAMP at some point)

---

### Post by bdwetzel on 2006-10-16
OK, well for some reason it locked-up during install...I am going to try installing the nvidia drivers, if i can.  Sigh, I really want this to work.  I wonder if it is this difficult for every A64 user.

---

### Post by petri on 2006-10-16
Yes, as I have noticed the A64 users report more problems but I might be a little bit subjective.

They do report ](*,)  with 32-bits Ubuntu too but so do we who have older CPUs (32-bit)

Have you checked out the **x86 64-bit Users** forum at [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

### Post by bdwetzel on 2006-10-16
OK, here is the latest developement...because installing from the server version of ubuntu did not work, I decided to reinstall (again) the a64 desktop version of ubuntu 6.06.  I also went into recovery mode after the install and installed the nvidia drivers. I rebooted, but again it froze (though i did get to see a pretty nvidia splash screen).  

I was reading somewhere about startx...so i rebooted in went recovery ran startx..and i am successfully sending this post in ubuntu.  But i would still like to be able to be able to login--to refresh all of my faithfuil helpers: 
*specs--
Gigabyte k8ns mobo--Nvidia nforce3 250 chipset--amd64 3000 processor...

let me know if anyone has any ideas

---

### Post by petri on 2006-10-17
The first idea that came to my mind is that now you run your Ubuntu as a root and that is not good at all. Recovery mode means single user mode without graphics (if you don't run startx) and single user mode means root.

Have you visited the 64 forum? 64-bits Ubuntu is simply not for beginners. Running as a root makes your system vulnerable and it can be compared to running Windows as the Administrator. That was one of the main reasons wqhy Windows computers got so bad reputation. In Windows you can't run as Administrator temporarely as often you need and then you have to logout an d login again which makes it too difficult for many users. In Ubuntu you can always run as a root with the command sudo. That is one of the reasons Ubuntu is safe.

You should consider to install 32-bits Ubuntu and get that working, there isn't so many applications which uses 64-bits architecture in Desktop so you ain't losing so much with 32-bits Ubuntu. If you decide to keep on 64-bits Ubuntu make it work to regular users.

You could make a Search with you motherboard chipset and see if that's causing the problem. I hope you get Ubuntu running soon.

---

### Post by bdwetzel on 2006-10-17
Hey thanks...I see the how it is a problem to run as root, And i already switched to 32-bits it was too much of a hassle in 64-bits though it did seem faster.  Anyway...I still have the login issue...I cant login as a user, only as root with startx.  Thanks for all your help.  If anyone has any ideas let me know.

---

