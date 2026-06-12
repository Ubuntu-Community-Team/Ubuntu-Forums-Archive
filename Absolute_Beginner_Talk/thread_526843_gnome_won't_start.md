---
title: "gnome won't start"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by krauser530 on 2007-08-15
I installed ubuntu a few days ago and everything has been working fine. today i enabled a restricted driver in the restricted drivers menu in hopes ubuntu will better utilize my ATi graphics card. i restarted my computer and now when i log into gnome i get a light brown screen with a white box in the top left corner. I cant type in it. I used ctrl+alt+backspace to restart x and installed fluxbox through the terminal. flux seems to work fine but i cant get gnome to work anymore. any ideas?

---

### Post by Hobo Joe on 2007-08-15
Boot into recovery mode, then type:
```

sudo aptitude install envy

```
Then type
```

envy -t

```
Select 'uninstall ATi driver', then once it's done select 'install ATi driver', make sure to let it configure your xorg for you.

---

### Post by krauser530 on 2007-08-15
what is envy? its not in the ubuntu repository that i can tell.

---

### Post by Hobo Joe on 2007-08-15
It's a app that uninstalls/installs your drivers for you, and configures your xorg.

It is very good at fixing things like this.

---

### Post by krauser530 on 2007-08-16
it cant find envy. is there a repository i need to enable or is there another way to obtain it?


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package matching "envy".  However, the following
packages contain "envy" in their description:
  alsa-tools-gui 
The following packages have been kept back:
  libvorbis0a libvorbisenc2 libvorbisfile3 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Hobo Joe on 2007-08-16
Try this instead:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu7_all.deb

```
Then run these commands:
```

sudo aptitude update

sudo aptitude upgrade

```
Then start back up at 'envy -t' in my other post.

---

### Post by krauser530 on 2007-08-16
that seemed to have worked thanks for the help

---

### Post by Hobo Joe on 2007-08-16
> **krauser530 said:**
> that seemed to have worked thanks for the help

So gnome loads up properly now? Or were you just saying that Envy installed?

---

### Post by krauser530 on 2007-08-16
yeah envy loaded and i reinstalled everything but gnome still wont start

---

### Post by Hobo Joe on 2007-08-16
Any error messages or anything? :-?

---

### Post by krauser530 on 2007-08-16
none just the standard ubuntu background and a white box

---

### Post by krauser530 on 2007-08-16
i tried reinstalling gnome but that didnt work

---

### Post by Hobo Joe on 2007-08-16
Ok, I have another idea.
```

sudo aptitude purge gnome-desktop

sudo aptitude install gnome-desktop

```

Also, post your xorg.conf file by typing this:

```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by krauser530 on 2007-08-16
using gedit made ubuntu crash. the screen went blank and i had to restart the computer

---

### Post by krauser530 on 2007-08-16
i have ubu on a seperate partition from my files so i think i may just try to reinstall it.

---

### Post by krauser530 on 2007-08-16
thanks for the help anyways

---

### Post by Hobo Joe on 2007-08-16
Did you try purging and re-installing first? I'd try that before the re-install.

---

