---
title: "Need to change Screen Resolution on Dell Inspiron E1505, don't know video card driver"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by sqbox on 2007-09-20
Hi,
I just recently installed Ubuntu 7.04 and it works but the screen resolution is wrong.   
Under System->Preferences->Screen Resolution, there is only one option (1400x1050) and no other choices drop down when I click on the drop down arrow.  The refresh rate is 60 Hz. 

I have tried the following command:
sudo dpkg-reconfigure xserver-xorg 

But it asks me to select a video card driver, and I have no idea what mine is or how to find out.  Can someone please point me in the right direction of determining this, and then how I can continue the process to change my screen resolution?  How do I know what resolution would best fit my screen (I don't remember the size of my laptop screen).

Thanks a lot.

---

### Post by st33med on 2007-09-20
post:
```
lspci
```
here.

---

### Post by sqbox on 2007-09-20
Thanks for your response.  I tried this, and one of the lines in the result was:

VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

I selected "ati" in the driver list, but then the configuration takes me to a screen that says "Furhter configuration will have to be done manually in the X server configuration file, "etc/X11/xorg.conf."  I tried opening this file but it's not clear to me what lines I have to change to set a certain resolution or how the video card driver I've just found is used.

Thanks in advance for any response.

---

### Post by Proximo1 on 2007-09-20
I was having issues also and I decided to install a new Nvidia Driver.  I messed up my Ubuntu OS.  So be careful and listen to the experts on the forum.  I failed to read one line and it ruined my system.
:mad:

---

### Post by sqbox on 2007-09-21
thanks for the tip. i've gotten it to work before but don't remember how.  basically i want to set the resolution so it looks normal instead of "stretched" in my screen.
thanks for any replies.

---

