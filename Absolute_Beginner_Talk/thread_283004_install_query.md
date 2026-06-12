---
title: "install query"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by vmaxchick on 2006-10-23
hi there now trying to install ubuntu from cd and have a problem well not sure if it is, seem to be staying at the windows that says prepare disk space, with only option being cancel, little circle is spinning. Clicked forward after option 1 on resize but it has been on this screen for at least 2 hours, any advice would be great, still sitting on this screen now
H

---

### Post by ReaderRat on 2006-10-23
What were you trying to do?
And tell us more about your computer....RAM,video card, hard drive(s), etc...

---

### Post by vmaxchick on 2006-10-23
just a standard installation and is ubuntu desktop downloaded yesterday and placed onto cd

here is the stage i was at
You'll then be presented with three options. This first option is ideal for users who want to set up a dual-boot (where you can choose whether you want to use Windows or Ubuntu each time you boot up your computer) but know very little about setting one up. Ubuntu will automatically shrink your Windows partition and create a new Ubuntu partition out of the free space. 

took this option and sitting with the screen above only with a cancel option thought it was starting to do this but has been on this screen for over 2 hours, disc is not moving

have gigabyte ,Athalon 210,  80 gig HD, Nvidia 5600 graphics card, 1GB ram

---

### Post by ReaderRat on 2006-10-23
Go ahead and quit the installation CTRL+ALT+DEL and then run from the LiveCD, so we can look up some things about your partitions.

---

### Post by ReaderRat on 2006-10-23
Once you have the LiveCD running, go to Applications>Accessories>Terminal and type this in the Terminal:
```
cat /etc/fstab
```
and post the output here.

---

