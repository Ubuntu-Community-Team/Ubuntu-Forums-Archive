---
title: "How do you change your splash screen?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2007-02-10
Hello. After I have formatted my computer I have for a long time lived with my splash screen being the same brown default one, but now I want to change it. I remember I used to have a menu under System>Preferences called usplash. So I did a sudo aptitude usplash but It didn't show up. So can someone tell me how to get this menu again?

---

### Post by shanepardue on 2007-02-10
It would be "sudo aptitude install usplash" not "sudo aptitude usplash". If it still doesn't work, make sure all of the repositories are enabled because it is in those repos.

---

### Post by jincast90 on 2007-02-10
> **shanepardue said:**
> It would be "sudo aptitude install usplash" not "sudo aptitude usplash". If it still doesn't work, make sure all of the repositories are enabled because it is in those repos.

Yes offcourse :) Anyway I tried doing the sudo aptitude install usplash, but the menu still isn't under System>Preferences

---

### Post by Cable on 2007-02-10
Usplash is not what you are looking for.  What you want to do is
```

sudo aptitude install gnome-splashscreen-manager

```You can then install new splashscreens that you download from [Gnome-Look]("http://www.gnome-look.org/") or [Gnome Art]("http://art.gnome.org/").

EDIT:  Hm....after reading the post again, I realize you are talking about something else.  My apologies for reading your post incorrectly.

---

### Post by shanepardue on 2007-02-10
Did it install usplash or not?

---

### Post by ciscosurfer on 2007-02-10
It's probably a good idea at this point to distinguish between a splash screen and usplash (screen):

Usplash (see this wiki page >> [https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash))
[LIST]
[*]see this wiki page for further info on how to customize the usplash >> [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)[/LIST]Splash screens are what pop up after you log in and just before you desktop fully appears (and shows you graphically about the startup of a few apps, for example, nautilus and the update-manager)

---

### Post by jincast90 on 2007-02-12
> **ciscosurfer said:**
> Splash screens are what pop up after you log in and just before you desktop fully appears (and shows you graphically about the startup of a few apps, for example, nautilus and the update-manager)

Yeps these are the ones I am looking for. I looked through the links you provided and It said that I could just change the picture manually. I already knew this was possible, but I would just rather have a menu for it (which I know exists) because I think it is easier and nicer.

---

### Post by ciscosurfer on 2007-02-12
> **jincast90 said:**
> Yeps these are the ones I am looking for. I looked through the links you provided and It said that I could just change the picture manually. I already knew this was possible, but I would just rather have a menu for it (which I know exists) because I think it is easier and nicer.In this case, you should take Cable's advice from a couple posts up and install **gnome-splashscreen-manager**.  Once you have it installed, you can use it by going to System > Preferences > Splash Screen (and from there, you can install any splashcreen themes you have downloaded from such sites as gnome-look.org or art.gnome.org).  The links I provided for you relate to Usplash and not splashscreens (remember, the usplash is what appears immediately after you select the kernel to load from your GRUB menu, and it shows (by default) an orange progress bar with a great big Ubuntu logo above it and an overall black background (this is the screen where, if you've set it up, you can see your services starting.  Remember, the splashscreen that shows up after you log in is different from your usplash screen) -- this shows up at boot time and shutdown time).  If you are interesting in changing your Upslash and are on Dapper Drake 6.06, then you can use the Usplash GUI manager (I can't recall the exact name of it at the moment though) to manipulate your Usplash screens.  If you are on Edgy Eft 6.10, you will need to refer back to the links I provided in my earlier post as the Usplash customization techniques have changed since the introduction of Ubuntu 6.10

---

### Post by jincast90 on 2007-02-12
> **ciscosurfer said:**
> In this case, you should take Cable's advice from a couple posts up and install **gnome-splashscreen-manager**.  Once you have it installed, you can use it by going to System > Preferences > Splash Screen (and from there, you can install any splashcreen themes you have downloaded from such sites as gnome-look.org or art.gnome.org).  The links I provided for you relate to Usplash and not splashscreens (remember, the usplash is what appears immediately after you select the kernel to load from your GRUB menu, and it shows (by default) an orange progress bar with a great big Ubuntu logo above it and an overall black background (this is the screen where, if you've set it up, you can see your services starting.  Remember, the splashscreen that shows up after you log in is different from your usplash screen) -- this shows up at boot time and shutdown time).  If you are interesting in changing your Upslash and are on Dapper Drake 6.06, then you can use the Usplash GUI manager (I can't recall the exact name of it at the moment though) to manipulate your Usplash screens.  If you are on Edgy Eft 6.10, you will need to refer back to the links I provided in my earlier post as the Usplash customization techniques have changed since the introduction of Ubuntu 6.10

Alright! gnome-splashscreen-manager was indeed what I was looking for. Thank you..

In my opinion this should be installed by default. I mean who says the default brown splash screen looks good with the rest of your desktop?

---

### Post by ciscosurfer on 2007-02-12
> **jincast90 said:**
> Alright! gnome-splashscreen-manager was indeed what I was looking for. Thank you..

In my opinion this should be installed by default. I mean who says the default brown splash screen looks good with the rest of your desktop?I'm sure the developers have thought about this.  And they have probably concluded that because it's only up for maybe 3 seconds, that it is not necessary to include an app to change it by default.  Just my thoughts on the issue.

---

### Post by gargo2000 on 2007-02-15
[QUOTE=Cable;2135682]Usplash is not what you are looking for.  What you want to do is
```

sudo aptitude install gnome-splashscreen-manager

```

It is not working for me, I received the following

```

 sudo aptitude install gnome-splashscreen-manager

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "gnome-splashscreen-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


```

Any Ideas?

---

### Post by gargo2000 on 2007-02-15
> **gargo2000 said:**
> [QUOTE=Cable;2135682]Usplash is not what you are looking for.  What you want to do is
```

sudo aptitude install gnome-splashscreen-manager

```

It is not working for me, I received the following

```

 sudo aptitude install gnome-splashscreen-manager

```


Never mind...I found the reason it wasn't pulling up.

---

### Post by paradj on 2007-03-10
> **ciscosurfer said:**
> It's probably a good idea at this point to distinguish between a splash screen and usplash (screen):

Usplash (see this wiki page >> [https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash))
[LIST]
[*]see this wiki page for further info on how to customize the usplash >> [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)[/LIST]Splash screens are what pop up after you log in and just before you desktop fully appears (and shows you graphically about the startup of a few apps, for example, nautilus and the update-manager)

ok  so thats usplash...
now where are the login splash how-to's?
you know how-to change the one that shows up ***as*** you login?

---

### Post by rusty4r on 2007-03-10
Now I'm lost, First I see the Grub Splash, I know which it is.

Second is the Ubuntu logo with the list of operations scrolling underneath.

Third is the login screen.

Then the NVidia Splash I think.

Then there is this small screen that pops up at the same time as the start up music just before the desktop. I thought this was the splash screen and I didn't know that splash and usplash were different.

Could someone tell me which is which please

---

### Post by paradj on 2007-03-10
i'm stiil tryin to figure that one, too..

as far as i gno...

grub is what you'll see (on a dual-boot system) to choose your OS load(eg, ubu/XP)

then there's the one which hides all the bootstrap text...

now depending on the nVidia level of install

::Kernel driver
nVidia (u can change but look for nVidia customization)
login screen (where you can enter username and password...not so much splash as background)
::Shell driver
login screen(eg. see above)
nVidia splash

then the 
usplash - by default in ubuntu this one is a rectangular shaped yellow/tan-ish/brown image that shows the base application(s) loading as little icons just below it.


..Please someone correct me if i got this wrong!

---

### Post by ciscosurfer on 2007-03-11
> **paradj said:**
> ok  so thats usplash...
now where are the login splash how-to's?
you know how-to change the one that shows up ***as*** you login?You can do this manually, or you can install an app to do it for you.  It's a good idea to know both.  So, here goes:[LIST=1]
[*]_Manually_: Open up Configuration Editor (if it's not on your menu yet, you can enable it by going into Menu Editor, selecting it to appear (and it will be under *Applications > System > Configuration Editor*).  Additionally, an easy way to get Configuration Editor to open up, is to hit the key combo of ALT-F2 and in the dialog that appears, type in **gconf-editor**.  From there, drill down to *apps > gnome-session > options* and then in the *splash_image* key, enter in the location of a login splash that you'd like to use.  What's most likely there already is something like **/usr/share/pixmaps/splash/whateverImageHere.png** ... so you can place your images here or use an image from a different location.  It doesn't really matter.  So that's the manual way to change your login splash.
[*]_Automatically_: Enable your Universe repository (check [here]("http://www.psychocats.net/ubuntu/sources") or [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html") if you don't know how to do this) and then issue the following in a Terminal (the update command is essential if you're just now adding/enabling the Universe or Multiverse repositories -- really, any time any change has been made to your /etc/sources.list file) --you can just copy and paste the following into the Terminal if you like...the double && is not a typo```
sudo aptitude update && sudo aptitude install gnome-splashscreen-manager
```[SIZE=-1]After it installs, you can get to it by going to *System > Preferences > Splash Screen*.[/SIZE]
[*][SIZE=-1]Have fun and I hope this has been helpful for anyone/everyone that has been wondering how to do this.  :-)
[/SIZE][/LIST]

---

### Post by graywizard on 2007-03-11
i installed this:

sudo aptitude install gnome-splashscreen-manager


but you guys confused me do much I would rather leave it as it and remove this ---- how do I do this please?



 i asked someone else - I got the answer - thanks - no need for one now.

i will keep system as it was.  less hassles and confusion.

---

### Post by lbelmond on 2008-02-29
=^.^=

---

### Post by tle89 on 2008-03-02
> **gargo2000 said:**
> [QUOTE=gargo2000;2158813]

Never mind...I found the reason it wasn't pulling up.

i get the same msg why was it pulling up i don't know how to fix it?

---

