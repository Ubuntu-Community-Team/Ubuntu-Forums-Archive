---
title: "Installing Xchat .."
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-11-16
How can i install Xchat using an RPM? Or is there another way? Here's the download page; [http://www.xchat.org/download/](http://www.xchat.org/download/)
Also how can i make Xchat compatiable with Mozilla or Konqueror? If possible

Thanks again.

---

### Post by KingBahamut on 2005-11-16
xchat should be included in a default install of Ubuntu. 

if it isnt, just run apt-get install xchat 

What compatibility with mozilla/konq are you driving at?

---

### Post by Kvark on 2005-11-16
Either open synaptic package manager and search for xchat, then mark xchat for installation by clicking the checkbox next to it and click apply.

Or open a terminal and type:
```
sudo apt-get install xchat
```

Then start using it when you've done either of those :)

---

### Post by Rackerz on 2005-11-16
Thanks guys that seemed to work! The compatibility I'm driving at is when i click an IRC link it will launch Xchat.

Also Is it normal that i will have too type 'su' and install things using the root user when installing through the terminal? 

EDIT: Also i don't have a Synaptic Package Manager i have the 'Adept Package Manager'. Is that correct? I know there about the same but i always thought KDE used Synaptic. Thanks!

---

### Post by Kyral on 2005-11-16
Adept is KDE's replacement for Synaptic. I heard its very good, for a GUI app. (Supports Debtags!!)

Also yes, its normal. Though the root account should be disabled by default...

wiki.ubuntu.com/RootSudo for more on the Root thing

---

### Post by Rackerz on 2005-11-16
Thanks Kyral. I was looking through that earlier i enabled it myself :D. Was having troubles and im lazy so i enabled the root account to make things easy.

---

### Post by Kyral on 2005-11-16
Just BE CAREFUL with it. Its easy to shoot yourself in the foot and blow up your system with it. Don't use it UNLESS YOU NEED TO! This means NO LOGGING INTO THE GUI AS ROOT!!

I cannot stress this ENOUGH. BE CAREFUL!!

---

### Post by Rackerz on 2005-11-16
Yep. That's the number one rule i've seen almost everywhere. So not root account for me ;).

---

