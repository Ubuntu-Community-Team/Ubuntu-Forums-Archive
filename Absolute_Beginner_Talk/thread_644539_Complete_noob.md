---
title: "Complete noob"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Rexor on 2007-12-19
Well after 3 weeks of battling a install of ubuntu I have done it. In fact I am posting from it now. Now I have a problem, I have no clue what I am doing, lol. I have a 8800gt that I downloaded the drivers for  "NVIDIA-Linux-x86-169.04-pkg.run" but I have no idea where to go to install them. 

Can someone walk me through the install in very very simple steps?

Thanks

---

### Post by FuturePilot on 2007-12-19
Before trying to manually install the drivers you should check the Restricted Driver Manager for drivers. System>Administration>Restricted Driver Manager.

---

### Post by RomeReactor on 2007-12-19
Hi. You give [Envy]("http://albertomilone.com/nvidia_scripts1.html") a try.

EDIT: But try FuturePilot's suggestion first.

---

### Post by Rexor on 2007-12-19
> **FuturePilot said:**
> Before trying to manually install the drivers you should check the Restricted Driver Manager for drivers. System>Administration>Restricted Driver Manager.

It says my hardware does not need any restricted drivers.

---

### Post by FuturePilot on 2007-12-19
> **Rexor said:**
> It says my hardware does not need any restricted drivers.
Then I would give Envy a shot. Manually installing can sometimes be a bit of a pain. Envy will automate everything for you.
> **RomeReactor said:**
> Hi. You give [Envy]("http://albertomilone.com/nvidia_scripts1.html") a try.

EDIT: But try FuturePilot's suggestion first.

---

### Post by kpkeerthi on 2007-12-19
See [Manual nvidia installation]("https://help.ubuntu.com/community/NvidiaManual") if you are still interested.

When you are ready to install, make sure you have 'execute' permission on the .run file
```

chmod u+x NVIDIA-Linux-x86-169.04-pkg.run

```

Good luck.

---

### Post by Rexor on 2007-12-19
Ok I tried envy and got "envy does not recognize your card as being compatible". Any other ideas?

---

### Post by macogw on 2007-12-19
That'd be manual install time, then.  Put the .run file in your home drive.  Follow these directions: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) but make sure you print out or copy them down (on real paper) before starting since you won't be able to get to Firefox while you're doing this.

In the directions, when it tells you to kill X, you do that like this:
```
sudo /etc/init.d/gdm stop
```
and when you finish and want to bring X back:
```
sudo /etc/init.d/gdm start
```

---

### Post by Rexor on 2007-12-19
Yeah might be a while before I can understand that let alone do it. Thanks for the help, running in 800x600 on my 22" monitor is killing me :( In other words I don't even know where to type that in, yes I am that big a n00b :(

---

### Post by hyper_ch on 2007-12-19
Can you edit the thread title to something more appropriate than just a generic "noob here"?

---

### Post by Rexor on 2007-12-19
> **hyper_ch said:**
> Can you edit the thread title to something more appropriate than just a generic "noob here"?

Done. Well once you get in it is, can't change the outside title for some reason :(

Also after reading the manual install steps I am unsure what folder or directory I need to place the driver file so that I can run it from the terminal when I need to.

---

### Post by RomeReactor on 2007-12-19
You don't need to put the .RUN file in a specific place, but it's easier to just leave it in your home folder; since that's where your terminal opens by default, so you only need run the command:
```
sudo sh NVIDIA-Linux-x86-169.04-pkg.run
```
if the file is in your desktop, when you launch the terminal you'll need to cd (change directory) there:
```
cd Desktop
```
before running the installer.

---

### Post by Rexor on 2007-12-19
Success. The manual installation worked and I am now able to run in 1068X1050 with the nivida drivers. Thanks to everyone for the help. I can't wait to have you guys help with the next issues, untill then keep it shiny side up.

:guitar:

---

