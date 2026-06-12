---
title: "help I crashed X server"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by POET250 on 2005-06-24
ok it started when i was trying to get my mouse working properly using dyle's instructions in this thread [http://www.ubuntuforums.org/showthread.php?t=28374&highlight=button](http://www.ubuntuforums.org/showthread.php?t=28374&highlight=button)

and I miss understood the instructions and placed these lines of code "#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" &
exec imwheel -k -b "67" &
exec $REALSTARTUP"  under the sessions>start programs editor under the system tab on the top bar.

  and now when i try to boot into linux a popup tells me that X server cannot run and i'm stuck in text only (*evil*) and i'm not able to fix it
PLEASE HELP  i would like to get back to learning linux and get away from using xp

---

### Post by intangible on 2005-06-24
Here ya go:

Log in to the text console under the username you use for X, and try this:
**mv ~/.gnome2/session-manual ~/.gnome2/session-manual.old**

---

### Post by POET250 on 2005-06-24
intang i did try after i logged in i input mv ~/.gnome2/session-manual ~/.gnome2/session-manual.old

and in response the system told me there was no such directory as /.gnome2/session-manual

---

### Post by intangible on 2005-06-24
Do you see the login screen for the system or do you have it setup to log directly into a user account?

If you see the login screen, try "Gnome Safe".

Otherwise, do this and give me the output:

**cd ~/.gnome2**
**ls -l**

The file "session-manual" is what holds all your manually specified startup programs, I'm not sure why it would give you a "File not Found" error.

---

### Post by POET250 on 2005-06-24
*intang when it boots i get the testing but when the tests are done there is no graphical log in screen it just appears in text at the bottom of the test results
and after i logged in i executed these commands cd ~/.gnome2
ls -l

and here is the output
total 48
drwx-----           2     4096     2005 06 20   02:41     accels
-rw-r--r--           1     1164     2005 06 22   01:08     backgrounds.xml
drwx-----           2     4096     2005 06 19   22:50    file-roller
-rw-r--r--           1         68     2005 06 20   03:09    gedit-2
-rw-r--r--           1       265     2005 06 22   03:09    gedit_metadata.xml
drwx-----           2     4096     2005 06 19   22:39    keyrings
-rw-r--r--           1         75     2005 06 22   01:12    main
drwxr-xr--         2     4096     2005 06 19   22:39    nautilus-scripts
drwx-----           3     4096     2005 06 19   22:39    panel2.d
-rw-r--r--           1       318     2005 06 22   21:53    session-manual.old
drwxr-xr-x        4     4096     2005 06 19    22:39    share
-rw-r--r--           1         34     2005 06 20    03:09    yelp

---

### Post by intangible on 2005-06-24
tests?  What tests, does it say something about hard drive or disk tests?

---

### Post by POET250 on 2005-06-24
test kinda like POST but for ubuntu (preboot tests or unpacking) and the hard drive works just fine.  it is a 120 gig with 2 60 gig partitions- 1 for xp and the other for ubuntu.  i am currently running xp to get ne thing done since ubuntu is down

---

### Post by POET250 on 2005-06-26
well if i can't get it working in the next 2 days i'll just reinstall ubuntu

---

### Post by monchichi on 2005-06-26
The problem is with the x-server config, not gnome. Run the following to check for relevant text messages: ```
cat /var/log/Xorg.0.log | more
``` It will give a lot of output but it should be pretty obvious what the error is related to, maybe something to do with xmodmap.

if you have to, run the following to create a new xorg.conf (which resides in /etc/X11/):
```
sudo Xorg -configure
```

---

### Post by POET250 on 2005-06-27
*monchichi well it seems not to have that log but when i tried (sudo Xorg -configure) multiple times it responded with sum thing along the lines of configure failed don't have graphics drivers or the such so i'm just gonna reinstall

---

