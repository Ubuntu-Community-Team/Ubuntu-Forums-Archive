---
title: "&quot;no screens found&quot;"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by clarijan on 2007-07-06
Okay, first of let me say that I am very new at this and might require some step-by-step help. Second here are my specs:

Dell Inspiron e1705
Core Duo 1.86
100 Gb HD
1 Gb Ram
--
as for the video card i ran [COLOR="Blue"]"lspci"[/COLOR] and it gave me this: 01:00.0 VGA compatible controller: ATI Technologies Inc Radon Mobility X1400

Third, thanks in advance.

The Problem: After installing ubuntu with the alternate CD everything went fine. Then, when I start up the computer I get the following:

[COLOR="Red"]Failed to start the X server (your graphical interface)...etc...[/COLOR]

upon further inspection:

[COLOR="red"]"Fatal server error: No screens found"[/COLOR]

i have tried running [COLOR="blue"]"sudo dpkg-reconfigure xserver-xorg"[/COLOR] but after answer all of the questions (up to "Desired default color in bits") but then it gives me the following message:

[COLOR="Red"]xserver-xorg postinst warning: overwriting possibly-customised congifuration file; backup in /etc/X11/xorg.conf.20070206083931[/COLOR]

where do i go from here to get the desktop to come up?

---

### Post by capitalistpiglet on 2007-07-06
From the terminal type
 ```
sudo startx
```
That should bring up the gui. If not it will come back with more error messages, if that happens then post them here and someone should be able to help.

---

### Post by overdrank on 2007-07-06
> **clarijan said:**
> Okay, first of let me say that I am very new at this and might require some step-by-step help. Second here are my specs:

Dell Inspiron e1705
Core Duo 1.86
100 Gb HD
1 Gb Ram
--
as for the video card i ran [COLOR="Blue"]"lspci"[/COLOR] and it gave me this: 01:00.0 VGA compatible controller: ATI Technologies Inc Radon Mobility X1400

Third, thanks in advance.

The Problem: After installing ubuntu with the alternate CD everything went fine. Then, when I start up the computer I get the following:

[COLOR="Red"]Failed to start the X server (your graphical interface)...etc...[/COLOR]

upon further inspection:

[COLOR="red"]"Fatal server error: No screens found"[/COLOR]

i have tried running [COLOR="blue"]"sudo dpkg-reconfigure xserver-xorg"[/COLOR] but after answer all of the questions (up to "Desired default color in bits") but then it gives me the following message:

[COLOR="Red"]xserver-xorg postinst warning: overwriting possibly-customised congifuration file; backup in /etc/X11/xorg.conf.20070206083931[/COLOR]

where do i go from here to get the desktop to come up?

Hi I have not had the privilege to use that card yet but maybe this link will help
[http://ubuntuforums.org/showthread.php?t=399913&highlight=Dell+Inspiron+e1705](http://ubuntuforums.org/showthread.php?t=399913&highlight=Dell+Inspiron+e1705)
Good luck and welcome! :D

---

### Post by clarijan on 2007-07-06
after running [COLOR="Blue"]"sudo startx"[/COLOR] i get:

[COLOR="Red"](EE) No devices detected

Fatal server error:
no screens found
XIO: fatal IO error 104 (COnnection reset by peer) on X server ":0.0"
after 0 requests (0known processed) with 0 events remaining[/COLOR]

any idea where to go from here?

---

### Post by balleyne on 2007-07-06
I recently solved a similar issue, but with completely different hardware (the new Intel Santa Rosa platform, 965GM)... however, maybe my solution might help a bit in combination with some other things.

I was getting the "no screens found" error. In my case, I had to install the latest kernel to get support for my video card, download the latest driver, and reconfigure xserver-xorg to use that latest driver.

See [http://blaise.ca/blog?p=14](http://blaise.ca/blog?p=14)

(( btw, this message "
xserver-xorg postinst warning: overwriting possibly-customised congifuration file; backup in /etc/X11/xorg.conf.20070206083931" is not a problem, it's just letting you know that it's backing up your xorg file ))

HTH..

---

