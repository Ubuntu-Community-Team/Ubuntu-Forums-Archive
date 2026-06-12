---
title: "Powermac G5 Audio not working saying dummy"
date: 2012-07-23
forum: Apple Hardware Users
---

### Post by Seth Mac Fan on 2012-07-23
I have installed **Kubuntu** **12.04 power pc** and can not get my audio to work at all it **says it is dummy audio** and when I turn it all the way up there is **no sound coming out** . When I run the live cd the audio card does not say dummy but it still does not work ? 

**Anybody know a fix for this ?**

---

### Post by 2blue on 2012-07-23
Have you opened alsamixer in terminal? You very often have to check the settings there to get any sound. In lubuntu 12.04 I had fuzz a bit to get alsamixer to appear, but in general I think it should be there.

---

### Post by str8bs on 2012-07-23
+1 2blue's post

The PowerMacs can be finicky. Mine has the issue listed in the [_PowerPC FAQ_](https://wiki.ubuntu.com/PowerPCFAQ)in the [_Sound Section_]("https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F")that begins "Recent versions of Ubuntu have inherited...."

It is basically opposite the G4DA issue right after it. You can rename that file or just edit it and put a #before all those if they are in the file.

---

### Post by Seth Mac Fan on 2012-07-23
> **2blue said:**
> Have you opened alsamixer in terminal? You very often have to check the settings there to get any sound. In lubuntu 12.04 I had fuzz a bit to get alsamixer to appear, but in general I think it should be there.

I will give it a try , it is just that I am not very good with the terminal , I know the basics but not as good as I should be to figure something like that out on my own with no instructions .

---

### Post by 2blue on 2012-07-24
Hi again Seth, is it working?

When you type alsamixer in terminal you enter an application that is very managable for those who are not that used to Terimal functions. You only need to work with the setting there which does not involve any sudo commands, but rather short keys to maneuver the functions (like arrows right-left-up-down). You get it almost immediately, and it is usually the "master" paragraph that needs to be set on higher levels, but there are several to play around with. There is even a GUI package in package manager that allows alsamixer to open as a regular application under  "Menu- Sound & Video - Alsamixergui", but you don`t really need to install it.

I think I ran the first command in the FAQ str8bs links too " sudo rm /etc/modprobe.d/blacklist.local.conf", then rebooted and for some odd reason I had to reinstall the alsamixer packages (from package manager) for it to appear in Terminal.

---

### Post by Seth Mac Fan on 2012-07-27
> **2blue said:**
> Hi again Seth, is it working?

When you type alsamixer in terminal you enter an application that is very managable for those who are not that used to Terimal functions. You only need to work with the setting there which does not involve any sudo commands, but rather short keys to maneuver the functions (like arrows right-left-up-down). You get it almost immediately, and it is usually the "master" paragraph that needs to be set on higher levels, but there are several to play around with. There is even a GUI package in package manager that allows alsamixer to open as a regular application under  "Menu- Sound & Video - Alsamixergui", but you don`t really need to install it.

I think I ran the first command in the FAQ str8bs links too " sudo rm /etc/modprobe.d/blacklist.local.conf", then rebooted and for some odd reason I had to reinstall the alsamixer packages (from package manager) for it to appear in Terminal.

I got my audio working I figured it out thanks it was not hard at all to figure out .

---

