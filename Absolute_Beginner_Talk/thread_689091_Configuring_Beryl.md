---
title: "Configuring Beryl"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by fizur2002 on 2008-02-06
I have most of it figured out, but what i havent been able to find is how to get the different icon sets to work, and have the icon cluster at the top of the screen and how to make windows disolve like in this youtube video.  Im using a fresh install of 7.10

---

### Post by oedha on 2008-02-06
since you have install 7.10....means that you have compiz installed ( some people said beryl is dead....compiz-fusion now )
sudo apt-get install compiz
go to desktop....right click - choose change desktop background
the go to visual effects tab.....choose the extra one......

---

### Post by fizur2002 on 2008-02-06
ive got extra checked, but i cant add the cluster of icons like i want in the top.

---

### Post by NightwishFan on 2008-02-06
do you have the compiz config settings manager?

---

### Post by fizur2002 on 2008-02-06
im a noob, i dont know how to check it.  Trying to learn linux so i can be of more use in the workplace, and have fun at home.

---

### Post by NightwishFan on 2008-02-06
It is ok. I am here to help.

On the top bar go to System/Administration/Synaptic Package Manager

Search for Compiz

Right click and install the compiz config settings manager.

This will add Advanced Desktop Effects Settings in the menu: System\Preferences

You can configure compiz fusion effects there its simple.

---

### Post by oedha on 2008-02-06
oo....did you mean...extra plugins ?
you didnt explain what video that you've seen....
do you have custom option on your visual effect tab ?

---

### Post by NIT006.5 on 2008-02-06
1. I would honestly recommend compiz-fusion over beryl. I'm also led to believe that the beryl project has more-or-less died out completely (so no updates) and secondly, as I understand it, compiz-fusion is a sort of "merger" of beryl and compiz. On top of that, I've had stability issues with beryl in the past (although it was possibly just my hardware) and generally I personally find compiz-fusion to be superior.

2. Even with the "default" installation of compiz-fusion, you will need the settings manager to "fine tune" and customize your effects (and imho this should have been included by default). However:

```

sudo apt-get install compizconfig-settings-manager
```

Then System -> Preferences -> Advanced Desktop Effects Settings

OR

In Appearance Preferences, on the Visual Effects tab you should now see a custom option with a "Preferences" button.

Hope that helps.

---

### Post by fizur2002 on 2008-02-06
ok, i have the options i want checked off, how do i get them to show up now?

---

### Post by fizur2002 on 2008-02-06
how do i put the widgets up on the screen?

---

### Post by oedha on 2008-02-06
have you open terminal and run
sudo apt-get install compizconfig-settings-manager
after you install it....thee shortcut will appear on your menu.....and you can start to set it

---

### Post by fizur2002 on 2008-02-06
yes i have done that, but certain things just will not show up.

---

### Post by fizur2002 on 2008-02-06
here is the youtube video.

[http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM)

---

### Post by Tatty on 2008-02-06
If you want widgets, you probably want to install Screenlets.

If you are looking for the dock (the bar across the top with the icons in) then you need to install the Kiba Dock

They are in the respositories


Although a lot of people moan that the Kiba Dock is too CPU intensive, if you find this is the case, you could try installing AWN which most people seem to prefer now. Although I cant really comment as  I do not use any docks or widgits myself because all my comps are pretty ancient. :)

---

### Post by nikoPSK on 2008-02-06
> **fizur2002 said:**
> how do i put the widgets up on the screen?

widgets? I've never gotten them to work... anyways, if this hasn't been covered, compiz is newer. :)

---

### Post by fizur2002 on 2008-02-06
well i dont have to worry about being too CPU intensive as i have a Q6600, so i should be fine.  Basically its going to be a show off OS for friends and such, along with regular web browsing and let windows deal with my gaming needs.

---

### Post by nikoPSK on 2008-02-06
> **fizur2002 said:**
> well i dont have to worry about being too CPU intensive as i have a Q6600, so i should be fine.  Basically its going to be a show off OS for friends and such, along with regular web browsing and let windows deal with my gaming needs.

gaming, no offense, will be harder with mainstream games.

---

### Post by Tatty on 2008-02-06
Well in that case it sounds like what you are after.

I just had a look and it seems that i was wrong about kiba-dock being in the respositories.  check out this thread to install [http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")
check this thread out too [http://gutsywww.ubuntuforums.org/showthread.php?t=584201&highlight=desklet]("http://gutsywww.ubuntuforums.org/showthread.php?t=584201&highlight=desklet")

For your widgets install gdesklets:
```
sudo apt-get install gdesklets
```


Just as a side note  to clear up any misunderstandings : origionally there was Compiz, then Beryl started up as an offshoot of Compiz.  For a while both projects existed separately but then last year they merged back together to become Compiz Fusion.

---

### Post by fizur2002 on 2008-02-07
ive got desklets installed, but they are not showing up.  once i get all this finished the way i want it too, i will be editing my first post with all the instructions so someone searching will have an easier time to configure it themselves.

---

### Post by nikoPSK on 2008-02-07
> **fizur2002 said:**
> ive got desklets installed, but they are not showing up.  once i get all this finished the way i want it too, i will be editing my first post with all the instructions so someone searching will have an easier time to configure it themselves.

you could try screenlets too. :)

---

