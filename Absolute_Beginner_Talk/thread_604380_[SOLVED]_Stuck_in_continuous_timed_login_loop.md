---
title: "[SOLVED] Stuck in continuous timed login loop"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by barkerben on 2007-11-06
Hello,

I could have sworn I have already asked this, but now I can't find my pos, so maybe I didn't :-p

I have accidentally set up my Ubuntu 7.10 box to have  timed login after 1s. But the credentials are wrong, so as soon as gdm loads I get a continuous loop of error messages and can't log on  - any idea what I can do?

Cheers,

Ben

---

### Post by cmnorton on 2007-11-06
You're going to have to find out which files are changed as a result of a timed login and use the live CD to go in and change them back. 

I believe the file you want to change is /etc/X11/gdm/gdm.conf. I got this out of 

[http://ubuntuforums.org/showthread.php?t=488675](http://ubuntuforums.org/showthread.php?t=488675)

After hearing your story, I don't have a true "throwaway" system on which to test this. 

Good luck.

---

### Post by barkerben on 2007-11-06
Hmmm...the only reference I could find to autologin was in the gdm.conf-custom file. I removed the references, but it had no effect. I don't know whether thos file has not been parsed for some reason. Argh :-)

---

### Post by schorsch on 2007-11-06
The following section in the file /etc/gdm/gdm.conf should be the interesting one:
```
[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30
```

---

### Post by barkerben on 2007-11-06
Yep:

I set the /etc/gdm/gdm.conf file to:

> 
[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30



and removed the timed login reference in the /etc/gdm/gdm.conf-custom file to leave to


> 

[daemon]

[security]

[xdmcp]

[gui]


No joy though...

Ben

---

### Post by schorsch on 2007-11-06
Uhm, sure you are using gdm and not kdm or any other display manager? Because I just added autologin for my user and the different section in /etc/gdm/gdm.conf-custom looks like this:
```
[daemon]

AutomaticLoginEnable=true

AutomaticLogin=schorsch

TimedLoginEnable=true

TimedLogin=schorsch

```
Furthermore I am not being asked for any credentials ... what are the exact error messages you get as me might look in the wrong direction? Are you sure that your file system is not full?

---

### Post by barkerben on 2007-11-06
Hi - I am certainly using gdm. Initially, the section in gdm-custom was set to to:

> 

[daemon]

AutomaticLoginEnable=false

AutomaticLogin=ben

TimedLoginEnable=true

TimedLogin=ben

 

I tried setting this to false, and then also removing it entirely. 

The error i get is that at the moment the gdm login box appears, I get a dialogie box appear wityh a "nop entry" sign and "Authentication failed", with an "OK" button. If I click "OK", it simply re-appears...

Any ideas?

I have managed to get in via recovery mode, but what I am able to do is limited...

Cheers,

Ben

---

### Post by schorsch on 2007-11-06
Are you able to run
```
sudo gdmsetup
```
in recovery mode?

---

### Post by barkerben on 2007-11-06
Unfortunately not. Since that seemed to be the source of the problems, I tried that first. However, to run that I need to be in a graphical environment. If I type "gdm" from the recovery command line, I get the same authentication problem. The only way I have got a desktop up is to type "startx". However, then if I try to run gdmsetup I get an error that "GDM is not running"...

---

### Post by schorsch on 2007-11-06
Hmmmmm .... what about removing and purging gdm in text mode and reinstalling it again? Sorry that I have no other idea at the moment:
```
sudo apt-get purge gdm
sudo aptitude install gdm
```

---

### Post by barkerben on 2007-11-06
> Sorry that I have no other idea at the moment:

No problem - it worked :-)

Thanks a lot,

Ben

---

### Post by travis31 on 2007-11-06
I had this problem after upgrading to Gutsy. What fixed it was removing this line
```
@include common-pamkeyring
```
from /etc/pam.d/gdm

---

### Post by startherepodcast on 2007-11-06
You Could Always Go Into Recovery Mode And Type

```
sudo startx
```

This Would Get You to Gnome to Reconfigure Your PC

---

### Post by schorsch on 2007-11-06
> **barkerben said:**
> No problem - it worked :-)

Thanks a lot,

Ben
Hey, glad to hear that this "brutal" method seems to have solved your problem. Could you please mark this thread as solved?

---

