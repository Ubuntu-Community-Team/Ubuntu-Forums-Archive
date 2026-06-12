---
title: "[SOLVED] 7.10 is terrible loading"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by farueulogy on 2007-10-20
I installed it - I removed it.

7.10 takes 5 minutes just to get to the log-on screen. 7.04 takes 20 seconds.

Anyone think that's justifiable?

*PC spec in signature*

---

### Post by flexion on 2007-10-20
it's booting super quick here
it would be helpful if you post a bootchart of that 7.10 installation

---

### Post by drinkpepsi on 2007-10-20
I have the same problem on my laptop. Only way I've found around it is when it says starting up, wait till the screen goes black, then hit alt+f1. It takes about 15-20 seconds to load then, but you have to do that each time you boot up or reboot.

---

### Post by PPAAUULL on 2007-10-20
No you don't have to hit those keys. I think that you can disable the bootsplash if that is the problem.

---

### Post by monstar on 2007-10-20
You have to edit the kernel

If you get to boot lines, hit e

I think in the 2nd line, at the end it says something like "ro quiet splash"
and 4th line, it says quiet

Take those out and it will boot up, but this is only a temporary fix


Sorry, I am new to this Linux thing, there is a file somewhere where you can edit your boot.  I used Gedit to make the changes, take out spash/quiet

And it will boot up quickly again

---

### Post by latheesan on 2007-10-20
I got the exact same problem. I thought it was just me lol.

> If you get to boot lines, hit e

What do u mean by this?

---

### Post by PmDematagoda on 2007-10-20
You could also edit them while in Ubuntu with this:-

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Kosimo on 2007-10-20
I'm also having the same issue...
Takes around 5 minutes to load when in feisty it takes just 20 secs.

---

### Post by monstar on 2007-10-20
> **latheesan said:**
> I got the exact same problem. I thought it was just me lol.



What do u mean by this?

Sorry dude, Like I said, this is my 2nd day using Linux
I have no idea what I'm talking about..

When i meant Hit E..

I have it set up as Dual Boot, so when i'm booting up and its asking me to choose Ubuntu Kernel or Windows...Highlighting Ubuntu, I press E on the keyboard...

BUT
To make the permanent changes
Do what PmDematagoda said

---

### Post by misfitpierce on 2007-10-20
Mine loads super fast as well. Perhaps a piece of hardware is giving an error and not loading correctly. Could slow down boot.

---

### Post by mb01915 on 2007-10-20
> **monstar said:**
> Sorry dude, Like I said, this is my 2nd day using Linux
I have no idea what I'm talking about..

When i meant Hit E..

I have it set up as Dual Boot, so when i'm booting up and its asking me to choose Ubuntu Kernel or Windows...Highlighting Ubuntu, I press E on the keyboard...

BUT
To make the permanent changes
Do what PmDematagoda said

I have 7.10 installed on two desktop and a laptop.  Startup is as quick as ever on the desktops.   The laptop is slow but not 5 minutes.  The laptop is dual boot with xp.  I wonder if the slow boot is due to the dual boot install?

---

### Post by markp1989 on 2007-10-20
mine boots alot faster then 7.04 ever did.

i checked using boot chare, fiesty took 30-40 sec, and gusty takes about 20-25 sec to boot


, did u do a clean install or an upgrade?

---

### Post by Zalbor on 2007-10-20
Mine loads faster than 7.04 too. At least I think it's faster, but certainly doesn't take more time.
As for boot options, I'm also dual booting with XP and "quiet" is turned off, but "splash" still there. I dunno if that matters...

---

### Post by Super Nade on 2007-10-20
Dude, it's loading super fast on my Desktop. Faster than Winblows by a good 20-30 seconds. What is your system config?

---

### Post by PPAAUULL on 2007-10-20
just installed 7.10 and it starts really fast. Faster then 7.04 and I have a dual boot so I think it might have something to do with the laptop.

---

### Post by Kosimo on 2007-10-20
Is not happening to everyone.
It seems to be a very particular problem witch affects some users.

So, 'till be fixed I'll wait more than 5 minutes to get the login screen...

By the way, I have a question to the affected people.
Do you guys have a windows partition apart the ext3 in the same HDD ?

---

### Post by PPAAUULL on 2007-10-20
I don't think that would be the problem cause I have that and mine works fine.

---

### Post by farueulogy on 2007-10-20
> **flexion said:**
> it's booting super quick here
it would be helpful if you post a bootchart of that 7.10 installation
I don't know how to do that.

---

### Post by farueulogy on 2007-10-20
> **PmDematagoda said:**
> You could also edit them while in Ubuntu with this:-

```
sudo gedit /boot/grub/menu.lst
```

What should I edit? :(

---

### Post by markp1989 on 2007-10-20
> **farueulogy said:**
> I don't know how to do that.

sudo apt-get install bootchart

reboot
look in /var/log/bootchart

---

### Post by jaybombalous on 2007-10-20
Can someone interpret this? I am not sure if Gutsy is loading slow or its my desktop that loads slow.

All I know is in feisty when I heard music after signing in all my stuff, skype, gdesklets, etc... loaded immediately. Now I have to wait an enternity for everything to load before I can even use the desktop. Any thoughts here?

---

### Post by dptxp on 2007-10-20
I read this solution to loong boot up time somewhere in the forums, tried it, and Gutsy
now loads real fast, though I get BIOS ERROR #81 and other error messages.

to disable, go to the terminal and type -

sudo gedit /boot/grub/menu.lst
...and enter your password

a big text file will open - you need to scroll right down to where it says ...


## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet splash


...or similar. just change 'splash' to 'nosplash' and save. reboot and celebrate!
cheers
roger

---

### Post by sfed on 2007-10-20
@dptxp that doesn't solve the problem.I also have a dell inspiron with an intel on board graphics card.Ubuntu loads fast but when it comes to desktop I wait about much more than feisty (20 sec or more).The screen gets orange and the mouse button has its default form.After 10 seconds it changes to another icon and after 10 seconds I see my desktop.

---

### Post by jaybombalous on 2007-10-20
> **sfed said:**
> @dptxp that doesn't solve the problem.I also have a dell inspiron with an intel on board graphics card.Ubuntu loads fast but when it comes to desktop I wait about much more than feisty (20 sec or more).The screen gets orange and the mouse button has its default form.After 10 seconds it changes to another icon and after 10 seconds I see my desktop.


exactly what I am saying, seems like each part of the desktop loads individually one waiting on the other app to load fully before trying to load another. This is seriously annoying to me, in feisty my desktop loaded quick as hell, once the music came on I could use skype within seconds. 

Now there is a huge delay. I hear music, wait... wait some more... bottom taskbar displays wait... then the icons load and the top taskbar load, wait... then it starts to load the clock and network icon which seems to be the problem, this step takes forever and completely stops skype and gdesklets from loading until after the network and clock load. Then skype and finally gdesklets loads.

compared to the 5 seconds it took to load my feisty desktop, 1 minute to load the gutsy desktop is a HUGE step backwards.

---

### Post by jaybombalous on 2007-10-20
I am almost thinking I can capture a video of it if there was a way to load a recording software outside of gnome and then capture the gnome desktop boot up process.

Don't have any idea though. :(

---

### Post by malcam on 2007-10-20
> **farueulogy said:**
> I installed it - I removed it.

7.10 takes 5 minutes just to get to the log-on screen. 7.04 takes 20 seconds.

Anyone think that's justifiable?

*PC spec in signature*

Just to say I had the same problem on my laptop and found a solution in another thread. Basically I would get a blank screen for several minutes before getting to the login screen - this has never happened to me in previous releases of Ubuntu. Here's the thread, although bear in mind you might need different details or it may be something else:

[http://ubuntuforums.org/showthread.php?t=579568&page=2](http://ubuntuforums.org/showthread.php?t=579568&page=2)

---

### Post by farueulogy on 2008-03-28
Solved - [See my final post here]("http://ubuntuforums.org/showthread.php?t=579846")

---

