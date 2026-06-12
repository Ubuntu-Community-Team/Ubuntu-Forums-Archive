---
title: "Video card drivers not working?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by xsabrewulf on 2007-10-19
I did the sudo apt-get install xorg-driver-fglrx

and it installed some stuff


when i do sudo aticonfig --initial
sudo aticonfig --overlay -type=Xv

it gives me a cant find /lib/ something..


i even went to restricted drivers and enabled. when I reboot it comes up with a prompt and says i need to run in LOW GRAPHICS MODE


i have ati X1900xt and I only have 2 choices of res... 800x600 and 640x480

---

### Post by Blara on 2007-10-19
same problem here, I managed to get gutsy to display 1280x1024 by clicking the "Configure..." button and choosing LCD Flat Panel 1280x1024. (or it might have been in ubuntu under System -> Administration -> Screens and Graphics) and a reboot.

But still haven't got TV out to work, or to use the correct graphics driver (it's using Vesa driver) I have a ATI Radeon x9600 card, but when I select ATI radeon in the screens and Graphics and reboot it still uses the vesa, very annoying. Anyone have any idea what I can do to make it work?

---

### Post by xsabrewulf on 2007-10-19
Anyone?

---

### Post by VON_CAPO on 2007-10-19
> **xsabrewulf said:**
> Anyone?
The best solution is "Envy" ---> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download envy_0.9.8-0ubuntu8_all.deb, install it, then go to "System Tools/Envy".

It will download the right driver for your card and it will install it automatically. 

Reboot and you're done. :)

_**EDIT:**_ I used it this morning after I made a fresh installation of GUTSY.
        I've got a NVIDIA 7800GS and it is running at 1920x1200 without any configuration. :)

[[IMG]http://img100.imageshack.us/img100/6875/screenshotcz3.th.png[/IMG]](http://img100.imageshack.us/my.php?image=screenshotcz3.png)

**_SECOND EDIT:_** Before to install Envy, you must enable all the repositories in the "Synaptic Package Manager" and to click "RELOAD".
                       
Otherwise, Envy will complain that the dependencies are not satisfiable.

Obviously, you must be connected to internet to do this.

---

### Post by ghostchamber on 2007-10-19
> **VON_CAPO said:**
> The best solution is "Envy" ---> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download envy_0.9.8-0ubuntu8_all.deb, install it, then go to "System Tools/Envy".

It will download the right driver for your card and it will install it automatically. 
Ok, I just did a fresh install yesterday, and I can't get Envy to run.  I get the following error message:

"Error: Dependency is not satisfiable: xserver-xorg-dev"

Yes, I'm still a huge Linuxs n00b.  What do I need to do?

---

### Post by VON_CAPO on 2007-10-19
Before to install Envy, you must enable all the repositories in the "Synaptic Package Manager" (Settings/Repositories/Ubuntu Software) and then, to click "RELOAD".

Otherwise, Envy will complain that the dependencies are not satisfiable.

Obviously, you must be connected to internet to do this.

---

### Post by xsabrewulf on 2007-10-19
Wow this is not working for me.


I installed Envy and everything installed, no errors or anything.

I reboot the PC and same thing... its put back into low graphics mode.

then i went into my restricited drivers and and clicked on ENABLE then rebooted.


once I reboot i get a black screen. nothing comes up. now I dont know how to roll back drivers or anything...

the PC doesnt lock up because with the black screen I type in my user name and password and then the HDD access like it actually loaded my desktop. just cant see anything.


my LCD doesnt lose connection either...

any advice?

---

### Post by VON_CAPO on 2007-10-19
Bump :confused:

---

### Post by VON_CAPO on 2007-10-19
Do you see on the left botton corner of your screen "Sessions"?

---

### Post by xsabrewulf on 2007-10-19
nope complete black screen

---

### Post by VON_CAPO on 2007-10-19
> **xsabrewulf said:**
> 

the PC doesnt lock up because **_with the black screen I type in my user name and password_** and then the HDD access like it actually loaded my desktop. just cant see anything.


my LCD doesnt lose connection either...

any advice?
If you see the field to input "User Name and Password" you should see "Sessions" on that corner. 8-)

---

### Post by xsabrewulf on 2007-10-19
i typed it in with a black screen

i couldnt see the fields


then my hdd started reading like crazy so i assume the desktop loaded

---

### Post by VON_CAPO on 2007-10-19
I'm afraid you need a guy wiser than me. (a "X Server" specialist). :(

---

### Post by VON_CAPO on 2007-10-19
> **xsabrewulf said:**
> I did the sudo apt-get install xorg-driver-fglrx
and it installed some stuff
when i do sudo aticonfig --initial
sudo aticonfig --overlay -type=Xv
it gives me a cant find /lib/ something..
i even went to restricted drivers and enabled. when I reboot it comes up with a prompt and says i need to run in LOW GRAPHICS MODE
I have ati X1900xt and I only have 2 choices of res... 800x600 and 640x480

I think it was here when you messed up your system.
Why you do not try a fresh install and then try Envy again? :)

---

### Post by xsabrewulf on 2007-10-19
what would be the best way to get rid of Ubuntu and reinstall without messing up the boot loader?

because i have vista and XP on this as well

---

### Post by VON_CAPO on 2007-10-19
> **xsabrewulf said:**
> what would be the best way to get rid of Ubuntu and reinstall without messing up the boot loader?

because i have vista and XP on this as well

In theory, it sounds easy to reinstall Ubuntu, but the trickiest part is when you have manually to use the partitioner... and you have 3 or more partitions.

I think it would better if you open a new thread ask help to reinstall it. :)

---

### Post by xsabrewulf on 2007-10-19
Well it worked!!!!

thanks EVERYONE for their help...


I am now at my 1440x900 res :)

now...

what are some MUST have APPS?

and whats the point of the "Desk 1 and Desk 2" on the bottom right?

---

