---
title: "Restarting X-server fails"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Papi-KB7VGW on 2007-07-10
I have a problem that when I try to restart X-server, it just hangs.  None of the tty terminals will come up.  I end up doing a hard shutdown and restart.  I searched the forum and tried the alt-sysrq-k but that didn't work either.  Does anyone have any ideas?  Running a Dell E1505N  almost forgot the syslog output  what ever the accessibility registry is appears to me to be the problem...

syslog after ctrl-alt-bksp
Jul  9 20:11:33 tkl-laptop gdm[5177]: Error reinitilizing server
Jul  9 20:11:37 tkl-laptop gdmgreeter[12159]: The accessibility registry was not found.
Jul  9 20:12:51 tkl-laptop init: tty3 main process (4508) killed by TERM signal
Jul  9 20:12:51 tkl-laptop init: tty4 main process (4503) killed by TERM signal
Jul  9 20:12:51 tkl-laptop init: tty5 main process (4504) killed by TERM signal
Jul  9 20:12:51 tkl-laptop init: tty2 main process (4506) killed by TERM signal
Jul  9 20:12:51 tkl-laptop init: tty1 main process (4510) killed by TERM signal
Jul  9 20:12:51 tkl-laptop init: tty6 main process (4511) killed by TERM signal
Jul  9 20:12:53 tkl-laptop exiting on signal 15

---

### Post by Ek0nomik on 2007-07-10
Have you updated your video drivers lately?  That is one solution I was able to find, but the only fix mentioned was, "updating my drivers fixed it".  I know it's rather broad, but maybe it will do you some good.  If not, just say so and we can look into it a bit more.

---

### Post by Papi-KB7VGW on 2007-07-10
Well that is certainly something I can look into.  I don't have any problems with video.  I have the Intel  945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) and installed the 915 resolution mod for it.  I think I will check out the Intel site.  This is really the only problem that I have and since this thing boots in 30 sec, I don't even use hibernate anymore.  If noone else has any ideas I will come back if I don't find anything.

---

