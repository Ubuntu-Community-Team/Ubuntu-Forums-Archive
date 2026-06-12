---
title: "LCD monitor causes problems"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by jimgeiser on 2007-12-28
I added an LCD and was not happy with the image I was getting-too elongated. I went into the display help and saw that I could reset the configuration to what I thought I had a Dell 1706 digital. When I rebooted the screen was fine as long as it was in the Dos stage, but when it went to the Ubuntu screen started rolling up and not readable. No way to get back to change it back. Is there way to get this done in the terminal.

---

### Post by blueridgedog on 2007-12-28
Try :

dpkg-reconfigure xserver-xorg

From a terminal.

---

### Post by jimgeiser on 2007-12-28
Thanks, but stupid question- how do I stop the startup in terminal before it gets to Gnome. Once it gets to gnome it scrolls and there is no way to do anything.

---

### Post by blueridgedog on 2007-12-28
Once it boots, you can kill the xserver with CTR+ALT+Backspace.  

This should take you to a command prompt where you can try and reconfigure your Xserver.

---

### Post by jimgeiser on 2007-12-28
I never used the Terminal before. When it opens it asks for login: then when I put that in it wants my password and when I type that in nothing shows and if after i put it in and press enter it says "login incorrect" I presume this is the same pw I type in every time the program wants to change something.
Is there a good book I can get to learn all this and not bother good people like you.

---

### Post by Moop on 2007-12-28
You're not bothering anyone. 

When you log in to the terminal you use your username and the same password you use for everything else. It's normal for it not to show up when you type. It should work. :)

---

### Post by jimgeiser on 2007-12-29
Evidentially I have one of them written down wrong and it isn't PW that I use every day. Can I use the CD I down loaded and correct my installation? If I just reinstall from the CD it will definely erase some of my stuff. I probably will be ask for Login and PW there also won't I?

---

### Post by blueridgedog on 2007-12-29
Have you tried booting to recover mode (one of the options on the boot menu)?

---

### Post by jimgeiser on 2007-12-29
I made a new ISO with Ubuntu 7.10 and found that it had that option. I did it and am now in terminal mode. I just installed firefox-dbg. I tried to do what uou said in first email, but it said that the "xserver-org" was not installed. I tried to install it, but it said it could not do it-to see help and it scrolled through it so fast I could not read it. Is there a way to pause it while I read it all? or even to print it?

---

### Post by blueridgedog on 2007-12-29
When you are booting off the CD, you are not working with your real file system.

Here is how to reset your user account password so you can reconfigure your xserver.

Reboot w/out the cd.  At the grub prompt select your normal boot entry, press e to edit, arrow down to the line that starts with "kernel...", press e to edit, add the word "single" to the end of the line (after a space).  Press enter to save, them b to boot.

You will boot to a # prompt.  Enter /usr/bin/passwd XXXX where XXXX is your user name to reset your password.  

You can attempt to reconfigure your xserver at this point or reboot normally and then to through the process above.

---

### Post by jimgeiser on 2007-12-29
WOW you are terrific! Got it up and running. That reconfiguring scared me a little after my run in with the drivers, but after i read everything twice it was easy.
Thank you a thousand times! And an early HAPPY NEW YEARhttp://ubuntuforums.org/images/smilies/icon_smile.gif
:)

---

### Post by blueridgedog on 2007-12-29
Well done.  Now you can help the next person :-)

---

