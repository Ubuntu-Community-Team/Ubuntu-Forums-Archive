---
title: "I Want A Higher Resolution Than 1024x768"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by everyusernameistakendamn on 2006-08-17
I am new to linux and I figure out the basics and now I want a resolution higher than 1024x768 but in the screen resolution preferences there is nothing higher, on windows xp I can go up to 1280x1024 and even higher, but I like it at 1280x1024, but in Screen Resolution Preferences I cant go higher than 1024x768. I have a S3 UniChrome Pro integrated graphics thats built into my MSI PM8M2-V P4 Motherboard, I am running Ubuntu 64-Bit Version 6.06 LTS. Also does anyone know how I can get Adobe Flash for 64-Bit Linux because I installed it on 32bit but it says its not compatible with 64. I have no clue how to use commands and shit, I can pull up terminal but thats about all, I tried to read some of the shit other people have posted but it confuses the hell out of me. I can figure just about anything out if someone explains it other than just posting it without details. Also I my sound isnt working, it says its unable to connect to the sound server, but it shows my sound card and everything in Sound properites, VIA 8237, but nothing works. Thanks to anyone who helps me, $15 Via Paypal will go to the first person who can help me get everything working. Anyone can email me at [email]got.bass.69@gmail.com[/email].

---

### Post by IYY on 2006-08-17
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

Basically, you need to edit the file /etc/X11/xorg.conf and add the resolution there, in the screen section.

---

### Post by arkham on 2006-08-17
The low resolution is probably due to the fact that your monitor and/or graphics card is not set up right.  I can probably help, but I'll need a little more information.  Run the following commands and include the output of each in your next post (or PM me):

1. lspci
2. cat /etc/X11/xorg.conf

In addition to that, supply your monitor make and model.

In terms of getting the sound working the above info will help there too.  Finally, for Flash installation and everything else, I advise everyone to use Automatix - my girlfirend was a complete noob and she had everything working in under haf an hour:

[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

