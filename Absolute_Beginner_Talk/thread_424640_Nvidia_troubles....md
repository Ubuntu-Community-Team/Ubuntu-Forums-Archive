---
title: "Nvidia troubles..."
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by holdinout on 2007-04-26
I'm having a hard time PROPERLY installing my Nvidia FX 5200. I first tried using the Restricted Drivers Manager to install, but then graphics would stop before the login screen. So after that, I tried installing the drivers through easyubuntu. It must have been installed wrong since direct rendering isn't supported (glxinfo | grep direct). What should I try to install these drivers?! I want beryl but I am guessing it wants some 3d support :) .  

BTW : Running Xubuntu, Feisty Fawn. I used directions to run easyubuntu one time and don't know how to reverse the changes it made.

---

### Post by zubrug on 2007-04-26
After your install did you
sudo nvidia-xconfig

---

### Post by holdinout on 2007-04-26
No sir, lemme try it...

---

### Post by holdinout on 2007-04-26
Command not found... Could this mean it's not really installed?

---

### Post by zubrug on 2007-04-26
Ya, do a 
sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig

I reboot after that

---

### Post by holdinout on 2007-04-26
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate

---

### Post by holdinout on 2007-04-26
I've looked a few other places too before posting, no luck. Should I just re-install Ubuntu and try again? I'd rather not. If theres a way to re-install with a terminal command, that would be useful since my live cd is scratched.

---

### Post by holdinout on 2007-04-26
WORKED! Don't know what I was doing wrong... I added some repositories mentioned on psychocats or something and tried again.

---

