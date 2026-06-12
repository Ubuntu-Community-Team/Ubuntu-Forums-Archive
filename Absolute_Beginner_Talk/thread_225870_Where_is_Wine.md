---
title: "Where is Wine?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-07-30
I decided to install Wine and give it a try.  I want to see if it'll run a couple of windows apps.

Anyhow, I went into the "Add/Remove" are of Ubuntu, found Wine, checked, applied, and installed.  

I can't find it anywhere on any of my menus.

I also edited the menus to see if it was hidden and it's not there, either.

Am I missing something?  Do I need to do something else in order to get this up and running?

---

### Post by Kilz on 2006-07-30
> **georgetoon said:**
> I decided to install Wine and give it a try.  I want to see if it'll run a couple of windows apps.

Anyhow, I went into the "Add/Remove" are of Ubuntu, found Wine, checked, applied, and installed.  

I can't find it anywhere on any of my menus.

I also edited the menus to see if it was hidden and it's not there, either.

Am I missing something?  Do I need to do something else in order to get this up and running?

[Take a read here.]("http://www.tghc.org/staticpages/index.php/wine")

---

### Post by jimmygoon on 2006-07-30
You have to get an EXE and run it... Wine isn't actually a program persay: It just runs when you try to run an EXE file...

---

### Post by georgetoon on 2006-07-30
Thanks, guys.  

Okay, so I put in a disk, installed the program.  Sso where does it run from.  it looks like it installed into a diretory called "c/progam files."  Where is this located? I did a search and came up empty.

---

### Post by Kilz on 2006-07-30
> **georgetoon said:**
> Thanks, guys.  

Okay, so I put in a disk, installed the program.  Sso where does it run from.  it looks like it installed into a diretory called "c/progam files."  Where is this located? I did a search and came up empty.

Its installed to a hidden folder called .wine in your home folder.

---

### Post by georgetoon on 2006-07-30
> **Kilz said:**
> Its installed to a hidden folder called .wine in your home folder.

Thanks.:) Ifound this and wow is this cool!:)

Okay, I installed PhotoImpact 5 and it is not able to run. The install screen takes up the entire screen real estate, so I'm unable to do/see an uninstall using Wine. Can I just go into the .wine folder and delete the Ulead PhotoImpact folder?

---

### Post by u04f061 on 2006-07-30
> **georgetoon said:**
> Thanks.:) Ifound this and wow is this cool!:)

Okay, I installed PhotoImpact 5 and it is not able to run. The install screen takes up the entire screen real estate, so I'm unable to do/see an uninstall using Wine. Can I just go into the .wine folder and delete the Ulead PhotoImpact folder?

you can remove that window by using

sudo winecfg

to configure wine.a window will open and look for emulate virtual desktop
or similar like this.uncheck that check-box or set the variable  1024 X 800
or same like above for resolution .

however better is to uncheck that box.

you can use graphical emulate for wine named as xwine in ubutu repository.

if u want to uninstall some windows programe you can easily delete entire files of it in ubuntu without any hesitation as for as i did on my ubuntu.
however most applications of ms windows have uninstaller try to find out those

---

### Post by georgetoon on 2006-07-30
> **u04f061 said:**
> you can remove that window by using

sudo winecfg

to configure wine.a window will open and look for emulate virtual desktop
or similar like this.uncheck that check-box or set the variable  1024 X 800
or same like above for resolution .

however better is to uncheck that box.

you can use graphical emulate for wine named as xwine in ubutu repository.

if u want to uninstall some windows programe you can easily delete entire files of it in ubuntu without any hesitation as for as i did on my ubuntu.
however most applications of ms windows have uninstaller try to find out those

Thanks.:)  I looked for an uninstaler in PI5 and canot find one.  I simply moved the entire folder to the trash bin (BTW, ubuntu's trsh bin dos not have a "restore files" option)

I attempted to do an instal on PI twice and after doing this, all the fonts got zaped when instalshield runs. the fonts on my system ae fine, but fonts associated with instaling a windows ap in instal shield anr not there..only little strings of small boxes. 

also, i tried to uninstall wine and evden though ubuntu tels me that wine has been uninstalled, .wine is stril present with Al files intact.

---

### Post by rowanparker on 2006-07-30
But the thing I like about the Ubuntu trash is that you can view a file in the trash without having to restore it first. All you need to do to restore something in the trash is copy and paste.

---

### Post by Lord Illidan on 2006-07-30
> **rowanparker said:**
> But the thing I like about the Ubuntu trash is that you can view a file in the trash without having to restore it first. All you need to do to restore something in the trash is copy and paste.

Plus it is a folder (.Trash) not in some wierd hidden place like the XP recycle bin.

---

### Post by georgetoon on 2006-07-30
> **rowanparker said:**
> But the thing I like about the Ubuntu trash is that you can view a file in the trash without having to restore it first. All you need to do to restore something in the trash is copy and paste.

Yes, but what if you do not remember the original location?

And back to my original problem, fonts are not working in Wine. I did an uninstall a re-install and another re-install. Nothing appears to work.

I wonder what would happen if I installed Wine from Automatix?

Edit -- I checked the Wine manual and it appears I can easily add fonts just be dragging and dropping them into "c/windows/fonts."  However, i don't know which font I need. does anyone know? 

Or perhaps I need to reinstall fonts in some way in order to get them recognized again?

---

