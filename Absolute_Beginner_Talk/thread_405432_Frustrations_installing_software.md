---
title: "Frustrations installing software"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by acrosome on 2007-04-09
OK, I am not only an Ubuntu neophyte, but pretty much a computer neophyte, too.  I generally know which files not to erase in Windows, can install software, and can use Office, Explorer, etc.  So you can imagine my frustration that I can't install anything and get it to run in Ubuntu (Dapper Drake 6.06).

Well, that's not totally true.  I got Pingus to run.  Whee.

I'm currently trying to install LGeneral.

I finally figured out the whole dependencies game.  (Thank God someone usually just posts some command line argument for you to cut and paste...)  First I had to install gcc (I got errors saying that I had no C compiler).  Then I installed SDL and the SDL mixer, as recommended.  Finally, I compiled and installed LGeneral and the PG-data package.  Well, I'm pretty sure I did...

Now, whenever I try to run LGeneral my screen goes blank except for this little error box saying "SIGNAL OUT OF RANGE !" in a really coarse font that slowly drifts around.  It looks like an error from my monitor rather than an error from Ubuntu or LGeneral.  It's a brand-new flat screen monitor from Norwood Micro, model F199.

Any ideas?

---

### Post by josephus on 2007-04-09
compile only when necessary.  

the first thing you should do is check in the repository.  go into System->Administration->Synaptic and search for lgeneral

I checked and it's there.  Just click on the box and apply and everything is installed.

---

### Post by aktiwers on 2007-04-09
Or using "apt-get install program name" offens works too.
Like this in terminal:
```
sudo apt-get install lgeneral
```Then type your password.. and its installed!

To run it from Terminal, simply type:
```
lgeneral
```Remember the terminal is case-SenSeTIve.

---

### Post by Maestro23 on 2007-04-09
> **aktiwers said:**
> Or using "apt-get install program name" offens works too.
Like this in terminal:
```
sudo apt-get install lgeneral
```Then type your password.. and its installed!

To run it from Terminal, simply type:
```
lgeneral
```Remember the terminal is case-SenSeTIve.

And if you don't find it, you need to add extra repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by josephus on 2007-04-09
that's right - it's in the multiverse repository.

---

### Post by FakeOutdoorsman on 2007-04-09
acrosome's problem may lie with the refresh rate of the game.  The game may be changing the refresh rate of the lcd monitor to a value that it can't handle.  If a crt monitor is plugged in and the game works then it confirms the refresh rate issue.

---

### Post by FakeOutdoorsman on 2007-04-09
I'm betting if you specify the particular refresh rates for your monitor the game should work.  Only problem is that I couldn't find any specs on the Norwood f199.

1. Open terminal (Applications -> Accessories -> Terminal)

2. Make a backup of your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

3. Edit the xorg.conf file in gedit:
```
gksudo gedit /etc/X11/xorg.conf
```

4. Find *Section "Monitor"* in gedit and add the following to that section *:
HorizSync       30-83
VertRefresh     60-60

5. Save in gedit and restart.

*You need to replace your Horiz Syn and VertRefresh with the specific values for your monitor.  The ones I supplied aren't guaranteed to work for you since they are for my monitor.

---

