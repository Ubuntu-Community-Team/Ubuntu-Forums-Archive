---
title: "Ubuntu 6.10, how do i install ATI video card drivers?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Blue Eagle on 2007-05-21
I downloaded a driver from the ATI website. Now I have a .run file and no clue what to do with it.

---

### Post by overdrank on 2007-05-21
> **Blue Eagle said:**
> I downloaded a driver from the ATI website. Now I have a .run file and no clue what to do with it.

HI may I ask what is the model of the video card you are trying to install?

---

### Post by Blue Eagle on 2007-05-21
ATI x1800

---

### Post by overdrank on 2007-05-21
> **Blue Eagle said:**
> ATI x1800

Hi than I would suggest Envy
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Hope this helps and good luck! :popcorn:

---

### Post by Blue Eagle on 2007-05-21
I tried Envy, now linux won't boot.

---

### Post by overdrank on 2007-05-21
> **Blue Eagle said:**
> I tried Envy, now linux won't boot.

Did you get a error message?

---

### Post by Blue Eagle on 2007-05-21
No, it just locks up at the end of the loading progress bar.

This was a fresh ubuntu install, did I need to install something else before I ran envy?

Also, can I do something akin to a system restore to repair linux?

---

### Post by overdrank on 2007-05-21
> **Blue Eagle said:**
> No, it just locks up at the end of the loading progress bar.

This was a fresh ubuntu install, did I need to install something else before I ran envy?

Also, can I do something akin to a system restore to repair linux?

Yes you can boot to recovery mode and enter the command *sudo dpkg-reconfigure xserver-xorg* Hope that helps !:(

---

### Post by Blue Eagle on 2007-05-21
It said something about xserver.org not being installed. Then it beat me up and stole my lunch money.

I think I just bought a ticket to reinstall town.

---

### Post by overdrank on 2007-05-21
> **Blue Eagle said:**
> It said something about xserver.org not being installed. Then it beat me up and stole my lunch money.

I think I just bought a ticket to reinstall town.

I am truly sorry for any problems I may have caused. I am running a X300 on edgy now and I used Envy to get it going along wit h beryl. My Apologies:(.

---

### Post by Blue Eagle on 2007-05-21
I probably overlooked something. Don't worry about it.

---

### Post by overdrank on 2007-05-22
> **Blue Eagle said:**
> I probably overlooked something. Don't worry about it.

HI if you have not reinstalled yet you can try the backup of your xorg
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
Hope this helps!:popcorn:

---

### Post by myoungf1 on 2007-05-22
Here is how I got the ATI .run installer to work:

open a terminal window and type sudo bash ./(the name of the file here)

It should after that extract all the necessary .deb files to install.

The three that are a must are the xorg-driver-fglrx fglrx-kernel-source and the fglrx-amdcccle files.

Once the files are installed go back to a terminal window and do the following

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

sudo shutdown -r now

Hope this helps

---

