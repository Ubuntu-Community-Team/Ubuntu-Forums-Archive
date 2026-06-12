---
title: "x server couldn't load"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by theycallmedolo on 2006-05-28
brand new to linux and ubuntu but i am definatly interesting in learning. i have the ubuntu livecd and everything seems to load up fine and then something pops up up saying x server couldnt load or something of that nature. i am not fimiliar with any of the command line items so here i am to get some help. also is linux for dummies a good reference item to pick up for this os?

---

### Post by Sutekh on 2006-05-28
What sort of graphics card do you have?  NVIDIA or ATI?

Unfortunately NVIDIA and ATI are not very forthcoming on how their cards work. The only way to get these cards working is to either use the manufacturers proprietry drivers or the community made free drivers. Ubuntu has a commitment to free (as in freedom) software, so they only provide free software solutions. Sadly they are often not completely up to the task, hence X server errors.

I really suggest that you check out post # 3 of this thread

[Ubuntu Forums - Live CD X Server Prob?]("http://ubuntuforums.org/showthread.php?p=935524#post935524")

The poster was able to solve their problem by using the **live-expert** function of the LiveCD. Using this method they were able to stop the auto-detection of their hardware and specify the video driver that the LiveCD uses. 

If you are able you should try to boot the LiveCD using the **live-expert** mode and choose the **vesa** driver.
[URL="http://www.ubuntuforums.org/showthread.php?t=75074"]
[/URL][ ]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by theycallmedolo on 2006-05-28
went in loaded up live expert chose vesa, a couple of other prompts came up and i wasnt to sure what to do so i think that is why it still said x server couldn't load any ideas?

---

### Post by theycallmedolo on 2006-05-28
also i have a nvidia geforce mx4000 sorry forgot to mention that

---

### Post by Sutekh on 2006-05-28
[quote=theycallmedolo]went in loaded up live expert chose vesa, a couple of other prompts came up and i wasnt to sure what to do so i think that is why it still said x server couldn't load any ideas?[/quote]
Sorry I don't really know what you should do about the other prompts.  Default/suggested values are good.
[quote=theycallmedolo]
also i have a nvidia geforce mx4000 sorry forgot to mention that[/quote]You should be able to get good support for that in Ubuntu, its just strange that the **vesa** driver *didn't* work.

After the xserver error are you left at a command line?

---

### Post by theycallmedolo on 2006-05-28
i was given the option to configure x server. i wasnt sure so i hit no then a bunch of things said stopping then i ended up at a command line i cant quite remember what it said but the last character was a $

---

### Post by Sutekh on 2006-05-28
Ok, you are at the command line.  Try to use
```
sudo dpkg-reconfigure xserver-xorg
``` - this command will reconfigure the X server (the GUI), you want to do this.  

 - You will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor. If you don't know what you should answer to these questions go with the default/suggested ones.
 
  - the important step is when you are asked to choose the video card driver for the X server choose **vesa**
 
  - once you are done try using this command```
[LEFT]sudo /etc/init.d/gdm restart[/LEFT]

```
 
  - this will restart the GNOME Display Manager, and start the GUI

[-o<

---

### Post by theycallmedolo on 2006-05-28
ok ran into a couple problems or so it said. one prompt came up that said if you see this template bug in installer also another message was -bash no job control in this shell ntu@c-71-234-191-87:~$and also vesa - no matching device station for instance busid pci:0:1:0 and pci:1:8:0, so it is official i am out of my league but i still wanna give it a shot any ideas?

---

### Post by theycallmedolo on 2006-05-28
also asked me what runlevel should be entered can i leave that blank?

---

### Post by theycallmedolo on 2006-05-29
should i get another copy of the live cd?

---

