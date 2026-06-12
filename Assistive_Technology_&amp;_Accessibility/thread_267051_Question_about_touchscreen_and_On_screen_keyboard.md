---
title: "Question about touchscreen and On screen keyboard"
date: 2006-09-28
forum: Assistive Technology &amp; Accessibility
---

### Post by anarchyburger on 2006-09-28
Hey guys

Alright I have a question.  I am converting a sony vaio srx77 laptop into a umpc.  Sounds nuts huh.  I will send pics when I am done.  So anyways I am adding a touchscreen to the lcd through usb but what I need is a on screen keyboard that I can utilize on the login screen (gdm),

---

### Post by frafu on 2006-10-01
An onscreen keyboard that would also be available at the login screen would be nice. 

8)

---

### Post by frafu on 2006-10-02
It seems that the login screen is among the next targets for the developers. Have a look at the last line of [this message]("http://ubuntuforums.org/showpost.php?p=1568608&postcount=2").

---

### Post by justynbutler on 2006-10-08
OnBoard at the login screen is an essential for full time use of Ubuntu on a slate tablet pc.

I'm really looking forward to this feature, devs please let us know when it's available!

cheers,
Justyn.

---

### Post by frafu on 2006-10-08
You may want to follow the project [here]("https://wiki.ubuntu.com/Accessibility/Projects/onBoard") and [here]("https://launchpad.net/people/onboard/+branch/onboard/main").

frafu

---

### Post by justynbutler on 2006-10-27
Hi again,

Are there any plans to make OnBoard work at the login screen in the near future? Or is it more of a Feisty Fawn kind of goal?

If the latter is the case, is there anything preventing a temporary hack for the mean time? For example, what's to stop OnBoard being launched (as root) by gdm? Say, by adding a line in gdm/Init/Default?

cheers,
Justyn

---

### Post by t0rtois3 on 2006-10-29
Yes this does work.  Add 

fi
exec onboard

at the end of /etc/gdm/Init/Default.  Then you must set the login window style to plain in the login window preferences dialog. 

I'll ask on the gdm mailing list if they plan to have a better way of doing this sort of thing.

---

### Post by justynbutler on 2006-10-29
That's great, thanks!

Justyn

---

### Post by frafu on 2006-11-22
Appearantly, you have to put 
```
 
exec onboard &

``` 
in the file /etc/gdm/Init/Default instead of 
```
 
exec onboard 

``` 

Look [here]("http://ubuntuforums.org/showthread.php?p=1792228#post1792228") for a more detailed explanation. 

frafu

---

