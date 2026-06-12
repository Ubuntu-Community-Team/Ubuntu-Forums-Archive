---
title: "only got half top panel"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-12-27
[FONT="Comic Sans MS"]Hi, installed Gutsy on a friends box yesterday. Had trouble with the screen resolution so I had the updates run overnight to get 'nvidia-glx' in the repos.
This morning he says the all the screens are really big..etc.
But - he can't get to 'system' because its missing, so is 'places'.
He has in the top panel - applications and user and search and network and sound and date/time and logoff.
We tried 'add to panel' no joy.     Tried 'sudo aptitude install ubuntu-desktop' and then a restart.
Everything came up as it should - for about 5 seconds - then back to previous.
I'm not at his place so I can't see his screen.
Is there a way to fix it in terminal?
He needs the video driver enabled to get his screens back to a normal/readable size, I only know the gui way.[/FONT]

---

### Post by jken146 on 2007-12-27
Screen res need changing?  Ctrl+Alt+F1 puts you in tty1 (no GUI).  Then use these commands:  ```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start
```

---

### Post by carloslosgrande on 2007-12-28
[FONT="Comic Sans MS"]Yeah his screen res is up the spout - needs the driver.
I managed to get to his office. It seems to have fixed itself - he actually had 3 menus layed on top of each other.
Anyway driver is installing now.
If it doesn't work I'll try your answer.
Thanks Jken[/FONT]

---

