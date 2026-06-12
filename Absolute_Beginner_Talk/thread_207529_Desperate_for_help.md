---
title: "Desperate for help"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Macmac on 2006-07-02
Hi, I'm new to the forum and absolutely new to Linux. Sorry if this post is long, but I try to explain what happened.
Yesterday I got a new entry level computer with the Linux the CD (Ubuntu 5.10). I installed Linux and everything went well, except when it tried to install something ending on "-jpeg" (sorry, can't remember the name). Now all I've got is a black screen with white type. Is that normal? I can't use it. I can't get to a desktop.
*I did not install the monitor driver.* I thought it would prompt me to do that.
Now I can't install the driver. I have no idea how to run the monitor CD-ROM from Linux anyway.
Could the problem be something called an Xserver?
I typed the following command: "sudo dpkg-reconfigure xserver-xorg" (I don't know what it is, but I found it on the web.) It went through many steps and then just gave a warning message ("possible overwrite" or something).
I'm not sure, but I think Linux does not see my monitor. How do I get Linux to work? How do I get to a desktop so that I can use my computer?
All help desperately appreciated.
Macmac

---

### Post by user1397 on 2006-07-02
[quote=Macmac]Hi, I'm new to the forum and absolutely new to Linux. Sorry if this post is long, but I try to explain what happened.
Yesterday I got a new entry level computer with the Linux the CD (Ubuntu 5.10). I installed Linux and everything went well, except when it tried to install something ending on "-jpeg" (sorry, can't remember the name). Now all I've got is a black screen with white type. Is that normal? I can't use it. I can't get to a desktop.
*I did not install the monitor driver.* I thought it would prompt me to do that.
Now I can't install the driver. I have no idea how to run the monitor CD-ROM from Linux anyway.
Could the problem be something called an Xserver?
I typed the following command: "sudo dpkg-reconfigure xserver-xorg" (I don't know what it is, but I found it on the web.) It went through many steps and then just gave a warning message ("possible overwrite" or something).
I'm not sure, but I think Linux does not see my monitor. How do I get Linux to work? How do I get to a desktop so that I can use my computer?
All help desperately appreciated.
Macmac[/quote]what do you mean you installed a file ending in jpeg?  that's a picure format, as in a picture from a digital camera.  that is not something that you install.  sorry if I seem rude, i'm just wondering how you could install a jpeg file!  

about your problem, did you backup any important data you had?  if you didn't have any imp. data, or you just have no data, why not just reinstall, but don't install that special file that broke your computer!!

---

### Post by Macmac on 2006-07-02
Thanks for the answer, Erik
The file I mentioned was just something that was part of the installation process. I have no idea if it really is a photo or what it is. I tried reinstalling. It's a new computer - there's no data on it that I want. The same thing just happened again. When I switch on the computer now, I get to a login screen. I really want to get to a desktop.

---

### Post by user1397 on 2006-07-02
[quote=Macmac]Thanks for the answer, Erik
The file I mentioned was just something that was part of the installation process. I have no idea if it really is a photo or what it is. I tried reinstalling. It's a new computer - there's no data on it that I want. The same thing just happened again. When I switch on the computer now, I get to a login screen. I really want to get to a desktop.[/quote]wait you got to a login screen?  is it colorful and does it say ubuntu or is it all black and white?

---

### Post by nanotube on 2006-07-02
[QUOTE=Macmac]Hi, I'm new to the forum and absolutely new to Linux. Sorry if this post is long, but I try to explain what happened.
Yesterday I got a new entry level computer with the Linux the CD (Ubuntu 5.10). I installed Linux and everything went well, except when it tried to install something ending on "-jpeg" (sorry, can't remember the name). Now all I've got is a black screen with white type. Is that normal? I can't use it. I can't get to a desktop.
*I did not install the monitor driver.* I thought it would prompt me to do that.
Now I can't install the driver. I have no idea how to run the monitor CD-ROM from Linux anyway.
Could the problem be something called an Xserver?
I typed the following command: "sudo dpkg-reconfigure xserver-xorg" (I don't know what it is, but I found it on the web.) It went through many steps and then just gave a warning message ("possible overwrite" or something).
I'm not sure, but I think Linux does not see my monitor. How do I get Linux to work? How do I get to a desktop so that I can use my computer?
All help desperately appreciated.
Macmac[/QUOTE]
so you only get the black console eh. that's a pretty common complaint. you can go to the third link in my sig (the faq), and find the entry about your specific problem.

---

### Post by Ptero-4 on 2006-07-02
packages ending in -jpeg are the libraries used to create and use jpeg picture files. As for the command you talk about. It overwrites the xorg config file (which probably got misconfigurated or damaged) with whatever settings you set.

---

### Post by Macmac on 2006-07-02
Yes, I get a login. It's just black and white. It says:
"Ubuntu 5.10 'Breezy Badger' <the computer name I chose> tty1
"<my computer name> login: "
When I login with my username and password, it tells me about last login, free software and no warranty. Then it writes: "<my login @ my computer>: ~$"
That's all.

---

### Post by Macmac on 2006-07-02
nanotube, I looked at your FAQ and found the command "startx". When I try that, it says: "Fatal server error: no screens found".
Let me rephrase my question: How do I install my monitor driver? How do I run the CD-ROM?
Thanks for the help so far!

---

### Post by 3rdalbum on 2006-07-02
Type that command you mentioned again. This time, when it asks you if you want to use video card autodetection, say NO. It will ask you to select a driver to use. Select the one called "vesa".

When it asks you for monitor autodetection, say No again. Choose "Simple" set up, and then select the size of your monitor. If it gives you that warning that you mentioned, just accept it.

At the command line, type "sudo reboot" and then when you restart, you should get the proper login screen.

---

### Post by PingunZ on 2006-07-02
3rdalbum, I can be wrong ( I probably am ) but doesn't he has to type ```
sudo dpkg-reconfigure xserver-xorg
```
before that ? 
So macman, if the trick of 3rdalbum didn't work try that command and then use the setting 3rdalbum told you ;)

Grtz PingunZ

---

### Post by Macmac on 2006-07-02
3rdalbum & pingunz, I tried your suggestions.
I typed: "sudo dpkg-reconfigure xserver-xorg" and did what you said.
The error message I get, is:
"xserver-xorg postinst warning: overwriting possibly-customised configuration file: backup in /etc/X11/xorg.conf.200603300307"
And it just throws me back to a command line.
Then I typed "sudo reboot" and I'm just back where I were - black screen, white type.
Can someone please tell me how to install my monitor driver from CD-ROM.
Still desperate. Macmac

---

