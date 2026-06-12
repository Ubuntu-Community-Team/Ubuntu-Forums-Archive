---
title: "HTML rendering disabled, need help getting wine to work"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by philosophicscience on 2008-03-08
I'm a newbie, so this may be getting in over my head. I'm trying to get wine, and eventually download steam and Team Fortress 2. I can't get wine to work right now, I have been following this: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) this: [http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/) 
and a few other things. I now have 'wine' under my applications, and when I launch this code:```
 wine iexplore http://appdb.winehq.com/ 
``` it brings up Wine Internet Explorer all in white with the message 'HTML rendering is currently disabled."

Where do I go from here?:confused::confused:

---

### Post by Tteddo on 2008-03-08
I would go [here]("http://www.tatanka.com.br/ies4linux/page/Main_Page") and download and install IE's for Linux. It works pretty well if you have to run IE. It's not IE7, just 5 and 6 though.

---

### Post by philosophicscience on 2008-03-08
I downloaded and installed that program, but what do I do now?

---

### Post by Tteddo on 2008-03-08
If it is installed correctly, then you should have a couple of IE links on your desktop, one for IE6 and one for IE5.

---

### Post by philosophicscience on 2008-03-09
I installed it and played around with it, but I can't get those icons on my desktop. I'm still stuck at this point.

---

### Post by Tteddo on 2008-03-09
How did you play around with it? Mine only put icons on my Desktop that I had to copy to the toolbar, menus, etc...
So, you are saying that IE works?
Instead of opening IE my way, I tried the command line like you are doing and got the following error.
[IMG]http://www.tteddo.com/temp/Gecko.jpg[/IMG]

 Have you seen that? After I hit cancel, I get the HTLML rendering error.

I am thinking you might want to uninstall wine, and install it through Synaptic (System>>Administration>>Synaptic)  so that any weird dependencies will be satisfied.

---

### Post by lswest on 2008-03-09
actually, that error is easily solved (especially with wine-doors) where you just have to go to applications-->wine-->wine-doors, find the application "Wine Gecko" and click the "install" link on the right side of the listing.  Then (after it says added to queue) click on the drop-down list next to the word "SHOW" and choose "queue". once there, make sure the wine gecko app is listed, and hit "apply" then in a few minutes it should be installed.  This process also works for any app in the list, if you're having trouble installing anything.

---

### Post by Tteddo on 2008-03-09
Wow! That wine-doors is a great find! Thanks! 
Crashed on the setup, but it seems to be working, and it will fix your problem philosophicscience.
You can get it here [http://www.wine-doors.org](http://www.wine-doors.org)

---

### Post by lswest on 2008-03-09
haha glad i could help^^

---

### Post by philosophicscience on 2008-03-10
I'm installing wine-doors right now, let's see if it can get me up and running! Thanks a ton.

---

### Post by lswest on 2008-03-10
haha okay, good luck ^^ *crosses fingers*  :P

---

