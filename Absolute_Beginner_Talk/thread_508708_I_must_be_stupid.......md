---
title: "I must be stupid......"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by CJ1 on 2007-07-24
I have just installed Ubuntu Server ver sion 6 and 7. The installs seem to go alright but once they are done I never can get the GUi to come up, I have tried some different tips that I have read in this forum and others and nothing seems to work. The install was downloaded from Ubuntus site and appears to have downloaded fine. 

Is there something within the install that I'm missing? 


Help.....

---

### Post by nitro_n2o on 2007-07-24
sudo apt-get install ubuntu-desktop

---

### Post by arcticFire on 2007-07-24
The server version doesn't install with Xwindows. If you want the GUI / Desktop you should download and install Desktop version. (If I've understood you correctly)

---

### Post by LaRoza on 2007-07-24
The server doesn't have a GUI, if you want a GUI with a server, the easiest method is to install the desktop edition (same cd), and then run this command: "sudo tasksel" you will get choices, pick "LAMPP".

---

### Post by CJ1 on 2007-07-24
just so that I'm clear the server version does not have a gui at all correct? and there is no gui to download and add to? the only ubuntu os release that has a gui is desktop, correct?

---

### Post by annda on 2007-07-24
you can follow nitro's suggestion and add gui to your server:

```
sudo apt-get install ubuntu-desktop
```

i would suggest adding the gui login manager GDM too, i'm not sure if it is included in the newer version of the ubuntu-desktop package (some time ago it wasn't)

```
sudo apt-get install gdm
```

UPDATE: as i said, i tried this step a long time ago on an old computer, so you might not need this. but if after having installed everything you don't get a graphic logon screen, type 'startx' after you log in for direct launch of X (GUI), or 'gdm' for the GUI login to... well, GUI.

---

### Post by doodaa on 2007-07-24
> **CJ1 said:**
> just so that I'm clear the server version does not have a gui at all correct? and there is no gui to download and add to? the only ubuntu os release that has a gui is desktop, correct?

Not the way I read the thread... I'd try nitro_no2's response.

---

### Post by fastpakr on 2007-07-24
> **doodaa said:**
> Not the way I read the thread... I'd try nitro_no2's response.

You can add the GUI to the server after installation with the command posted above:  sudo apt-get install ubuntu-desktop'.

---

### Post by Orochi on 2007-07-24
If you already have the Server edition installed, run 'sudo apt-get ubuntu-desktop' to download the gui and all the basic programs.

---

### Post by bodhi.zazen on 2007-07-24
> **CJ1 said:**
> just so that I'm clear the server version does not have a gui at all correct? and there is no gui to download and add to? the only ubuntu os release that has a gui is desktop, correct?

1. Stupid people do not ask questions, they just plow forward.

2. On the Ubuntu forums, just ask ...

3. Yes, there is no GUI with the server install. You can install a light weight gui like Fluxbox, openbox, icewm. You can install a light KDE, gnome, or xfce ... You can install the full desktop ...

Lightweight gnome : [http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

4. The desktop and alternate CD's will both come with a gui.

5. The server install comes with the server kernel which is a little different form the desktop or alternated CD.

---

### Post by CJ1 on 2007-07-24
I have tried that command logged in as root and the return message I get is that it cannot find the install
I have lloked at the cd and it is not obvious to me, should I be logged in as root or sudo? Also I'm assuming that the install for the gui is on the CD somewhere? Thanks for the patience just trying to learn.....

---

### Post by dca on 2007-07-24
Is that box connected to the internet?

---

