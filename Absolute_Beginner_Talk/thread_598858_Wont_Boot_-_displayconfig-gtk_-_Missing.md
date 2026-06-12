---
title: "Wont Boot - displayconfig-gtk - Missing"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Fourdee on 2007-10-31
So er, I was trying to clean up my system by removing unneeded packages.

I have the nvidia driver installed and i think i went a bit too far.

When i boot to 7.10 i get this error message:-

"unable to boot as displayconfig-gtk is unavailable - please configure the xorg manually" - Or something similar, didnt have a pen/paper handy.

Ive probably gone over the top cleaning packages and removed this which is probably a core component to the display settings/desktop of my setup and 7.10?

I can boot into recovery mode, but i have no idea what command i need to use to try and resinstall/fix this issue

This is the last time i remove packages when i dont fully understand what they do. I suppose you only learn from your mistakes eh? :) 

Any help would be appreciated, 
Cheers
Dan

---

### Post by greg963 on 2007-11-01
A simple solution would be:

apt-get update
apt-get install -f
apt-get install ubuntu-desktop

---

