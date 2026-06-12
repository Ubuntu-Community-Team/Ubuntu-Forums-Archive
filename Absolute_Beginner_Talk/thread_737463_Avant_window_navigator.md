---
title: "Avant window navigator"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Jon11393 on 2008-03-27
When I attempt to open it nothing happens.... I ran it in the terminal (avant-window-navigator) and got the following error:[B]

avant-window-navigator: symbol lookup error: avant-window-navigator: undefined symbol: awn_gconf_new

[/B]

I'm new to Ubuntu and was wondering if anyone had some idea of how to solve this problem.

---

### Post by emptybox on 2008-03-27
I'm new to Ubuntu as well, but I installed AWN Today using this guide.

[http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+navigator")

I'm still playing about with it, but when you install it this way it comes up in Applications->Accesssories, and you can start it that way.

It does need Compiz to be working first. Which means your Deskop Effects have to be turned on.
(System->Preferences->Appearance.

---

### Post by Jon11393 on 2008-03-27
Yes, I used that to install it but now it seems to not be functioning... :(

---

### Post by Daveth on 2008-03-27
to clarify then, it is neither on the desktop or in Applications/accessories/Avant window manager ? Did the installation throw up any obvious dependency errors?

---

### Post by Jon11393 on 2008-03-27
It is not appearing when I click on "Avant window manager" in Applications -> Accessories -> Avant Window Manager.Although, in the preferences tab( System -> preferences -> AWN manager) the manager shows, just not the bar in itself. As far as I know there were no errors in installation, only after a reboot did it not appear. 

Note: I added the command avant-window-navigator in the session box.

---

### Post by forrestcupp on 2008-03-27
Are your desktop effects turned on?  If you don't know, go to System->Preferences->Appearance and click the 'Visual Effects' tab.  AWN requires that they are on.  If you can't get them to come on, that is a different problem we will have to solve.

Go ahead and check that and also tell us what video card you have and which drivers you are using.

---

### Post by Jon11393 on 2008-03-27
Desktop effects are on.

I'm using a Mobility Radeon X300 video card with restricted drivers enabled for it... I don't know which ones though.

 Sorry about the vagueness, I'm new to this Ubuntu thing (been using windows all my life, until now).

---

### Post by Therion on 2008-03-28
Wow... How weird is this?  I had this *exact experience* just about a half hour ago. Too be totally honest with you I'm not 100% certain how I resolved it all step by step but here's pretty much how I stumbled through it all and got AWN up and running smoothly.

I uninstalled most of the currently installed AWN stuff using Synaptic.  Then I used [this link](http://linuxhelp.blogspot.com/2008/02/install-avant-window-navigator-awn-in.html) to reinstall it.  It seemed to me that enabling the gutsy-backport repository is what did the trick, but I dunno.  I was on my first cup of coffee for this whole thing, but I do know I have AWN up and running and looking good.  If you use Cut and Paste for installing though, watch out... the extra $ in the command line was messing with my head... But, then, it WAS pretty early.

Hope that helps.

---

### Post by Daveth on 2008-03-28
um, you have told awn to load on each start-up event I suppose? It is in preferences on the opening general tab on awn manager in the menu (or right click on awn if you could see it!). If not, I'll keep looking for solutions for you.

---

