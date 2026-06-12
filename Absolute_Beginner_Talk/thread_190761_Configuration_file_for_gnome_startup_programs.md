---
title: "Configuration file for gnome startup programs"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by sumadartson on 2006-06-06
Unfortunately, I am not able to find the configuration file in which gnome stores its startup programs. This is driving me so crazy, I'm seriously considering switching to KDE. And I hate KDE.

All I need to do is change the order of starting these programs up. Does anyone know where gnome stores the actual configuration file where this is controlled? 

I must be the n-th person asking this, but I haven't been able to find the answer in the forums as yet. I'll close the thread if this question is answered elsewhere.

PS Simplicity police, ok. However, an advanced button every once in a while won't kill a single user. :mad:

---

### Post by stevanbt on 2006-06-06
Have you tried System-->Preferences-->Sessions.  There's a tab there that will allow you to specify programs that are executed at startup... However, I'm not sure if you can change the order though.

---

### Post by sumadartson on 2006-06-06
Hey Stevanbt,

Yup, tried it. It seems the most logical option to look for the setting. And, for some reason, they removed the option where you could change the order. ](*,) 

Still, there should be a configuration file somewhere. Right? I haven't learned vim for nothing... I hope. :wink:

---

### Post by uzi09 on 2006-06-06
hey, i think you're probably looking for this:
[http://www.gnome.org/learn/admin-guide/2.14/sessions-3.html](http://www.gnome.org/learn/admin-guide/2.14/sessions-3.html)

btw, my biggest peeve about gnome is the fact that you can't just go straight to the file and (in english :P) edit it just as easily as you can in WM such as iceWM and fluxbox. some of the things i've wanted to edit end up being really confusing xml files and just makes me real mad :mad: -- i think this may be the only file i've come across yet in gnome that comes close to accomplishing this.
[/rant]

---

### Post by sumadartson on 2006-06-06
>  	
hey, i think you're probably looking for this:
[http://www.gnome.org/learn/admin-gui...essions-3.html](http://www.gnome.org/learn/admin-gui...essions-3.html)


Thanks for the suggestion, but I already found that one. However, I think I should have been more specific. This file handles the configuration for all users, but I just need to modify this for one user account.

[hyperbole] This is approximating Windows-like stupidity... [/hyperbole]

---

### Post by uzi09 on 2006-06-06
uhh, wouldn't that just be this file:
$HOME/.gnome2/session
?

---

### Post by sumadartson on 2006-06-06
> uhh, wouldn't that just be this file:
$HOME/.gnome2/session
?

You'd think so...

However, that file is only present if you save a session. It doesn't exist in my ~/.gnome2 dir until I do 

```
gnome-session-save
```

Yet, I can store startup programs using the gui without this file existing. :-k 

 I'll start vimming and see if I can get things running [sid vicious] my way [/sid vicious].

---

### Post by sumadartson on 2006-06-06
Ok... using a random string for a startup command and than grepping for the string results in

> weegee@TIJGETJE:~$ grep -R asdfasdfawef .
grep: ./.gnupg: Permission denied
grep: ./.mozilla-thunderbird/xwyt28gz.default/lock: No such file or directory
grep: ./.openoffice/1.1.3/setup: No such file or directory
grep: ./.gdesklets/sockets/%3A0.0: No such device or address
grep: ./.kde/socket-TIJGETJE/kdeinit__0: No such device or address
grep: ./.kde/socket-TIJGETJE/kdeinit-:0: No such device or address
grep: ./.kde/socket-TIJGETJE/klauncherzLpZpb.slave-socket: No such device or add ress
grep: ./.kde/socket-TIJGETJE/localhost.localdomain-171a-4485fb61: No such device  or address
grep: ./c/windows/system32/help.exe: No such file or directory
grep: ./c/windows/system32/winver.exe: No such file or directory
grep: ./c/windows/system/help.exe: No such file or directory
grep: ./c/windows/system/winver.exe: No such file or directory
./.config/autostart/asdfasdfawef.desktop:Exec=asdfasdfawef


Apparently, the ominously named "autostart" directory contains this information in some files. However, how this is read and how I can change the execution order here is unclear.

I might just write a bash file which I could call from the autostart. This is ridiculous. Or I'm very stupid. Or both.

---

### Post by StayPuft on 2006-08-28
I am upset that this thread died. How could they not allow me to change the order of startup programs? I hope this is fixed in Edgy.... It's really a pain in the *** when trying to use DevilsPie.

---

### Post by sumadartson on 2006-08-28
I might be wrong, but...

I think the list is executed in alphabetical order. So you could build a workaround by renaming the xml files.

The other option is to write a short bash script that executes in the right order.

----
No sig to see. Move along now.

---

### Post by bluntu on 2006-08-29
I rarely use TOR even though I have it installed and the problem is that it runs upon starting up every single time.

Is there a way I can stop it from running on startup? Now each time I turn on  my computer I have to do this:

$ sudo /etc/init.d/tor stop

---

### Post by sumadartson on 2006-08-29
Uhrm, move the script from init.d (do back it up), but make sure it's no longer in that directory. 

Then, run update-rc.d . Read the man page from update-rc before you run it. Marvel at how amazing linux is.

---
I might be wrong.

---

