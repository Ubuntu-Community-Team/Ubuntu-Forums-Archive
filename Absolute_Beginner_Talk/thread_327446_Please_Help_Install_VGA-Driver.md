---
title: "Please Help Install VGA-Driver"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by bkhaoui on 2006-12-29
Hello Everybody :-),

after using Microsoft for years i decided to switch to Linux - so i installed Kubuntu and everything goes fine (the installation process) - but here is now the prob. of a newbie ;-)
I am using a HP Omnibook XT1000 with integrated S3 Twister graphic chipset - i taught (K)ubuntu will set the display correct, but i just get a "small" resolution 1024x768 - so i can just see a small "window" - trying to change the resolution doesnt work, because this is the largest. Kubuntu uses the vesa-driver and doesnt let me change another driver. Can u pls give me a solution how to solve the problem? Any advice is welcome!
Pls excuse my poor english - germans doesnt speak english very well ;-)

Best regards,
Brahim

---

### Post by pseudonym on 2006-12-29
> **bkhaoui said:**
> I am using a HP Omnibook XT1000 with integrated S3 Twister graphic chipset - i taught (K)ubuntu will set the display correct, but i just get a "small" resolution 1024x768 - so i can just see a small "window" - trying to change the resolution doesnt work, because this is the largest. Kubuntu uses the vesa-driver and doesnt let me change another driver. Can u pls give me a solution how to solve the problem? Any advice is welcome!
Hi,
What you can try is this -
1. Press Ctrl+Alt+F1 to exit from the graphical environment.
2. Login with your user name and password.
3. Type 'sudo /etc/init.d/kdm stop to shut down your display manager.
4. Type 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg_bkup.conf' to backup your video configuration file.
5.Type 'sudo dpkg-reconfigure xserver-xorg' to change your video settings.
6. when asked to 'automatically detect graphics card' (or similar), choose 'No' and enter the name manually (not that important) and then the driver name (very important) - for your graphics it should be 'savage' .('s3' will probably also work but it is the legacy driver for these chips).
7. Then answer all the other questions according to how they apply to your graphics card and monitor.
8. when finished, type 'sudo /etc/init.d/kdm start' and log back in to your new video settings. :)
9. If it doesn't work type 'sudo cp /etc/X11/xorg_bkup.conf /etc/X11/xorg.conf to re-instate your original video configuration file. Then repeat step 8 and report back here to let us know what happened.

> **bkhaoui said:**
> Pls excuse my poor english - germans doesnt speak english very well ;) 
Kein Problem. Es war alles recht verständlich. Und mein Deutsch ist ja auch nicht immer perfekt! :)

---

### Post by bkhaoui on 2006-12-29
Hello :-)

thx a lot for the quick reply (i am very impressed) - i will give it a try and report as soon as possible ;-)

Best regards,
Brahim

P.S.: Dein Deutsch ist sehr gut! :-)

---

### Post by pseudonym on 2006-12-29
> **bkhaoui said:**
> Hello :-)

thx a lot for the quick reply (i am very impressed) - i will give it a try and report as soon as possible ;-)
for future reference, someone has written a very good HOWTO [here]("http://www.ubuntuforums.org/showthread.php?t=83973&highlight=screen+resolution"). It covers pretty much everything.

> **bkhaoui said:**
> P.S.: Dein Deutsch ist sehr gut! :-)
Danke! Ich wusste, irgendwann würde mich das Deutschlernen bezahlt machen! :D

Willkommen bei Ubuntu! :D

---

### Post by bkhaoui on 2006-12-29
Hello pseudonym,

it works :-) - thanks a lot for ur support!
The first step is done - now it is up to me to learn linux ;-)

Best regards,
Brahim

---

### Post by pseudonym on 2006-12-29
> **bkhaoui said:**
> Hello pseudonym,

it works :-) - thanks a lot for ur support!
The first step is done - now it is up to me to learn linux ;-)

Best regards,
Brahim
It's a pleasure, Brahim :)

Noch ein Tipp (auf Deutsch wenn ich so will, denn Übung macht der Meister :) ) -

Natürlich stehen wir im englischen Forum immer bereit zur Hilfe, aber, falls Du es noch nicht weisst,  vielleicht würdest Du dich auch für [diese Seite]("http://www.ubuntuusers.de/") interessieren - das offizielle deutsche Portal für Ubuntu Linux. :)

Alles Gute! :)

---

