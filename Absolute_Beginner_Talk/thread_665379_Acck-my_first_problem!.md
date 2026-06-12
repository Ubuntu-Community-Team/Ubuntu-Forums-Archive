---
title: "Acck-my first problem!"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by betsy_kevin on 2008-01-12
Hiya-
I just finished installing (successfully I think) 7.1 on my old compaq presario with a sort of new emachines 17 wide screen monitor. The first time I booted up, I got a post and ubuntu started to load - then the monitor started to flash a psychedelic venetian blind pattern. Does anyone have any experience with this? This is absolutely the first time I've tried Linux so I have no idea what's going on. Thanks!:confused:

---

### Post by lgambett on 2008-01-12
The X server (ie the engine behind the graphic interface) is not correctly configured or your hardware is not supported. Try to reconfigure it;
- while the monitor is flashing press Ctrl+Alt+F1
- this should bring you to a non graphical environment. Enter your username and password (as defined during the install process), then try to reconfigure X giving the command;
sudo dpkg-reconfigure xserver-xorg
The system will pose you a lot of questions; if you do not know the answer use the default.
At the end of the process try to start X again with the command
startx

Good luck !

---

### Post by betsy_kevin on 2008-01-12
Thank you!
That worked, as an additional note, I entered the horizontal and vertical screen values (suggested in another faq) which helped greatly. I also checked the side screen box when I got back to the gui and picked the correct rez.
Regards - Kevin :)

---

