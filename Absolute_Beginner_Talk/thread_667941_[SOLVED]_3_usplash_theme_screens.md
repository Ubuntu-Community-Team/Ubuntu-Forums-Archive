---
title: "[SOLVED] 3 usplash theme screens"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by phil66 on 2008-01-14
My distro is Linux Gutsy Gibbons 7.10

I downloaded startup-manager (SUM) to change grub theme and usplash theme

Both new themes from Gnome-look.org 

Grub install with no problems and now running

Usplash downloaded and install with no problems but the original usplash an orange or yellow colored theme is still displaying

After the new usplash displays the orange usplash display then blinks and another yellow or orange one displays until the desktop displays

Would someone please tell me how to correct this

---

### Post by meindian523 on 2008-01-14
Do you want to replace the splash screen while desktop is loading or the one while Ubuntu is booting?

---

### Post by phil66 on 2008-01-15
"Do you want to replace the splash screen while desktop is loading or the one while Ubuntu is booting?"

I want to replace the one just before the desktop loads. Or if possible completely eliminate it.

What is that screen named. The boot screen is usplash but I have no name to begin searching the one before the desktop.

Thanks for the reply

---

### Post by meindian523 on 2008-01-16
Just confirming,you mean the one in which Nautilus ,etc load,it has a Ubuntu logo in top right and there's a kind of progress bar of icons at the bottom(default screen),correct?

---

### Post by phil66 on 2008-01-16
> **meindian523 said:**
> Just confirming,you mean the one in which Nautilus ,etc load,it has a Ubuntu logo in top right and there's a kind of progress bar of icons at the bottom(default screen),correct?

The one you are speaking of is "Usplash" and is the first screen after grub.
I have been able to change that one to another display

The one after that is the one I would like to make changes too.
It is a solid color and I can only change the color
That display comes up fades then comes up again
After that display comes the desktop

Anything but that solid color screen would be an improvement

---

### Post by meindian523 on 2008-01-17
Nopes,I'm talking about the first screen after the login.

---

### Post by phil66 on 2008-01-17
> **meindian523 said:**
> Nopes,I'm talking about the first screen after the login.

I will try again to clarify. This is what I see when I power up.

First screen is grub

I do not get a login screen as this is a one user pc and I auto login

Second screen is usplash which shows to be booting something

Third is the solid color screen which I do not know how to change or modify

Fourth screen is the desktop

I hope this give you enough info

---

### Post by meindian523 on 2008-01-17
Does it look like the static you receive between two channels when you are tuning your TV?

---

### Post by phil66 on 2008-01-17
> **meindian523 said:**
> Does it look like the static you receive between two channels when you are tuning your TV?

Not really just off then back on to that awful looking yellow color

---

### Post by meindian523 on 2008-01-17
I'm afraid I got no idea what you are talking about.I can't see any parallel on my system here.You will have to wait for someone else more experienced to help you out in this matter.

---

### Post by phil66 on 2008-01-18
Would anyone else like to take a shot at this.

I have an orange screen between the login manager and the desktop

I would like to eliminate this screen if possible. Why is it therehttp://ubuntuforums.org/images/smilies/confused.gif
:confused:

---

### Post by GaryUK on 2008-01-19
> **phil66 said:**
> Would anyone else like to take a shot at this.

I have an orange screen between the login manager and the desktop

I would like to eliminate this screen if possible. Why is it therehttp://ubuntuforums.org/images/smilies/confused.gif
:confused:

Phil66,

The screen you are referring to is the Gnome splash screen rather than the usplash - you can put an image on it by using system/preferences/splash screen. How you get rid of that awful orange colour I have no clue as yet - I think it may be a setting in the gconf-editor or you may be able to do it with the startup manager utility if you have it.

Sorry cannot be much more help but it bugs me as well and I hope someone knows more than me so that we can both get rid of it.

Regards,

---

### Post by phil66 on 2008-01-20
[QUOTE=GaryUK;4169801]Phil66,

The screen you are referring to is the Gnome splash screen rather than the usplash - you can put an image on it by using system/preferences/splash screen. How you get rid of that awful orange colour I have no clue as yet - I think it may be a setting in the gconf-editor or you may be able to do it with the startup manager utility if you have it.

Gary

Thanks for the reply

I have start up manager but can only change grub display and usplash display

As far as the splash screen under systems>preference it does not exist

Will try and search gconf-editor for any clues

---

### Post by phil66 on 2008-01-21
Problem resolved

This is a presession screen that open before desktop
This screen is needed in the boot sequence

The colors may be changed by opening a terminal to
/etc/gdm/presession/default and changing the color code at the default location near the bottom of the screen

Now if we could only add a theme it would be easier on the eyes

---

### Post by BandD on 2008-03-09
If anyone else finds this thread, please note the Capitol letters in the path to this file:

```
sudo gedit /etc/gdm/PreSession/Default
```

Anyway, great work!  Thanks for posting the final result.  It looks much better now!

---

