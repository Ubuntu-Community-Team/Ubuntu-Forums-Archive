---
title: "FINALLY! Away from Windows!!"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by andyho on 2007-07-18
[COLOR="Indigo"]Alrighty so 3 days ago I installed  Ubuntu after fighting with Vista for over a week. It took a while but finally got it! My poor machine was riddled with viruses.. hell, I thought a stick of RAM was dead for the last 3 months.. nah, it tested fine! :o Now though I can't get my Nvidia card to install.. no biggie, onboard works for now. I did get my HP Officejet installed, but no scanning. :confused: I see it's a standard problem.. the only other thing left to figure out is how I'm going to connect to the remaining Windows machines on the network. But at least I got away from windows finally!! I just couldn't stand all the spyware, adware, and trojans I just seemed to pick up!?! Anyways.. if anyone has any pointers I'd be glad to try them. I've tried the tutorials for the vid card, but no luck yet.. Talk to y'all later!![/COLOR]

---

### Post by wolfen69 on 2007-07-18
Welcome!
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)  are 2 good places to start

---

### Post by brownknight on 2007-07-18
welcome and congratulations on your switch to ubuntu.

---

### Post by rocknrolf77 on 2007-07-18
> **wolfen69 said:**
> Welcome!
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)  are 2 good places to start

I think it's easier to start with the psychocats guide first :) It has screenshots so it's easier for a new user.

---

### Post by benanzo on 2007-07-18
Congratulations!

I would be happy to help you with your scanner and video card.  What kind of scanner is it?  -- You said HP, what model is it?  Also, which nVidia video card do you have?

For the video card usually all you have to do is enable it in **Restricted Manager**.  Go to **System -> Administration -> Restricted Drivers Manager** and put a checkbox next to the nVidia item then follow the intructions.

For the scanner you should be able to set it up using HP's configuration program.  Unfortunately it is not in the Ubuntu menu by default so you have to either enable it or launch it from the terminal.

To enable the menu item right-click on the Menu Bar panel (Applications - Places - System) and select **Edit Menus**.  Now in the left pane scroll down and highlight the **Preferences** item.  Scroll through the right pane and put a check box next to **HPLIP Toolbox**.  Now close the menu editor.  You can get to HP's config app buy going to **System -> Preferences -> HPLIP Toolbox**.

But wait!  For some dumb reason the standard Ubuntu install doesn't include one necessary library in order to run this app, **python-qt3**.  So you have to install it first.

Open a terminal (**Applications -> Accessories -> Terminal**) and do:
[COLOR="Red"]EDIT:[/COLOR] *Sef* pointed out below that you should update your package information before installing **python-qt3**, which is true:
```
sudo apt-get update
```
Now you can do:
```
sudo apt-get install python-qt3
```

Now you can run the program to set up your scanner and fine-tune your printer.

Good Luck!

---

### Post by Sef on 2007-07-18
> Open a terminal (Applications -> Accessories -> Terminal and do:
Code:

sudo apt-get install python-qt3



Before doing that command, do this one:

```
sudo apt-get update
```

---

### Post by Kheldin on 2007-07-18
> **andyho said:**
> [COLOR="Indigo"]Alrighty so 3 days ago I installed  Ubuntu after fighting with Vista for over a week. It took a while but finally got it! My poor machine was riddled with viruses.. hell, I thought a stick of RAM was dead for the last 3 months.. nah, it tested fine! :o Now though I can't get my Nvidia card to install.. no biggie, onboard works for now. I did get my HP Officejet installed, but no scanning. :confused: I see it's a standard problem.. the only other thing left to figure out is how I'm going to connect to the remaining Windows machines on the network. But at least I got away from windows finally!! I just couldn't stand all the spyware, adware, and trojans I just seemed to pick up!?! Anyways.. if anyone has any pointers I'd be glad to try them. I've tried the tutorials for the vid card, but no luck yet.. Talk to y'all later!![/COLOR]

Welcome to Ubuntu!!

Although it takes some time for the first time linux newbie to make the transition, I believe (as well as many others) that you will be very happy that you switched. The community here is excellent as you will find many people willing to help you out. Just remember, be patient and persistent and you will prevail!

Anyways, good luck and welcome again.

---

### Post by misfitpierce on 2007-07-18
aye another welcome and congrats on switch! :)

---

### Post by ubanchaos on 2007-07-18
yes welcome to linux and none crashing OS

---

