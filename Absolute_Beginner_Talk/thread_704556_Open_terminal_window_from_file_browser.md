---
title: "Open terminal window from file browser?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by jmclein on 2008-02-22
I have 2 questions.

1.  I could have sworn that I used to have  the option when I right clicked while in the file browser to be able to "open a terminal window here" that would open a terminal window in the directory I was in.  Is there a program or add on that will allow be to do this again?

2.  Is there a way to setup it up so that I can right click something like a installer and select "Run as root"?

---

### Post by brennydoogles on 2008-02-22
> **jmclein said:**
> I have 2 questions.

1.  I could have sworn that I used to have  the option when I right clicked while in the file browser to be able to "open a terminal window here" that would open a terminal window in the directory I was in.  Is there a program or add on that will allow be to do this again?

2.  Is there a way to setup it up so that I can right click something like a installer and select "Run as root"?

Assuming that you are not using Kubuntu or Xubuntu, you can add your own custom options to the right click menu by placing scripts in your /home/.gnome2/nautilus-scripts/ folder. Here are some scripts that I use regularly ( in the attached tar.gz file) including an open as root command, open terminal here command, and an open ROOT terminal here command. Just extract the folder into the nautilus-scripts folder, and make sure they are all executable. After that, when you right click you will see a scripts option, and all of the script will be in there!!

---

### Post by jmclein on 2008-02-22
> **brennydoogles said:**
> Assuming that you are not using Kubuntu or Xubuntu, you can add your own custom options to the right click menu by placing scripts in your /home/.gnome2/nautilus-scripts/ folder. Here are some scripts that I use regularly ( in the attached tar.gz file) including an open as root command, open terminal here command, and an open ROOT terminal here command. Just extract the folder into the nautilus-scripts folder, and make sure they are all executable. After that, when you right click you will see a scripts option, and all of the script will be in there!!

I looked but I couldn't find the little bowing down smiley guy.  Thanks a ton, this is exactly what I needed!

---

