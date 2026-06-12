---
title: "Problems with resolution"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by boyack on 2007-09-08
Hiya!


I've just installed ubuntu on my computer. It all went well the only thing is ubuntu wont let me change my resolution, I have a resolution of 1440.900 pxl but ubuntu wont let me change it from 1152.864, so all the ubuntu is wrong.

How can i change it to another resolution?


Greetings:D

---

### Post by overdrank on 2007-09-08
> **boyack said:**
> Hiya!


I've just installed ubuntu on my computer. It all went well the only thing is ubuntu wont let me change my resolution, I have a resolution of 1440.900 pxl but ubuntu wont let me change it from 1152.864, so all the ubuntu is wrong.

How can i change it to another resolution?


Greetings:D

Hi and welcome this thread may help
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
Good luck! :KS

---

### Post by boyack on 2007-09-08
thanks! but.. isn't there a more easy way of doing it, you see im totaly new on ubuntu i´ve just got a few hours but i cant understand a thing on this resolution :S

---

### Post by eapache on 2007-09-08
The difficulty in changing it is a known bug in this version. The next version (to be released in October) includes a patch so that it will include 1440x900 by default. Until then, I'm afraid there is no other way.

---

### Post by boyack on 2007-09-08
ok, thanks, and when the next version is realeased can I just update from ubuntu or do i have to download it all again?

And as i understand i have to get to the xorg.conf file to change the resolution, how do i get tothat file?

Thanks alot!

---

### Post by eapache on 2007-09-08
Yes there will be an 'upgrade' button when it comes out.

First run```
gksudo gedit /etc/X11/xorg.conf
```and enter your password. Then scroll down to the section that says 'Section Monitor', and you should see a list of resolutions. Simply add 1440x900 to that list, save, and restart.

This can break your system if you make a mistake, so if you are at all unsure of what you are doing, please request clarification.

---

### Post by overdrank on 2007-09-08
> **boyack said:**
> ok, thanks, and when the next version is realeased can I just update from ubuntu or do i have to download it all again?

And as i understand i have to get to the xorg.conf file to change the resolution, how do i get tothat file?

Thanks alot!

HI it tells you in the link I provided and remember to **_BACK UP_** your xorg
 How to edit xorg.conf file
Run in terminal or console:
Code:

sudo nano /etc/X11/xorg.conf

How ever I would recommend you using 
```
gksudo gedit /etc/X11/xorg.conf
```
Instead of sudo nano
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by boyack on 2007-09-08
hiya

thanks for all that help but where do i type the code? gksudo gedit /etc/X11/xorg.conf

---

### Post by overdrank on 2007-09-08
> **boyack said:**
> hiya

thanks for all that help but where do i type the code? gksudo gedit /etc/X11/xorg.conf

Oh sorry in the terminal located under applications, accessories, terminal :)

---

### Post by boyack on 2007-09-08
ok, I'm in the xorg.conf window  now. What do i do? :S sorry

---

### Post by overdrank on 2007-09-08
> **boyack said:**
> ok, I'm in the xorg.conf window  now. What do i do? :S sorry

Hi add the resolution you want to the lines that look like this
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
and add it to all the lines and did you **_BACK UP_** you xorg first.
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

