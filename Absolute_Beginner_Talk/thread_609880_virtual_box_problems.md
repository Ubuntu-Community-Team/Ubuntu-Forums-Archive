---
title: "virtual box problems"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-11-11
I am trying to run virtual box, but it says
The virtual box kernal driver is not avaliable for the current user
make sure the user has write permissions for /devvboxdr by adding them to the vboxusers group

What should i do? How should i do it?
Thanks

---

### Post by quinnten83 on 2007-11-11
go to systems>administration>users and groups
type your administrator password
select manage groups,look for the group VBOXUSERS,
select properties and check the box in front of your user name.

All done, close and save if necessary.

---

### Post by overdrank on 2007-11-11
> **Falc7 said:**
> I am trying to run virtual box, but it says
The virtual box kernal driver is not avaliable for the current user
make sure the user has write permissions for /devvboxdr by adding them to the vboxusers group

What should i do? How should i do it?
Thanks

HI and had some trouble installing last nite, you may try this link
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
It worked for me just a min ago and then user manual is located there too. Good luck! :KS

---

### Post by Falc7 on 2007-11-13
thanks guys, it worked, but i've run into another problem

it says cannot read from the boot medium, system halted

Do i need the OS's installation cd to be in, in order to run the OS?

---

### Post by maybeway36 on 2007-11-13
Either that or an ISO of the OS should be mounted.

---

### Post by Falc7 on 2007-11-14
okay, i have an iso of windows xp, i mounted it using gmount.
Then started the virtual box, i get this message

PIIX3 cannot attach drive to the secondary master
VBOX status code: -102 (VERR_FILE_NOT_FOUND)

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

What should i do?

---

