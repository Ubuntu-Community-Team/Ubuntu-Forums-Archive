---
title: "I would like to launch an app as a daemon at startup . . ."
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Phurious on 2007-08-15
Newbie here, so use small words.  I would like to have stunnel4, hellanzb and perhaps lottanzb run at startup *WITHOUT* me having to launch them from terminal.  Now I have seen a couple of scripts that are supposed to launch Hellanzb as a daemon, but so far I have failed miserably at adapting them to my needs.  It is important the applications launch in the order I have them listed.  They are all installed and working correctly; I can successfully launch all of them from terminal.  Can anyone help?  :confused:

TIA

---

### Post by milosz.galazka on 2007-08-15
Hello,

You can create one simple script that will run commands in selected order and then copy it to **/etc/init.d/** 
After that just run
[B]cd /etc/init.d/
update-rc.d mynewscript defaults[/B]

(Don't forget about permissions)

---

### Post by bodhi.zazen on 2007-08-15
Place those commands, in order, in ;

/etc/rc.local

no sudo needed (the script runs as root at boot)

---

### Post by Phurious on 2007-08-15
milosz.galazka - Thanks for the response!  That is what I was originally trying to do and failed miserably.

bodhi.zazen - Thank you also.  I added the commands as you suggested in your reply, but the only program that appears to have run is stunnel4.  Do I need to enter special commands for applications that run in a terminal window?  To demonstrate my ignorance, I can run "hellanzb.py" in ternminal, and see the application launch in terminal.  If I close the terminal window, it kills the application also.  What can I do to launch the application so that it will not quit when the terminal window is closed?  I *THOUGHT* the answer was along the lines of what milosz.galazka had suggested, but I may have had the command incorrect.

Thanks for you help!

---

