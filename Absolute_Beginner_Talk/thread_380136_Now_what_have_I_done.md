---
title: "Now what have I done?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-03-09
Aaarrrgh! 

It all started when I decided to try to change the font style in firefox.  Changing the font led to an immediate crash, and I couldn't get it to restart.

I figured the easiest thing to do would be to uninstall and reinstall the browser.  Under applications there used to an entry named "Add/remove" -- it's gone now, but I 'll get to that -- so I tried to remove firefox with it.  A message popped up and informed me that firefox had too many dependencies and that I would have to remove it with the Synaptic Package Manager. 

So I fired up the ole SPM.  Don't really no how to use the thing well so I read the instructions.  IT said that if I wanted to remove a package and all it dependencies I had to mark it for "complete removal."  I located firefox  in the SPM, marked it for complete removal, and hit apply.

Then I tried to reinstall.  First thing I noticed was that the "add/remove" tab that used to be at the bottom of Applications was gone.  I tried reinstalling firefox through SPM but no dice.

Now I can launch firefox, my add/remove tab is gone, a bunch of icons are missing, etc.

Can I fix this without going through an entire re-install?

---

### Post by webjames on 2007-03-09
Hi,

you could try from the terminal: (terminal is under Applications > Accessories > Terminal)

```
sudo apt-get install firefox
```

sudo means run the command as root (more privileges)

apt-get install works the same as S.P.M. but in the terminal.

when you right clicked complete removal would would have seen this screen:

[attach]26981[/attach]

when you go to remove something i wouldn't recommend it if it has a dependency : ubuntu-desktop

hope this helps, post back the results.

regards,

James

---

### Post by lamalex on 2007-03-09
yeah if you managed to uninstall firefox you also managed to uninstall ubuntu-desktop. apt-get install that and then apt-get install firefox. unfortunately firefox is tied into ubuntu so you can't get rid of it. it's a double edged sword but that's not worth going into. (re)install ubuntu-desktop and let us know your status.

---

### Post by Mr. Svinlesha on 2007-03-10
Hi: sorry about the delay in my reply, been away from the computer for a couple of days, and am at work now. In addition I misread your posts at first and thought you meant that I needed to reinstall ubuntu from scratch -- which, unfortunately, I'm probably going to have to do soon anyway, due to printer problems.

I'm a bit confused about the advice:  just to be absolutely clear, I should type:

1) apt-get install ubuntu-desktop

2) enter

3) password

4) apt-get install firefox

Have I got it right?

---

### Post by towsonu2003 on 2007-03-10
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
that will install everything that a regular ubuntu installation provides. in fact, it's just a pseudo-package that keeps track of everything else and make sure that "everything else" is installed :)

(bonus info incoming below)
 it's similar to package xubuntu-desktop and kubuntu-desktop
xubuntu-desktop makes you install the default software that comes with [Xubuntu]("http://xubuntu.com/")
kubuntu-desktop makes you install the default software that comes with [Kubuntu]("http://kubuntu.com/")...

---

### Post by Mr. Svinlesha on 2007-03-11
Hey guys!

Well, I tried all three commands:

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install firefox

...in that order.

The add/remove option has returned under applications, but I still can't get firefox to start.  The browser crashes immediately upon opening.

Any other suggestions, or am I heading for a complete reinstall at this point?

---

### Post by Mr. Svinlesha on 2007-03-11
I just noticed that my OP is very poorly written and even incorrect.  The next-to-last line above should read: > Now I **can't** launch firefox, my add/remove tab is gone, a bunch of icons are missing, etc.I must have been exhausted when I wrote it, sorry about the potential confusion.  

The same is still true.  I can't get firefox to launch.

---

### Post by towsonu2003 on 2007-03-11
> **Mr. Svinlesha said:**
> but I still can't get firefox to start

launch it from the command line and try with a *clean/new profile*: [https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs) (section 1.2.)

if it still fails with a new profile, let us know what kind of error it spits to the terminal / command  line (Applications > accessories > Terminal)

---

### Post by infol on 2007-03-11
the changes (font style) you made are probably still causing the problems you have,

try renaming/removing the configuration folder ```
mv ~/.mozilla ~/.notworkingmozilla
``` so that firefox creates a new profile from scratch.

---

### Post by Mr. Svinlesha on 2007-03-11
> **infol said:**
> the changes (font style) you made are probably still causing the problems you have,

try renaming/removing the configuration folder ```
mv ~/.mozilla ~/.notworkingmozilla
``` so that firefox creates a new profile from scratch.Hey!  Whadda ya know!  It worked!

Thanks, infol!  That was nifty!

But I don't understand...was the configuration folder named "notworkingmozilla"?  That's almost like magic.  Do you think I could fix my printer by writing in something like, "Hey, Ubuntu ~/.printer ~/.fixmybrokenprinter"?

:)

---

### Post by infol on 2007-03-12
Hi again,

glad it worked  ;)

Your personal configuration files for Firefox (as you probably have figured out) are stored in ~/.mozilla ... if this folder is missing (which it is if you have renamed it), firefox will create a new folder with that name and use the default settings.

If it is now working, you can safely delete the folder ~/.notworkingmozilla (unless you want to figure out what caused the problems you had).

> Do you think I could fix my printer by writing in something like, "Hey, Ubuntu ~/.printer ~/.fixmybrokenprinter"?
unfortunately, ubuntu has not developed to this stage yet....  :)

---

### Post by towsonu2003 on 2007-03-12
> **infol said:**
> 
If it is now working, you can safely delete the folder ~/.notworkingmozilla (unless you want to figure out what caused the problems you had).


you can get your bookmarks back from there though: 
```
nautilus ~/.notworkingmozilla
```
there is a folder there that looks like: 
randomnumbers.default

go in there, copy the bookmark.html to your desktop and tell Firefox to import it using the menu at Bookmarks > Organize Bookmarks (opens new window) > File > Import

Other files that might interest you in that folder:
cert8.db cookies.txt formhistory.dat hostperm.1 key3.db signons.txt history.dat  mimeTypes.rdf ([[SIZE="1"]source[/SIZE]]("https://help.ubuntu.com/community/FirefoxNewVersion"))

this is stuff like certificates, form history, cookies etc...

---

### Post by Mr. Svinlesha on 2007-03-13
**infol**:

Actually, I hadn't figured that out.  I'm still working on trying to figure it out.  In fact, I'm going to go try to figure it out as soon as I'm finished writing this.


**towsonu**:

:)

Showoff.

Luckily, my installation of Ubuntu is so new that I haven't had the chance to bookmark anything of note.


I do have to add that it seems strange that a font would be available on the rolldown menu in the preferences tab but not be supported, such that it would crash firefox.  That seems like a bug worth reporting.

---

### Post by Mr. Svinlesha on 2007-03-13
Okay, time for Ubuntu 101:

You say my configuration folder is stored in ~/.mozilla.  I would like to actually see that folder with my own eyes. I can't find it.  Maybe I'm looking for it in the wrong place, or the wrong way? 

File Browser = Windows explorer: true or false?  But there is no folder named mozilla in the file browser.  What am I missing?

I see that I now rank  five cups of Ubuntu, but I don't really feel like I'm worth a single bean, yet.

---

### Post by infol on 2007-03-21
hi again!

all files (or folders) starting with a dot (like .mozilla) are hidden; however, if you open up your home folder and press ctrl+d , you should see a lot of new folders appearing, containing your preferences for the different applications you use.

for example, if you install any firefox plugins, the will be stored in /home/[COLOR="Red"]yourusername[/COLOR]/.mozilla 

if you install a new desktop theme, the 'theme-files' are stored in /home/[COLOR="Red"]yourusername[/COLOR]/.themes 

etc, etc.

---

