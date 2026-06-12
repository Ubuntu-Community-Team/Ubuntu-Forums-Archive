---
title: "No signal with Ubuntu on my HDTV"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-02-29
Well I have a 32" Westinghouse HDTV. I just got my dual boot up and running. I installed the updates but did NOT install the restricted updates that it lets you know about in the top right hand corner. Well I installed the regular updates and rebooted. Now I don't have a little hint saying "Hey, you have restricted drivers you need to download" or whatever. So first off, idk where to go do install those now that it's not right there for me. So NO, i havn't installed my nVidia drivers or anything yet, mainly cuz idk how too.

Second, Ubuntu doesn't work with my HDTV. TV just says NO Signal. Now it has worked before with it but i didn't have dual boot installed properly. 

What I want is 1360 x 768 resolution on Ubuntu...but i can't exactly change it when I can't even see my screen! 

-Justin

P.S. I'll hook up my CRT monitor to change things in Ubuntu if i need too.

---

### Post by blazercist on 2008-02-29
How are you connecting the pc to the hdtv?  You probably want to install the restricted drivers they will suport TV-out and the like much better.

---

### Post by HoLLyw00dGT on 2008-02-29
VGA to VGA from my 8600gt. How do I install the restricted nVidia drivers?

---

### Post by blazercist on 2008-02-29
System>Administration>Restriced Drivers Manager Check the appropriate checkbox for your video card and close the manager.  I believe it will prompt you to restart or perhaps it will restart the X-server automatically.  Either way next time you login it should be working properly.

---

### Post by LowSky on 2008-02-29
do you have two monitors hooked up. one being your LCD TV? If so then you will need the drivers, just do what blazercist says

---

### Post by HoLLyw00dGT on 2008-02-29
Nope just the HDTV, been SWITCHING back and forth just so i can see lol. I'll give that a shot and hook my tv back up and see if it says no signal. What other things should i look to install drivers for? Windows makes it easier... lol that or i'm just not used to it.

-Justin

---

### Post by HoLLyw00dGT on 2008-02-29
Well went to restricted drivers, put in pw, it had an disabled nvidia driver, i enabled, rebooted, switched to TV, and "No Signal" I've had it on here before >_< Is there ever gonna be a time during linux you dont have a problem? lol

---

### Post by HoLLyw00dGT on 2008-02-29
Any suggestions?

---

### Post by HoLLyw00dGT on 2008-02-29
Ok, I remember when i first got my TV and used it as my monitor. I had a refresh rate of 70 hertz and i had no signal. Changed it to 60 hertz and it works amazingly. (Windows)

On my little sh1tty 15" CRT monitor that is 10 years old it says 52 or 54 hertz when i got to System, pref, resolution.

Is there a way to change the refresh rate in the code or something on my CRT, Turn off comp, plug in my LCD and then see if it works?

-Justin

---

### Post by HoLLyw00dGT on 2008-03-01
bump

---

### Post by blazercist on 2008-03-03
sorry for the wait, goto system> administration>screens and graphics and enable and configure the second screen there it shoudl recognize the tv automatically but you can adjust the settings and save your configuration there.

---

