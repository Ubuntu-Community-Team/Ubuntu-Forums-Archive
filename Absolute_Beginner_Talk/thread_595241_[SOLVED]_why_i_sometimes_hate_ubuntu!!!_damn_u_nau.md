---
title: "[SOLVED] why i sometimes hate ubuntu!!! damn u nautilus"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-10-28
ok now that i've got your attention :) i love ubuntu but sometimes i hate the fact that i dont know enough to fix stuff i've broken. 

heres my problem: after playing around with emerald themes and window manager themes i finally got  an appearnce setting that i liked so happy me :) but after next reboot i found out that i screwed up again .. thx me. 

i dont have nautilus anymore :confused::confused::confused: at least i'm guessing that 

```
ap@alita:~$ ps aux |grep nautilus
ap        7070 86.4  3.3 149040 68852 ?        R    16:15 299:37 nautilus --no-default-window --sm-client-id default2
ap        7190  0.0  0.0   2660   896 ?        S    16:15   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
ap        7720  0.0  0.4  30764  8384 ?        S    16:48   0:00 nautilus --no-default-window --sm-client-id default2
ap        7944  0.0  0.4  30764  8388 ?        S    16:49   0:00 nautilus --no-default-window --sm-client-id default2
ap        8275  0.0  0.4  30764  8388 ?        S    16:53   0:00 nautilus --no-default-window --sm-client-id default2


ap        8410  0.0  0.4  30764  8400 ?        S    16:54   0:00 nautilus --no-desktop file:///home/ap
ap        8452  0.0  0.4  30764  8404 ?        S    16:56   0:00 nautilus --no-desktop file:///home/ap
ap        8503  0.0  0.4  30768  8400 ?        S    17:01   0:00 nautilus --no-desktop computer:
ap        9017  0.0  0.4  30764  8400 ?        S    18:41   0:00 nautilus --no-desktop file:///media/sda1
ap        9317  0.0  0.4  30764  8388 ?        S    19:43   0:00 nautilus --no-default-window --sm-client-id default2
gg       10412 87.8  2.8 123008 58788 ?        R    19:50 116:04 nautilus --no-default-window --sm-client-id default2
gg       10482  0.0  0.0   2660   896 ?        S    19:50   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
gg       10868  0.0  0.4  30768  8388 ?        S    19:52   0:00 nautilus --no-default-window --sm-client-id default2
ap       11782  0.0  0.4  30768  8388 ?        S    19:56   0:00 nautilus --no-default-window --sm-client-id default2
gg       12941  0.0  0.4  30764  8388 ?        S    20:17   0:00 nautilus --no-default-window --sm-client-id default2
gg       13087  0.0  0.4  30764  8400 ?        S    20:18   0:00 nautilus --no-desktop file:///home/gg
ap@alita:~$ 

```

i cant rightclick my desktop (no menu shows up ) i cant open any folders from menu home computer documents or anything.

files that are on the desktop are not displayed :confused:

everything worked fine before and i can still do everything like open firefox (as im posting here) but no nautilus at all no windows nothing .. so im stuck with terminal at the time which is ok but not great...

**[COLOR="Red"]!!! nautilus is not broken i even reinstalled it[/COLOR]** if i create a new user and login to that account i've got my desktop back and nautilus works just fine. i just dont want to reinstall all programs and change my settings again. 

here's some screenshots of what happens when in log in (see below) there should be harddrives and files on the desktop but nothing even clicking the log out button does not bring up the logout screen its like the desktop (black) is on the highest z-level somehow

**[COLOR="Red"]STUFF I DID [/COLOR]**
i copied the .themes directory to a new user account from my existing messed up account .. and the new user account was messed up as well.. so i thought well just delete the .themes folder and your good to go .. but nooooo nothing happend i just dont get it

---

### Post by juanlu on 2007-10-28
hello,

have you tried to delete the configuration folder for nautilus? It should be /home/your-user/.nautilus. I don't remember now if this is exactly this way because I'm on kde now, but if you have this folder deleting or renaming it will make nautilus to start with default configuration.

I hope it works for you

---

### Post by daimaru on 2007-10-28
thanks but no change still black screen... the thing is i get the black screen then i go to preferences appearance and suddenly my background is there again , but still no files or folders . i just dont get it how can i have messed up my account just by changing some stuff ín the themes :confused:

---

### Post by Wiebelhaus on 2007-10-28
lol , you pwn'd yourself.



have you tried reinstalling Nautilus?

---

### Post by meborc on 2007-10-28
edit: ignore me... i misread :$

---

### Post by daimaru on 2007-10-28
> **sx66gns said:**
> lol , you pwn'd yourself.



have you tried reinstalling Nautilus?

yeah i guess your right , im going to sleep on it and if no one has found an answer im going to close the thread and start reinstalling stuff . damn...

yes i did reinstall nautilus : no good

---

