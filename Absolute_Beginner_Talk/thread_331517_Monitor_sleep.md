---
title: "Monitor sleep"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by darklyndsea on 2007-01-04
Is there any way to disable the monitor turning off besides with power management preferences?  It turns off after maybe 20 minutes and moving the slider to never doesn't change that.

---

### Post by rajeev1204 on 2007-01-04
hi

Thats cos of ur monitor's inbuilt power saver feature

I dont know if it can be done in linux but in windows i think u can with the monitor installation CD

---

### Post by darklyndsea on 2007-01-05
My monitor did not come with a CD, and it turns off at the time I have set it to turn off in Windows (5 hours), since I am dual booting.

---

### Post by commonplace on 2007-01-06
I have the same problem. The monitor does not have a built-in sleep/low-power feature. I'm not sure ANY monitor does (where'd you read that?). At any rate, my monitor goes to sleep after 20 minutes regardless of the slider, which I currently have set to 'Never'.

How can power saving for the monitor be completely disabled?

/Kevin

---

### Post by TooRight on 2007-01-09
Mine does too... it never used to on Dapper; I could set it up to stay on for hours without keyboard or mouse activity and it would stay that way. Since installing Edgy, however, it shuts itself down on its own, no matter what i set it to in Kcontrol :(

Other than it being the the latest version on my comp now, the only difference is that now I am also running Beryl... I wonder if something with that is causing it.

---

### Post by deadgobby on 2007-01-09
[http://ubuntuforums.org/showthread.php?t=334479](http://ubuntuforums.org/showthread.php?t=334479)

---

### Post by TooRight on 2007-01-09
Checked that first thing when the problem started (though I had done nothing to my bios to cause it to start do this anyways)

---

### Post by darklyndsea on 2007-01-10
Changing the BIOS worked for me!

---

### Post by orb9220 on 2007-01-10
And also try and it worked for me in dapper was to 

Set screensaver to 1 min and monitor to 2min then:
wait for screensaver to kick in and move the mouse. Now go to screensaver and deactivate.
Now wait for monitor to blank at 2mins then move mouse and change back to never.

Read hear in old thread and worked for me.

Also adding  a  Option "DPMS" "OFF" in xorg.conf has also worked for some.

---

