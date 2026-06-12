---
title: "Dialup setup (was: Problems with Internet)"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by ynnoj on 2007-01-31
I've just installed Ubuntu on a laptop and I'm trying to set up dialup internet (that's right, dialup).  I set up a modem connection in Ubuntu and then try to get to google through Firefox.  It doesn't work.  Then, I check the connections box and it says the modem connection isn't active.  But I just activated it!  How can I fix this and get a working internet connection?

---

### Post by ieee488 on 2007-01-31
I'm still using dial-up myself, but on a desktop.

My suggestion to you to see if your modem is recognized by Ubuntu is to open up a Terminal window, then type **sudo wvdialconfig** and see what it outputs.

---

### Post by batholith on 2007-01-31
What kind of dialup modem do you have? Because they're are different fixes/setup procedures for different modems...

---

### Post by Brunellus on 2007-01-31
thread title changed to better reflect nature of problem.  

Please be advised that dial-up support with Winmodems in Linux is dicey at best...

---

### Post by housam on 2007-01-31
I've a dial-up connection working just fine with my laptop. Scan your modem by a [scanModem tool ]("http://www.linmodems.org/")to see if it is supported or not and if supported , which driver is suitable for it.

---

