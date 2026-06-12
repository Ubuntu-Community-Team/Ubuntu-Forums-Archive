---
title: "this has no effect on my gtk root themes"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-10-01
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

i don't have gnome installed, just a bunch of left over gtk and some gnome apps. i switch between fluxbox and openbox.

---

### Post by phidia on 2007-10-01
Not sure if this [thread]("http://ubuntuforums.org/showthread.php?t=239378&page=14") helps or not. Specifically this part:

>  Originally Posted by thebert  View Post
I have installed Murrine, some themes, and the configurator as outlined in the first post and I am having a lot of problems. Originally when I would apply a murrine them using the configurator it would not apply to some programs such as synaptic package manager. i tried running the configurator again, selecting "none - ~/.gtkrc-2.0" This messed up all of my other themes using the gnome theme selector. No matter which theme i choose now the window border will be from that theme, but the gnome panels and the rest of the programs will be from the murrino theme. I would like to go back to the way I had it before I installed Murrine. Any help would be appreciated.
To have same themes applied also to synaptic I suggest:
Code:

sudo ln -sf /home/your-user/.themes /root/.themes

for the mistake with the gtkrc you have to do:
Code:

rm -f ~/.gtkrc-2.0

and then relesect your theme into gnome theme manager (or relogin)

Then there's [this]("http://ubuntuforums.org/showthread.php?t=89197&page=2") thread on themes which may be getting farther from the target.

Even if my help is none-you'll get a bump out of it. :)

---

### Post by jordanmthomas on 2007-10-01
What you're doing would only work if gnome-settings-daemon is running I think, so you can try running (assuming you have gnome installed) it and seeing if it works after that.

Have you set up a .gtkrc for yourself?  If so, try creating a symbolic link for root to yours.

---

### Post by fuscia on 2007-10-02
whoa! huge mistake. i thought it was fixed, but i was in kde at the time. looks like it was the gtk-qt thing doing the work. ouch!

---

