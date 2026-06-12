---
title: "For the love of god &gt;_&lt; Installing GTK themes.."
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Riyonuk on 2007-08-11
It seems no matter what I do I cannot install any themes T_T
I'm using Ubuntu 6.10, and am trying to install pretty much any theme from gnome-look. Currently, my focus is on this one --> [http://gnome-look.org/content/show.php?content=61936&forumpage=0](http://gnome-look.org/content/show.php?content=61936&forumpage=0)

I download it..

Drag and Drop doesnt work
Clicking install, browsing to it doesnt work
Extracting to /home/riyonuk/.themes doesnt work

They either say bad file format, OR they install (I get all excited) and then when I choose to apply the skin, it just makes everything look like windows, that or makes the ubuntu default theme all black. I hate my life x_x

Please help ^^

---

### Post by starcraft.man on 2007-08-11
> **Riyonuk said:**
> It seems no matter what I do I cannot install any themes T_T
I'm using Ubuntu 6.10, and am trying to install pretty much any theme from gnome-look. Currently, my focus is on this one --> [http://gnome-look.org/content/show.php?content=61936&forumpage=0](http://gnome-look.org/content/show.php?content=61936&forumpage=0)

I download it..

Drag and Drop doesnt work
Clicking install, browsing to it doesnt work
Extracting to /home/riyonuk/.themes doesnt work

They either say bad file format, OR they install (I get all excited) and then when I choose to apply the skin, it just makes everything look like windows, that or makes the ubuntu default theme all black. I hate my life x_x

Please help ^^

Works for me, though it looks horrible in my opinion. I just went System > Preferences > Theme and pushed install/browse.

If you want a better dark theme IMO go download smoked glass (and neutronium classic for the firefox black fix, read the included instruction file in the neutronium). If you want a light theme look at nimbus and pick a different icon theme (the default one makes Sun logo display next to applications menu, annoying). Both great themes IMO and install fine in my experience.

---

### Post by Riyonuk on 2007-08-11
Could you post a screenshot please?

---

### Post by PurposeOfReason on 2007-08-11
When you put it in your /.themes folder did you remember to take the emerald theme out of that folder?

---

### Post by capink on 2007-08-11
I always put the themes in /usr/share/themes so they are available for all users.

---

### Post by Riyonuk on 2007-08-11
Still not working, it looks nothing like that screnshot. Not even remotely close. Suggestions? Maybe reccomendations for minimilistic dark themes.

---

### Post by Riyonuk on 2007-08-14
Anybody know a solution? This is ridiculous :(

---

### Post by Bachstelze on 2007-08-14
The file you download is called 61936-Dyne.tar.gz. Just open a terminal, browse to the dir you saved the file to and do :

```
sudo tar xzvf 61936-Dyne.tar.gz -C /usr/share/themes
```

You're there.

---

### Post by tadada on 2007-08-14
The screen shot is from fluxbox (I used it in a CLI system I set up but it had problems with nautilus so I reinstalled normal Ubuntu) If you want it to look like that you need Fluxbox. It is only the window controls for gnome so it uses the human window border with Dyne colors.

---

### Post by Riyonuk on 2007-08-14
Ok, well this is how it looks when I apply pretty much any theme --> [http://img77.imageshack.us/img77/5570/screenshotnn1.png](http://img77.imageshack.us/img77/5570/screenshotnn1.png)

I just installed XFCE and Fluxbox. I log in with XFCE, there is no toolbars. When I minimize something, it just vanishes. I log in to fluxbox, when I right click, is just says fluxbox.

I think linux hates me T_T

---

### Post by Riyonuk on 2007-08-14
Plus, in the Gaia theme, [http://www.gnome-look.org/content/show.php/GAIA?content=63246](http://www.gnome-look.org/content/show.php/GAIA?content=63246), it has the start button picture, so Im assuming it would apply to the ubuntu logo in the top left?

---

