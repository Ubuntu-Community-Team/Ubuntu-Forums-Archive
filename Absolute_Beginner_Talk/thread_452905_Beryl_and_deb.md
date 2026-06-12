---
title: "Beryl and deb"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by dhongyt on 2007-05-23
Hey guys, just have some questions about beryl and deb.

I'm trying to install beryl for ubuntu 7.04 and I'm using the website
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

Since I have a Nvidia 8800GTS should I use XGL for it? If not which should I use?

Also I can't seem to get the deb command to work. Everytime I use it it just says command not found, do I have to install something for it to work? If so, what?

---

### Post by Iokua on 2007-05-23
> **dhongyt said:**
> Hey guys, just have some questions about beryl and deb.

I'm trying to install beryl for ubuntu 7.04 and I'm using the website
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

Since I have a Nvidia 8800GTS should I use XGL for it? If not which should I use?

Also I can't seem to get the deb command to work. Everytime I use it it just says command not found, do I have to install something for it to work? If so, what?

I can't answer your question about XGL as I don't use Beryl or any other composites. Be forewarned that this software (Beryl/Compiz) is not yet polished and can introduce a whole minefield of problems.

But "deb" is not a command. The guide is telling you that you need to add the Beryl repository to your /etc/apt/sources.list, which is just the file that stores your repositories. You can do this with the command line, but the easiest way to do this is to open up Synaptic (System -> Administration -> Synaptic).

Then click on Settings -> Repositories. Then navigate to the Third-Party tab. Click on "Add" and add the repository where it says "APT" line.

```
deb http://ubuntu.beryl-project.org/ feisty main
```

---

### Post by perce on 2007-05-23
Actually, in 7.04 Beryl is in Universe, so just type sudo apt-get install beryl you don't need to add repositories. I hadn't to chose any graphic card options. I don't use Beryl often (only when I want to show off with friends), but it's giving me no problems at all, except for making the fan a bit noisier sometimes. However I have an Intel graphic card, so the business might be different for you.

---

### Post by jiminycricket on 2007-05-23
I would also use 'sudo aptitude install beryl' instead of apt-get, so it pulls in recommends such as beryl-manager.  You can also tell Synaptic to consider recommends as depends to get the same result.

---

### Post by dhongyt on 2007-05-24
Okay so I did that and now every window's toolbar at the top isn't there anymore and I can't type in firefox without disabling it. Any ideas?

---

### Post by skyhopper88 on 2007-05-24
Here's the fix from the beryl faq.
" My windows don't have any decorations (title bar, resize handles, minimize/maximize/close buttons)

Before try this, make sure that you have the window decoration enabled at your beryl-manager's settings. It can be the problem.

You can try these solutions by modifying sections of /etc/X11/xorg.conf :
(type gksudo gedit /etc/X11/xorg.conf then enter your password)

1. Try changing DefaultDepth to 24 in the ' Screen ' section if it's not.

2. Delete or comment out with a #, if existing, these entries in ' Section "Module" ' :

Load "dri"
Load "GLCore"

3. Add this entry in ' Section "Module" ' if not present :

Load "glx"

4. Change in Section "Device" the ' Driver "nv" ' entry to :

Driver "nvidia"

if it's not already (assuming you have an nvidia card)
5. Add this entry in ' Section "Screen" ' :

Option "AddARGBGLXVisuals" "True"
(this will probably be what fixes it)
6. Add this section at the end of the file if not present:

Section "Extensions"
Option "Composite" "Enable""

After that close everything on your desktop and save and hit control alt backspace (not delete) to restart X and try berl again.

---

### Post by dhongyt on 2007-05-24
Thanks I will try that.

---

