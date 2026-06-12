---
title: "different users different languages"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Zaxor the other @ss isn't on 2007-01-30
I have different users that use different languages is there anyway I can get ubuntu to load up the prefered language of the user at startup..


thanks a ton guys and gals

Zaxor... (the original since 1981)

---

### Post by PriceChild on 2007-01-30
You should just be able to change their language in the System>Prefs afaik?

---

### Post by Zaxor the other @ss isn't on 2007-01-31
Sorry friend I see no place to do it on the menu

If you want I will list all the apps

about me
Assistive technology preferences
Desktop Background
Font
Keyboard
Keyboard shortcuts
menu layout
menu & toolbars
mouse
network proxy
palm os
power management
prefered applications
remote desktop
removable drives and media
scim input method setup
screen resolution
screensaver
sessions
sound
theme
windows

thanks appreciate the help

---

### Post by irish_flu on 2007-01-31
Under the System --> Administration menu, there's a spot where you can add support for various languages, and also a menu where you can choose each new user's "default" language.

Them using the word "default" makes me think there has to be a way to change it for each individual user, but I haven't figured it out yet....

---

### Post by Zaxor the other @ss isn't on 2007-01-31
> **irish_flu said:**
> Under the System --> Administration menu, there's a spot where you can add support for various languages, and also a menu where you can choose each new user's "default" language.

Them using the word "default" makes me think there has to be a way to change it for each individual user, but I haven't figured it out yet....

Yeah I see the "language support" but it changes the whole system and not the individual user.

I would be shocked if there isn't a way to do this

---

### Post by Zaxor the other @ss isn't on 2007-02-01
bump

---

### Post by Zaxor the other @ss isn't on 2007-02-01
> **PriceChild said:**
> You should just be able to change their language in the System>Prefs afaik?

any other ideas

---

### Post by rannasjem on 2007-02-03
I need to set up different languages for different users also, any update on this?

---

### Post by PurplePenguin on 2007-02-03
It can be done quite easily.

Click "Options" and then "Language" at the user login screen.

I've done this successfully for a long time now with English and Russian users - works like a charm.

---

### Post by smolko on 2007-02-04
> **PurplePenguin said:**
> It can be done quite easily.

Click "Options" and then "Language" at the user login screen.

I've done this successfully for a long time now with English and Russian users - works like a charm.

That's it! Thanks PurplePenguin.
I've just been wondering, whether It's possible to change this when creating a new user - or even better create a group of users with one specific language and then just add the new user e.g. to the "English" or "Russian" group.
I'm just curious, I have only 4 users on my computer with 3 different languages :) changing it once at the login screen is really easy in my case.

---

### Post by PurplePenguin on 2007-02-04
I'm not sure if there's a way to do it when you create a new user (I just checked the System -> Administration -> Users and Groups, but nothing jumped out at me).  It's not too bad, though.  I think you just have to select a language once and it remembers each user's last selected language choice.

---

### Post by Zaxor the other @ss isn't on 2007-02-06
> **PurplePenguin said:**
> I'm not sure if there's a way to do it when you create a new user (I just checked the System -> Administration -> Users and Groups, but nothing jumped out at me).  It's not too bad, though.  I think you just have to select a language once and it remembers each user's last selected language choice.

Thanks I will give it a try

---

### Post by Zaxor the other @ss isn't on 2007-02-06
> **PurplePenguin said:**
> It can be done quite easily.

Click "Options" and then "Language" at the user login screen.

I've done this successfully for a long time now with English and Russian users - works like a charm.

this may sound strange but on my login screen there is no Language option...

I have 

Session Type
Switch User (which goes to a check box with a check and unused)
Restart Session
Remote Login
Console Login
Shutdown

---

### Post by ingo on 2007-02-08
I suffer from the same symptoms as Zaxor - but then again I use Kubuntu and KDM. Nevertheless, GDM or KDM should be the same difference, shouldn't it?

If anybody got Kubuntu running, could you let us know how to do this?

Ta

Ingo

---

### Post by ingo on 2007-02-08
right, just installed gdm
> sudo apt-get install gdmand selected it to be my default login manager (question comes up automatically) and lo and behold, there is the "options" box and I can select my language! 

But when I select "German" and then log in everything stays in English although I've got both language packs installed...

BTW, if you want to switch back to your trusty KDM simply do the following:

1) log out
2) change terminals by pressing CTRL+ALT+F2
3) login and then type
> sudo /etc/init.d/gdm stop4) type 
> sudo dpkg-reconfigure kdm5) select kdm as your default

Bingo

Question remains for me - how to switch between languages? Is there something really dumb I overlooked?

---

### Post by Zaxor the other @ss isn't on 2007-02-13
> **ingo said:**
> right, just installed gdm
and selected it to be my default login manager (question comes up automatically) and lo and behold, there is the "options" box and I can select my language! 

But when I select "German" and then log in everything stays in English although I've got both language packs installed...

BTW, if you want to switch back to your trusty KDM simply do the following:

1) log out
2) change terminals by pressing CTRL+ALT+F2
3) login and then type
4) type 
5) select kdm as your default

Bingo

Question remains for me - how to switch between languages? Is there something really dumb I overlooked?

I did a complete reinstall and use ubuntu and Kubunto in conjunction... I use ubuntu to place the names of the users in "users and groups" and add any language support I need under "language support" than I use Kubunto to log in and on the first time login they ask for Language preference which I fill out for the appropriate user.  It is a very idiotic way to do things but it seems to work...though your users must use Kubuntu

---

