---
title: "at startup it opens firefox"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-16
okay. i added firefox to the startup programs tab in the sessions menu just to test it.
i restarted. it opened firefox as expected.
then i removed firefox from the list and it still opens it at startup
what to do?:confused:

---

### Post by bapoumba on 2007-02-16
Hi,
you could try closing Firefox and run **gnome-session-save** from a terminal (if you are using GNOME, of course ;)).

---

### Post by panti19 on 2007-02-16
thanks for the reply, but it didn't work :(

---

### Post by bapoumba on 2007-02-16
Mmm, well, no pending updates in Firefox extensions or themes ?
I've looked around and did not find anything relevant :/
What are your startup programs listed in > System > Prefs > Sessions ?

---

### Post by panti19 on 2007-02-16
update-notifier
/usr/lib/evolution/3.8/evolution-alarm-notify
gnome-power-manager
gnome-volume-manager --sm-disable

---

### Post by JamieC on 2007-02-16
Open a terminal window (Applications -> Accessories -> Terminal) and post the output of the following:-
```

cd ~/.config/autostart && for i in `ls`; do echo $i; cat $i; done

```

---

### Post by Old Pink on 2007-02-16
You could try ```
sudo aptitude reinstall firefox
``` in a terminal (Applications > Accessories > Terminal)

---

### Post by panti19 on 2007-02-16
~/.config/autostart$ 

that's all it displays

(Pink Floyd forever, my friend! )

---

### Post by panti19 on 2007-02-16
heelp. now it opens :
skype; gaim; firefox when i boot.
it appears that it's trying to restore the last session.
i had skype and gaim opened before i shut down, but not firefox

---

### Post by livingtarget on 2007-02-16
In Sessions, do you have "Automatically save changes to session" enabled? If so untick it and reboot, see if it helps.

---

### Post by panti19 on 2007-02-16
now it's worse:
it opens the sessions window, firefox and the file browser in the home folder :confused:

---

### Post by livingtarget on 2007-02-16
Ok after you've done that go into the sessions screen. Have a look around so it indeed says you disabled automatic saving. See attached image...

Now close ALL programs that you don't want to start when running a new session!

Make sure you know how to use CTRL + ALT + F1 and CTRL + ALT + F7.

CTRL+ALT+F1 will launch you in the console mode and CTRL+ALT+F7 will make you go back into GUI mode. Try it for a few times.

So with no programs open, press CTRL+ALT+F1 and log-in, now type **gnome-session-save**. Hopefully that should do it, you've saved the sessions manually and because it's not updating automatically it's worked. Go back into GUI mode and next time you reboot it ought to be ok, if not I've run outta ideas. :KS 

I just realised: alternatively you could enable automatic saving close down everything you don't want,  reboot and switch automatic saving off again. It should result in a clean session also :P

---

### Post by panti19 on 2007-02-16
it cannot save session in CTRL+ALT+F1 mode because:
cannot find display
i've saved the session in normal GUI terminal and it said it saved the session , but when i rebooted,it opened firefox and the terminal

---

### Post by livingtarget on 2007-02-16
Did you try the 2nd method? 

1. Enable "automatic saving" again

2. Close ALL programs down

3. Log off/Reboot

4. When you gnome booted immediatly disable "automatic saving"

5. Log off/Reboot again and it should give a plain session.

---

### Post by Old Pink on 2007-02-16
Simple solution: 

Close everything

System > Preferences > Sessions

Delete the sessions in the list. 

Reboot.

---

