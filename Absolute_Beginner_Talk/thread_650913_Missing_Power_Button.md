---
title: "Missing Power Button"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2007-12-26
I suspect this won't be as easy as unmuting a sound-channel but here goes:  :biggrin: 

When I hit the power button on the menu bar and t***he window pops up and I notice my power-off button is missing***.  I have SUSPEND and HIBERNATE but not POWER OFF.  I can log out and shut down from that screen but thats a real slowdown when I'm packing up the laptop.   

I tried a fix from another thread on this topic and I got nothing.   

Before we go any further here are a list of recent changes to my system, the first on being the the most recent:

AlsamixerGUI (about two hours ago)
Chromium (game)
Added the weather icon to the menu-bar
Yesterday:
Added KDE
Installed Adblock for Firefox.

The problem manifested after installing AlsamixerGUI, I promptly uninstalled it and still no button.   Shortly after uninstalling AlsamixerGUI Firefox hung up and I had to use Force Quit (taskbar) to shut it down.    Any connection?

What else can I try?

---

### Post by rickycodie on 2007-12-26
try to right click on the menu bar and then add to panel. it should be in there.

---

### Post by Epic Plecostomus on 2007-12-26
> **rickycodie said:**
> try to right click on the menu bar and then add to panel. it should be in there.

No no.  :)  I have that button.  I click on it and the window that pops up is missing the POWER OFF option.   Big blank space where it used to be.

---

### Post by vishzilla on 2007-12-27
Please verify this:
go to Menu: System -> Administration -> Login Window

In the first tab "Local" of "Login Window Preferences", check if "Menu Bar:
Show Actions menu" is selected.
If no, check it and close the form. If that was the problem it should appear
again.

---

### Post by Epic Plecostomus on 2007-12-27
> **vishzilla said:**
> Please verify this:
go to Menu: System -> Administration -> Login Window

In the first tab "Local" of "Login Window Preferences", check if "Menu Bar:
Show Actions menu" is selected.
If no, check it and close the form. If that was the problem it should appear
again.

I don't see that on there.  Am I looking in the right place?

---

### Post by vishzilla on 2007-12-27
> **Epic Plecostomus said:**
> I don't see that on there.  Am I looking in the right place?

Oops! its the 2nd tab of the Login Window Preferences.

Go right here System>Administration>Login Window. Hope you get it right

---

### Post by vishzilla on 2007-12-27
Its below the GDM theme selection! Did you get it? I have attached the Login Window

---

### Post by Epic Plecostomus on 2007-12-27
Hoooboy I must be really dumb.  Bear with me a bit longer.

I click on SYSTEM.   I go to ADMIN.   I look down the list and I don't see Login Window. 

Nor is it listed when I edit the menu.

---

### Post by vishzilla on 2007-12-27
> **Epic Plecostomus said:**
> Hoooboy I must be really dumb.  Bear with me a bit longer.

I click on SYSTEM.   I go to ADMIN.   I look down the list and I don't see Login Window. 

Nor is it listed when I edit the menu.
try out ```
sudo gdmsetup
``` in terminal

---

### Post by meierfra on 2007-12-27
> Added KDE

That's what caused it. I have the same problem ( since ever). I don't know whether there is a fix, but I didn't search very long.  I just have the computer's power button set to turn of the computer. So it does not bother me.

---

### Post by RomeReactor on 2007-12-27
Hi. Are you in Gnome or KDE now? when you add another QUIT button, is it still missing the Shut Down option?

---

### Post by meierfra on 2007-12-27
I fixed  my previous post.

---

### Post by Epic Plecostomus on 2007-12-27
> **meierfra said:**
> That's what caused it. I have the same problem ( since ever). I don't know whether there is a fix, but I didn't search very long.  I just have my power button set to turn of the computer. So it does not bother me.

That's why.   When I type the terminal command that was suggested it tells me I don't have the GDM running.   That's why I cannot find the menu.  Natch

And I suspect meierfra is right I just didn't notice it last night.   I can live without it for the time being.   

Both of you thanks for your help.

---

### Post by Epic Plecostomus on 2007-12-27
> **RomeReactor said:**
> Hi. Are you in Gnome or KDE now? when you add another QUIT button, is it still missing the Shut Down option?

I'm in Gnome now.  And I tried that.  :)  Thanks!

---

