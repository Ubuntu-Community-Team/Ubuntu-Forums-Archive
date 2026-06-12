---
title: "Kde"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-28
Hello!
Ubuntu has gnome. I wanna experience KDE in my ubuntu too. I dont want to install kubuntu. Can I install KDE in my ubuntu and can I have both gnome and kde on my ubuntu and switch between then anytime i like or it's impossible?
Thank you.

---

### Post by stchman on 2008-01-28
> **Hoom@n said:**
> Hello!
Ubuntu has gnome. I wanna experience KDE in my ubuntu too. I dont want to install kubuntu. Can I install KDE in my ubuntu and can I have both gnome and kde on my ubuntu and switch between then anytime i like or it's impossible?
Thank you.

Yes install the following:

```
sudo apt-get install kubuntu-desktop
```

You can then select KDE session at the login screen.

---

### Post by taurus on 2008-01-28
Yes, you can install KDE with

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
Then, you can choose which window manager you want to use from the Options at the bottom left at the GUI login screen.

---

### Post by Whiffle on 2008-01-28
Yes.  

kubuntu and ubuntu and all the other derivatives are not actually different distributions.  They just have a different desktop installed by default, thats all.  Everything underneath is the same.  Here are a couple of good articles:
[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

I for one would recommend not using the kubuntu-desktop package, I've used it and I like vanilla kde much better.

---

### Post by Hoom@n on 2008-01-28
Thank you but could you please tell it a bit easier? I mean what should I do? Should I type it in terminal? or?
Thank you.

---

### Post by taurus on 2008-01-28
Open a terminal, Applications -> Accessories -> Terminal, and type in one line at a time.

---

### Post by LaRoza on 2008-01-28
> **Hoom@n said:**
> Thank you but could you please tell it a bit easier? I mean what should I do? Should I type it in terminal? or?
Thank you.

There terminal way is easy.

You can also install:

```

sudo aptitude install kde-core

```

This is a smaller package than kubuntu-desktop and doesn't install as many programs, just KDE and a few others.

---

### Post by perlluver on 2008-01-28
Yes any sudo apt-get install's go into the terminal.

```
sudo apt-get install kde-core
``` for vanilla Kde or,
```
sudo apt-get install kubuntu-desktop
``` for Kubuntu look.

---

### Post by forrestcupp on 2008-01-28
Or if you prefer to install things with Synaptic, just search for kubuntu-desktop, select it and mark it for installation, then press the Apply button.

---

### Post by jpeddicord on 2008-01-28
If you don't feel comfortable using the terminal at all, you can install the KDE desktop by clicking [here]("apt:kubuntu-desktop"). Once installed, sign out, click the Options menu, and pick KDE for your session.

---

### Post by Hoom@n on 2008-01-28
Thank you. I wanted to use:```
sudo apt-get install kde-core
``` but I got: ```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```
What should I do?

---

### Post by taurus on 2008-01-28
If you have synaptic or Add/Remove open, please close it down before you run those commands from a terminal.

---

### Post by Hoom@n on 2008-01-28
I have just firefox and distribution update open. Should I close them?

---

### Post by Aurora@FleetBuzz on 2008-01-28
Uh oh!  Another itch to scratch!  I've got to try this, but first a few questions:

I am the only user on my computer so I've bypassed the log in screen.  I take it I should enable the log in screen again so I will be able to select which desktop, Gnome or KDE, I want to use for that session?  Is there any other way to select the desktop?

I've read earlier in the thread that all this affects is the desktop; "under the hood" it's the same ubuntu operating system.  Are there any problems that could be encountered by installing kde and gnome on the same ubuntu installation?

For someone like me who is kind of allergic to the terminal, wouldn't installation via the Synaptic Package manager be best?  If I should have to un-install, wouldn't this be the easiest route.

Thanks for any answers.  I'm running Gutsy on a Dell Dimension 8200 if that has any impact....

---

### Post by Hoom@n on 2008-01-28
Sorry what should I do?
+++
after installing kde are gnome and kde seperated or i have everything in both kde and gnome and how can i switch between them?

---

### Post by jpeddicord on 2008-01-28
Installing via Synaptic will work just fine. And yes, you will have to abort the distribution update or wait for it to finish before you will be able to do anything.

There are no problems with having both KDE and GNOME on the same system. The only side-effect is that your menus for both will become cluttered from applications from the other desktop environment.

If you have autologin set, you can change to KDE by going to System > Quit and the Log Out. That should get you to the login screen.

---

### Post by forrestcupp on 2008-01-28
> **Aurora@FleetBuzz said:**
> Uh oh!  Another itch to scratch!  I've got to try this, but first a few questions:

I am the only user on my computer so I've bypassed the log in screen.  I take it I should enable the log in screen again so I will be able to select which desktop, Gnome or KDE, I want to use for that session?  Is there any other way to select the desktop?

I've read earlier in the thread that all this affects is the desktop; "under the hood" it's the same ubuntu operating system.  Are there any problems that could be encountered by installing kde and gnome on the same ubuntu installation?

For someone like me who is kind of allergic to the terminal, wouldn't installation via the Synaptic Package manager be best?  If I should have to un-install, wouldn't this be the easiest route.

Thanks for any answers.  I'm running Gutsy on a Dell Dimension 8200 if that has any impact....

If you bypass the login screen, you can still get to it by pressing ctrl-alt-backspace when Gnome is done loading.  Then in the login screen, you can choose your session.  If you want KDE to be default, you can set it that way in the sessions manager.

---

### Post by Hoom@n on 2008-01-29
Thank you, but I'm sure that I saw a program which makes kde and gnome menus separated. Do you know what's that?

---

### Post by forrestcupp on 2008-01-29
> **Hoom@n said:**
> Thank you, but I'm sure that I saw a program which makes kde and gnome menus separated. Do you know what's that?

[This](http://gnome-look.org/content/show.php?content=31035&forummode=2&forumpage=0&forumexplevel=3&PHPSESSID=f1e0098af05af95ffa7c8a1fb419f9c6) is used in Gnome for the Kde stuff, and [this](http://www.kde-look.org/content/show.php?content=31031&forummode=2&forumpage=0&forumexplevel=3s) is used in KDE for Gnome stuff.

---

### Post by Hoom@n on 2008-01-29
Thank you.

---

### Post by Hoom@n on 2008-01-30
Sorry!
It's KDE 3.5, but I wanted to test KDE 4.0. Please tell me:
1-How can I remove KDE 3.5?
2-How can I get KDE 4.0?
3-How can I change screen resoulution in KDE?
Thank you.

---

### Post by Hoom@n on 2008-01-30
Really no way to uninstall 3.5 and install 4 (i know that i can have both of them but i wanna remove 3.5) Please help

---

### Post by Hoom@n on 2008-01-31
I found [this]("http://www.cyberciti.biz/tips/install-kde-4.html") to install KDE4 and it's correct. Please tell me how to remove KDE3.5?

---

### Post by jaytek13 on 2008-01-31
If you installed kde-core, you can remove everything it installed by doing 

```

sudo apt-get autoremove kde-core

```

---

### Post by Hoom@n on 2008-01-31
Thank you. I gonna test it(i'm updating and can't test now)
+++
And please tell me where is screen resuloution in KDE.
___
Thanks again.

---

### Post by Almumin on 2008-02-07
Open a terminal --> switchdesk kde &
will switch to kde

---

