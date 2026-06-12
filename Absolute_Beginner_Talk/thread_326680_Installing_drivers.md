---
title: "Installing drivers"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Naritsu on 2006-12-28
I have a CD that has the linux drivers on it but i have no clue how to install them...

---

### Post by maxamillion on 2006-12-28
drivers for what and what file format are the drivers given in?

---

### Post by Naritsu on 2006-12-28
everything really, the only ones ive tried so far is my chipset driver i dont even really know if i have linux drivers for the other stuff
NFORCE-Linux-x86_32.0-0306-pkg1.run

---

### Post by maxamillion on 2006-12-28
well .. what isn't working? ... linux generally doesn't need many drivers, majority of popular hardware "just works" from a fresh installation and in my case the only thing i installed was the nvidia-glx driver for my video card (available in the optional repositories for ubuntu) and i didn't even need that, just wanted direct 3d rendering.

---

### Post by Naritsu on 2006-12-28
well a lot of stuff in the device manager isnt showing up and i cant get max resolution or use my 2nd screen. now i dont really know how to do anything in linux yet so i have no clue how to do anything with the 2nd screen but when i go to the screen resolution thing it only goes up to 1024x768. oh and my mouse for some reason stops moving every once in a while and i gotta unplug it and plug it back in to get it working again.

---

### Post by logos34 on 2006-12-28
you don't need to worry about the nforce drivers--ubuntu will detect your hardware and install the open source drivers for you.  You do need to put in the nvidia graphics driver though--that'll solve your resolution problems most likely (in not you can edit your xorg.conf  file).  

Go to:
[https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

click on 'Video' link at bottom for install howtos.  read 'Latest nvidia edgy'

---

### Post by Naritsu on 2006-12-28
Got the drivers installed but the resolution is still stuck low, and how would i go about enabling my 2nd screen?

---

