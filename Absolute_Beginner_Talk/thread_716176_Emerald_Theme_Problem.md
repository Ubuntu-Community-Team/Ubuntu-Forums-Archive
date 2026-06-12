---
title: "Emerald Theme Problem"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by wargamer17 on 2008-03-05
I recently installed a theme for emerald on my ubuntu computer to make it look like mac os X. The theme is from the mac4lin project and can be seen in my attached screenshot. The screenshot also shows my problem. The problem is that after I enable desktop effects and type "emerald --replace" in the terminal(which is how you start emerald i think, or at least i have been) I lose my title bar and bottom bar of all windows. How does this happen and how can it be fixed? I am new to linux but I am getting used to commands now so that's not a problem. Anyway to fix it would be great.

---

### Post by owbizi on 2008-03-05
Just to check, do you have libemeraldengine0 installed?
$sudo apt-get install libemeraldengine0

---

### Post by spiderbatdad on 2008-03-05
You should not have to emerald --replace. compizconfig-settings-manager should take care of that for you.

---

### Post by wargamer17 on 2008-03-05
> **owbizi said:**
> Just to check, do you have libemeraldengine0 installed?
$sudo apt-get install libemeraldengine0

I tried entering that and it says it is already the newest version.

[QUOTE=spiderbatdad]You should not have to emerald --replace. compizconfig-settings-manager should take care of that for you.[/QUOTE]

I have already tried getting compizconfig-settings-manager through terminal with this code:
```
sudo apt-get install compizconfig-settings-manager
```

But it says "E: couldn't find the package for compizconfig-settings-manager".

---

### Post by owbizi on 2008-03-05
Then, apt-get it!
$sudo apt-get install compizconfig-settings-manager python-compizconfig

---

### Post by wargamer17 on 2008-03-05
That's what i did, but i still get the error. Would it work if i uninstalled the theme and then reinstalled it? or is it something else? Also, i'm not sure if this is related, or besides the fact that i can't get the compizconfig-settings-manager thing to work, but when i type "compiz --replace" my whole screen goes white and i can't do anything. The only way i can get out of it is by Alt+F2 and typing "metacity --replace" again just by guessing.

---

### Post by spiderbatdad on 2008-03-05
looks like possibly your sources are commented out in /etc/apt/sources.list

[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

you should also be able to find the package by opening synaptic and searching it.

---

### Post by wargamer17 on 2008-03-05
When i went into synaptic and searched for "compiz" i installed pretty much anything i could with the "compiz" and in System > Preferences i have GL Desktop. Is that the manager you have been trying to get me to install? if so, i still can't get emerald to work but i get all the kool desktop effects working with metacity themes via GL Desktop. What else is there that I can do to fix this?:(

---

### Post by rainwalker on 2008-03-05
Go to System > Administration > Software sources and enalbe all of the repositories. Then try installing compizconfig-settings-manager again

---

### Post by wargamer17 on 2008-03-06
It shows all the repositories checked and when i try to install it, it still says the same thing :(.

---

### Post by rainwalker on 2008-03-06
Did you reload the package list?

---

### Post by wargamer17 on 2008-03-06
Yes, i believe I did, but my system no longer works. I logged out after installing some updates and when i logged back in, it said my last session was only 10 seconds long or something like that and that i didn't have enough disk space to load the session. So, i'll just wait till I reinstall windows and reinstall Ubuntu as well. Won't be too long, so I'll be back in a couple of days depending on how long it takes for me to back stuff up.

---

### Post by Tomana on 2008-03-06
ok, I ran the following successfully using terminal (and in this order)

sudo apt-get install emerald
emerald --replace
sudo apt-get install libemeraldengine0
sudo apt-get install compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager python-compizconfig

then, go to Ststem > Preferences and you should find the following New Icons

Advanced Desktop Effects Settings
Emerald Theme Manager

Download some Emerald Themes here:

[http://www.gnome-look.org/index.php?xcontentmode=103&PHPSESSID=160acbfd087bccb857d5cad1e715c34c](http://www.gnome-look.org/index.php?xcontentmode=103&PHPSESSID=160acbfd087bccb857d5cad1e715c34c)

and then play with it for a while (it's ok, nothing will break)

Other than this I know not, at this time

---

### Post by wargamer17 on 2008-03-08
Well, i am going to be reinstalling ubuntu soon, so that should fix whatever problem i had with the title bar thing. Maybe I did something wrong when i was trying it out. It was my first time, and I never really read anything I just installed the theme and it worked until i switched it. I will also try your commands because it should be an easier way to install what I need. Thank you, and I will let you know if it helps when i re-install it this week. :)

---

