---
title: "problems with audacity"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-07-10
hi, i have just started to use audacity but i need some help or suggestions because i have a problem with the audio. every time i record while playing my guitar, it goes fine but when i play it, a high pitch noise is present during the recording.  Any suggestions?

---

### Post by expatCM on 2007-07-10
If you use another package other than Audacity, presumably the high pitch sound is still present?

Are the guitar / amp and computer properly grounded?

Does your computer have an internal microphone?  Is that switched off?

---

### Post by davidsrsb on 2007-07-10
there is an application called baudline that is useful for showing the spectrum of the input

---

### Post by ramjet_1953 on 2007-07-10
What your problem is, is that Audacity is basically an OSS package and most new distributions use ALSA.

OSS and ALSA are the packages that control the audio on your system.

However, do not despair, there is a package that you can download that will fix the problem.

Copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get install alsa-oss[/COLOR]

Then when you start Audacity, start it with the command:

[COLOR="Red"]aoss audacity[/COLOR]

Viola! Audacity now behaves itself!

To make the startup command permanent, just go into [COLOR="Blue"]System>Preferences>Main Menu[/COLOR] and edit the startup command for [COLOR="Blue"]Audacity[/COLOR].

Regards,
Roger :cool:

---

