---
title: "My screensaver won't display"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-02-10
My computer runs Ubuntu 6.10.

I have no trouble selecting a screensaver to use on my computer. The problem is, after I close the window, the computer uses a blank screen when idle. I have the "Activate screensaver when computer is idle" button checked, and I don't know what I'm doing wrong. The computer is a bit old, so is Ubuntu not displaying it because the video card isn't supported?

---

### Post by Spin Doctor on 2007-02-10
Check your powersaving settings, so your monitor is not set to turn it self off before the screensaver kicks in.

However, I have two installations of Ubunty Edgy. One of them have same behavior as yours..the screensaver will not kick in when it should...and that is the brand new computer...

---

### Post by colinnwx on 2007-02-12
Hey, i have almost exactly the same problem! i kind of figured it might be a powersaving setting, but it didn't look like there was anything option i could set under power options.

My screensaver works fine when the laptop is plugged in, but the moment i run it on battery, the screensaver doesn't display. Couldn't unset anything in power management to help the problem though.

---

### Post by dr_d on 2007-02-12
I've got the same problem. I can preview the screensavers no problem, but when the computer idles it only displays a blank screen.

my specs:
- edgy eft
- nvidia drivers

one of us should file a bug if it hasn't been done already.

---

### Post by biggles7268 on 2007-02-14
I'm having the same problem, and being a complete linux newb I have no idea what to do about it :)

---

### Post by Spin Doctor on 2007-02-16
This is interesting.
For some reason, I got the screensaver to work. Try first to deactivate your screensaver. Close down screensaver settings. Then reopen and select a screensaver and mark the activate checkbox, and close....

Try this..as I dont know exactly what I did to fix this issue.... 

Kind of nice solving a problem not trying to solve it...but harder to explain to others how to duplicate... =)

---

### Post by dr_d on 2007-02-21
hmm doesn't work... i tried playing around with it and changing as many options i could...

do you remember anything else you changed that might have fixed this? changed any display settings? installed any new packages?

cheers,
dr d

---

### Post by Spin Doctor on 2007-02-24
I remember working on my splash settings in Gconfeditor. I dont see how this could affect...but you never know. This is a weird problem, and it sucks not knowing exactly what solved it... I messed up my other ubuntu installation the  other day anyway.. so I am going to make a fresh install again in a couple of days. It will be fun to see if the screensaver will work out of the box or not... =)

---

### Post by dr_d on 2007-02-24
Yeah let us know how it goes... For me at least, Edgy screensavers dont work out of the box.

Cheers!

---

### Post by Doomedelite on 2007-02-28
Screensavers in edgy don't work more me neither, I can preview fine. ATI 9600SE

---

### Post by amgat on 2007-03-01
I had the same problem. I did as suggested - deactivated the screensaver and closed the screen saver settings page. Then opened it again and ticked off the "start automaticly" checkbox. Works OK for me now.

---

### Post by Mattallyc on 2007-03-18
Likewise my screensaver used to work fine before I activated the Nvidia driver.  Now I can view the preview but just get a blank screen when it properly kicks in. Tried turning it off and on again but to no avail.
Just tried uninstalling all screensaver programs and reinstalled just gnome-screensaver.  Didn't help at all...
Could someone who's got screensavers working with an Nvidia card post their xorg.conf file contents? It might help.
Cheers,
Matt.

---

### Post by exactopposite on 2007-03-26
i'm having the same problem. i just installed edgy on this machine a couple of days ago. i instaleld the nvidia drivers (geforce 6500) and when it's time for the screensaver to come on the monitor goes blank, but the monitor power is still on.

---

### Post by kevjaun on 2007-03-27
Same as. It works first time when I boot/restart but not thereafter. Has anyone submitted a bug?

---

### Post by chipdip on 2007-03-27
Another one bites the dust. Mine does the exact same thing.

---

### Post by C-A on 2007-03-27
I am using Kubuntu so my experience may not apply but my screensaver does not work if I have the power saving disabled but works fine with power saving enabled.

---

