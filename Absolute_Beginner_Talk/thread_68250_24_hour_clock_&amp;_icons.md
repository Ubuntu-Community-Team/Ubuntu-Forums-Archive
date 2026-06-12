---
title: "24 hour clock &amp; icons"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by clueo8 on 2005-09-22
I cannot find out how to change the clock to a 12 hour format with AM PM in KDE Kubuntu.

Also, I'm trying to set an File Icon (ex. *.mp3) to an external .png file, it keeps saying that it has to be local.  How can I get around this?

---

### Post by mlomker on 2005-09-22
[QUOTE=clueo8]I cannot find out how to change the clock to a 12 hour format with AM PM in KDE Kubuntu.[/quote]

Go into the Control Center, look under Regional & Accessibility, click on Country/Region & Language.  Click on the Time & Dates tab and change the **Time format** option.  

That's one of the first things that I do on a new install, myself. 

> 
Also, I'm trying to set an File Icon (ex. *.mp3) to an external .png file, it keeps saying that it has to be local.  How can I get around this?

Do you mean a png image out on the Internet?  I don't think you can do that.  You'd have to download the image and save it somewhere on your computer first.

---

### Post by clueo8 on 2005-09-22
It is saved on my computer... But Its prolly cause I didnt open the control center with su rights... is there a way to do this?

One problem I'm having now is that my clock is in the wrong time zone, and It is set right! to America/NYC Eastern.  I go to "Adjust Date & Time" it will ask me for my root password and I enter it correctly and nothing is displayed.

---

### Post by mlomker on 2005-09-22
Did you install Hoary or Breezy?  The control panels in Breezy are still broken.  The inability to set the time zone properly is one of the reasons that I went back to Hoary.

You can try **kdesu kcontrol** on the run line.

---

### Post by clueo8 on 2005-09-22
not sure which one I have, how can I tell?  I've been seeing it ask me for the Hor** CD.  I got it running by right clicking on the clock and changing the "show time zone" Then everything else started...

Alot of the time,  when I enter su mode or sudo in a terminal, its saying my user name is UID 1000 and not 0 but yet it still opens up my command in super user mode...

---

