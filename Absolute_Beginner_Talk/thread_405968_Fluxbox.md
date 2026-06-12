---
title: "Fluxbox"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by fobnicat on 2007-04-10
I am attemptingt o d/l and install fluxbox.. Has anyone had any experience with this install?  Does it even run on Ubuntu? also which source do I d/l?  Thanks guys..

P.S. is there a way to do it through repositories?

---

### Post by johnnymac on 2007-04-10
Yup I use it....and it is in the repositories.

---

### Post by fobnicat on 2007-04-10
could you get me that code for the repository install? I knew it was on the subversion repository, but for soem reason I dont know how to gain access to that repo. Thanks!

---

### Post by johnnymac on 2007-04-10
sure...

sudo apt-get install fluxbox

Also, if you do a search for Fluxbox in the forums you'll find posts talking about tips, tricks, etc.

---

### Post by rufius on 2007-04-10
```
sudo apt-get install fluxbox fluxconf fbdesk fbpager
``` 

:)

---

### Post by fobnicat on 2007-04-10
thanks guys

---

### Post by fobnicat on 2007-04-10
hmmmm 


```
fobnicat@fobnicat-desktop:~$ fluxbox
Warning: Failed to open file(/usr/share/fluxbox/nls/en_US.UTF-8/fluxbox.cat)
for translation, using default messages.
Failed to read: session.tabs
Setting default value
Failed to read: session.ignoreBorder
Setting default value
Failed to read: session.forcePseudoTransparency
Setting default value
Failed to read: session.numLayers
Setting default value
Failed to read: session.tabPadding
Setting default value
Failed to read: session.focusTabMinWidth
Setting default value
Failed to read: session.styleOverlay
Setting default value
Failed to read: session.slitlistFile
Setting default value
Failed to read: session.groupFile
Setting default value
Failed to read: session.appsFile
Setting default value
Failed to read: session.tabsAttachArea
Setting default value
Failed to read: session.modKey
Setting default value
apps file failure
Failed to read: session.screen0.imageDither
Setting default value
Failed to read: session.screen0.opaqueMove
Setting default value
Failed to read: session.screen0.workspacewarping
Setting default value
Failed to read: session.screen0.desktopwheeling
Setting default value
Failed to read: session.screen0.reversewheeling
Setting default value
Failed to read: session.screen0.autoRaise
Setting default value
Failed to read: session.screen0.clickRaises
Setting default value
Failed to read: session.screen0.decorateTransient
Setting default value
Failed to read: session.screen0.rootCommand
Setting default value
Failed to read: session.screen0.resizeMode
Setting default value
Failed to read: session.screen0.windowMenu
Setting default value
Failed to read: session.screen0.followModel
Setting default value
Failed to read: session.screen0.window.focus.alpha
Setting default value
Failed to read: session.screen0.window.unfocus.alpha
Setting default value
Failed to read: session.screen0.menu.alpha
Setting default value
Failed to read: session.screen0.menuDelay
Setting default value
Failed to read: session.screen0.menuDelayClose
Setting default value
Failed to read: session.screen0.menuMode
Setting default value
Failed to read: session.screen0.overlay.lineWidth
Setting default value
Failed to read: session.screen0.overlay.lineStyle
Setting default value
Failed to read: session.screen0.overlay.joinStyle
Setting default value
Failed to read: session.screen0.overlay.capStyle
Setting default value
Failed to read: session.screen0.windowScrollAction
Setting default value
Failed to read: session.screen0.windowScrollReverse
Setting default value
Failed to read: session.screen0.tabs.intitlebar
Setting default value
Failed to read: session.screen0.tabFocusModel
Setting default value
BScreen::BScreen: an error occured while querying the X server.
        another window manager already running on display :0.0
Error: Couldn't find screens to manage.
Make sure you don't have another window manager running.
fobnicat@fobnicat-desktop:~$ 

```

so is this telling me that Fluxbox takes the place of GNOME?
if so, how do i stop gnome so I can start flux?

---

### Post by mand0 on 2007-04-10
> **fobnicat said:**
> so is this telling me that Fluxbox takes the place of GNOME?
if so, how do i stop gnome so I can start flux?

I believe you need to log out and then log in choosing fluxbox.

---

### Post by Crakie on 2007-04-10
From your error message:

> Make sure you don't have another window manager running.

Seems you were trying to install it when Gnome was running. Try logging out, pressing cntrl-alt-f1 and login. Next, to make sure Gnome is not running somewhere:

```
sudo /etc/init.d/gdm stop
```

Then do your install procedure. I don't know how to start Fluxbox, since I've never used it myself, but after installation you should be able to start it without rebooting. If you cannot find the command, I suppose rebooting will do just as well:

```
sudo shutdown now
```

You will probably have an option to login with Fluxbox (correct me if I'm wrong here people, I used to run Gnome and KDE side by side and it worked like that).

---

### Post by ardchoille42 on 2007-04-10
Fluxbox is a window manager, it is used instead of gnome. Log out, choose Options and click fluxbox in the options dialog, then log in. Fluxbox is a nice and light window manager but powerful as well. More information about fluxbox is [here]("http://www.fluxbox.org/").

---

### Post by bodhi.zazen on 2007-04-10
You do not need to reboot or re-install fluxbox or anything complicated like that.

You can run Gnome and fluxbox (or more) at the same time if you like, but you need to do some modifications ...

See here ... [http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

If you just want to run fluxbox, log out of gnome. At the log in screen select sessions and select fluxbox, then log back in.

You will also find some helpful how-to's for fluxbox here : [http://community.fluxbuntu.org/index.php/board,18.0.html](http://community.fluxbuntu.org/index.php/board,18.0.html)

HTH

---

### Post by fobnicat on 2007-04-10
whoo hoo! got it! thanks guys

---

