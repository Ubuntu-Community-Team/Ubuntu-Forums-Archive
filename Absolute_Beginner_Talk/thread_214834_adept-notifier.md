---
title: "adept-notifier"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-07-13
Could someone please tell me what I'm supposed to see when there are new updates, and when there are none? Last time I updated, I was in Gnome, but have seen no update notifications since switching to KDE.

---

### Post by slimdog360 on 2006-07-13
I wouldn't have a clue but I suppose if you typed in the old ```
sudo apt-get update && sudo apt-get dist-upgrade
``` you can always find out. 
But Im guessing you already knew that.

---

### Post by richbarna on 2006-07-13
Open Adept, Check the box that says upgradable, and uncheck all the others (on the search part).

---

### Post by Orc65 on 2006-07-13
> **editrix said:**
> Could someone please tell me what I'm supposed to see when there are new updates, and when there are none? Last time I updated, I was in Gnome, but have seen no update notifications since switching to KDE.


Ok, I'm using Kubuntu and I get this notifier in the bottom right of the taskbar. (Circled Icon in image)

---

### Post by editrix on 2006-07-13
Guys, I googled this before I asked, and found nothing useful. And here, in less than half an hour, I get THREE useful answers--especially the screenshot. Thanks!

Will check out all of them and ask again if I need help.

And, no, I didn't know about
sudo apt-get update && sudo apt-get dist-upgrade At least, not in that way. I don't want to update everything on my system (dialup, it takes too long) but will try it if all else fails.

---

### Post by editrix on 2006-07-13
> **Orc65 said:**
> Ok, I'm using Kubuntu and I get this notifier in the bottom right of the taskbar. (Circled Icon in image)

Orc, you may have solved another problem of mine. My sound is too loud! Is that a speaker icon next to the wallet? Does it control speaker volume? If so, where did you get it, because I see nothing about volume or speaker in the menu or applets.

---

### Post by infoseeker on 2006-07-13
Open the mixer (Kmix I think). It should then appear (as far as I remember).

---

### Post by editrix on 2006-07-13
> **infoseeker said:**
> Open the mixer (Kmix I think). It should then appear (as far as I remember).

Tried that, thanks. But I couldn't figure it out--and it's huge! All I want is a little slider like Windows has--and Gnome, I think.

---

### Post by editrix on 2006-07-13
> **richbarna said:**
> Open Adept, Check the box that says upgradable, and uncheck all the others (on the search part).

Well, the good news is, according to Adept, there are no updates. 


[QUOTE=Orc65] I get this notifier in the bottom right of the taskbar[/QUOTE]

Tried adding that to my Kmenu, but when I launched it, nothing happened--maybe because there are no updates? I guess I'm expecting something like in Gnome, where the light's either on or off, depending on whether there are updates or not. Is that how the notifier works in KDE? Or does it just show up when there are updates? (Yes, I know I could wait, but ...)

---

### Post by Jucato on 2006-07-13
Adept Notifier is a service/daemon that runs in your background. So you don't see any window when you try to run it. Also, Adept Notifier is started whenever you start KDE/Kubuntu, so it basically checks for updates during startup. I'm not sure if there's also a time interval when Adept Notifier checks again for updates, just like in GNOME. You can manually trigger Adept Notifier by doing a *sudo apt-get update*.

If there are updates available, a green LED icon will be displayed in your system tray and a notification will popup (AFAIK). If there are no updates, there is no icon.

---

### Post by editrix on 2006-07-13
> **Fenyx said:**
> Adept Notifier is a service/daemon that runs in your background....If there are updates available, a green LED icon will be displayed in your system tray and a notification will popup (AFAIK). If there are no updates, there is no icon.

Thanks for clearing that up. I had visions of 842 updates when I did finally figure it out. Now I can relax--and get on with my next problem :-)

---

### Post by cookdav on 2008-05-06
> **editrix said:**
> Could someone please tell me what I'm supposed to see when there are new updates, and when there are none? Last time I updated, I was in Gnome, but have seen no update notifications since switching to KDE.

When there are none, each time you login, you should BRIEFLY see a
shiny round green LED icon...since that means no updates, it disappears
after a few seconds.

But, when there ARE upgradable packages available, you'll see
a 'warning triangle' icon, which will persist.

If, as happened to me when I upgraded, and re-used my same home-area
from the previous release (of Kubuntu 7.10), this adept-notifier setup
BROKE, then the fix is to just do:
```

rm -R .kde

```
and logout and back in, and KDE will rebuild your whole KDE desktop
and taskbar layout, including the Autostart launchers.  
Then, the notifier should work once again.
[This 'fix' is often necessary after upgrades of KDE, as
the data-layout changes in subtle ways.]

Hope this helps...

Dave

---

### Post by hotpinkflamingo on 2008-05-13
I accidentally turned off that update notifier, and can't figure out how to turn it back on.  I've never had an icon in my taskbar showing when there are updates.  How do I add it?
Should I run this:
rm -R .kde
?
I thought that -r is a command that wipes your system?

---

### Post by hotpinkflamingo on 2008-05-22
Can anyone help me?  I feel like I'm invisible; I have at least 4 open questions here that no one has responded to.......

---

### Post by El-Gimpo on 2008-05-30
Hey.  I'm a semi Ubuntu N00b as well, and did the same thing.  Accidently disabled adept notifier, and couldn't for the life of me work out how to restart it.

I came across this thread searching for the answer, and as I've just worked it out, I thought I better come back and share it.

The command is adept_notifier.  I just ran that in konsole,then a pop up appeared and said that autostart had been disabled, and would I like to re-enable it.

Haven't logged out and back in to try it yet though.

---

### Post by hotpinkflamingo on 2008-05-30
Thanks a bunch!  That sounds simple enough.  :)

---

### Post by El-Gimpo on 2008-05-30
No problems.

---

