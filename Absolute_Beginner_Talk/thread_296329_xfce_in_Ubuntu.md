---
title: "xfce in Ubuntu"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Absolom on 2006-11-09
Today I decided to see what the Xfce destop looked and felt like in Ubuntu I used the following command in terminal.

sudo aptitude update && sudo aptitude install xubuntu-desktop

it seemed to install ok and I get xubuntu login screen there is no xfce option in my sessions and it just goes to my gnome desktop what if anything did I do wrong?

---

### Post by LLRNR on 2006-11-09
Well I decided to install not xubuntu desktop, but kubuntu desktop (I wanted desperately to see what KDE feels like) and at the beginning the same thing happened to me...
[quote="Absolom"]it seemed to install ok[/quote]
Yeah... but at a double check I found out that there were some packages that were missing or were to be downgraded... I installed those and it worked afterwards, the KDE session option appeared in my sessions menu at login.

HTH,

LLRNR

---

### Post by taurus on 2006-11-09
You don't see an option for XFce4 in the Sessions (bottom left corner) from the GUI login screen!!!

---

### Post by Absolom on 2006-11-09
I get the Xubuntu login screen with the sessions selection right under the place name/pw are put it has sessions on right and languages on left.....  but when I select it I have choice of KDE Gnome gnome failsafe etc but no XFCE selection....

when I get in I have my gnome desktop...

---

### Post by taurus on 2006-11-09
Have you tried to reboot?

---

### Post by Absolom on 2006-11-09
Yes have tried restart several times first ,then tried a shut down completely and turned on same results....

---

### Post by gn2 on 2006-11-09
> **Absolom said:**
> Yes have tried restart several times first ,then tried a shut down completely and turned on same results....

Can you boot Ubuntu, and mark xubuntu-desktop for re-installation in Synaptic?

Perhaps that might track down and install the missing bits & bobs.

Point and click------ does the trick!

Terminal only when all else fails is my motto :)

---

### Post by Absolom on 2006-11-09
I ran 

sudo aptitude update && sudo aptitude install xubuntu-desktop

in terminal a second time and it said no new everything.... made no difference

---

### Post by taurus on 2006-11-09
Which version of Ubuntu are you running:  Breezy, Dapper, or Edgy?  And what does your /etc/apt/sources.list look like anyway?

```
cat /etc/apt/sources.list
```

---

### Post by Absolom on 2006-11-09
I had brain storm did a lil googling and figured it out originally I installed xfce but seems that is not same as installing xfce desktop I ran sudo apt-get install xubuntu-desktop   and it installed desktop and now gives me the xfce option in sessions..

I feel kinda dumb now.. should of occured to me earlier.

---

### Post by kerry_s on 2006-11-09
Even with just xfce4, you should have got the option in session. I have a server install with just xfce4 and it was in session.

---

