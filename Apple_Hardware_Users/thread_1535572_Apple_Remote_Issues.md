---
title: "Apple Remote Issues"
date: 2010-07-21
forum: Apple Hardware Users
---

### Post by GavinRoskamp on 2010-07-21
Ok folks, I know that there's been plenty of other threads out there about this, but I'm looking for a clear-cut, step-by-step method of how to get this stupid Apple Remote to work with Ubuntu 10.04 on a Mac Mini Early 2009 (I believe it is MacMini3,1) and the basic video programs like Totem. It would be super-mega-ultra awesome if it would work with Hulu desktop as well, but that's just a novelty at this point.

So far, I've done some stuff to my system like downloaded and installed lirc, whatever it is, the gnome infrared remote control settings thing off the Ubuntu Software Center (and again via terminal when trying to follow an install guide...), and I've got it working... in the preference window. In the test part, I can hit buttons and it says stuff like VOLUMEDOWN or whatever, but outside of this, no applications seem to be listening to the remote. I've set it up correctly in there, and the thing that gets me is that when I go to customize the remote control settings and choose the from the standardized list of outputs, it just doesn't save them. I go back to the main preference window and test it out and I still get the same old commands. Am I not pressing something?


Anyway, I'd really appreciate it (and so would every other person who has had to fight the stupid Mac Mini to get Ubuntu working on it correctly) if someone out there who is not as much of a Linux n00b as me to post an EASY to follow step-by-step method to get this remote working. Model number A1156, made by Apple. I don't remember what the IR receiver's specific name is, but it's like Built-In IR Receiver.

Anyway, I, along with tons of other people, would love you to death if you could help us get this working. Thanks!!!

-Gavin

---

### Post by LtPitt on 2010-07-22
My remote worked almost out-of-the-box using xbmc & lirc

Give it a try!

---

### Post by Nikos.Alexandris on 2010-07-22
> **LtPitt said:**
> My remote worked almost out-of-the-box using xbmc & lirc

Give it a try!

What and where is xbmc?

Thanks, Nikos

---

### Post by Nikos.Alexandris on 2010-07-22
> **Nikos.Alexandris said:**
> What and where is xbmc?

Thanks, Nikos

OK, I have it. A quick apt-cache search showed nothing and... well, here it is:
[[COLOR="Blue"]http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step[/COLOR]]("http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step")

---

### Post by hotbdesiato on 2010-08-03
> **Nikos.Alexandris said:**
> OK, I have it. A quick apt-cache search showed nothing and... well, here it is:
[[COLOR="Blue"]http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step[/COLOR]]("http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step")
I have still the same issue like Gavin that my Apple remote control is recognized by the Ubuntu Infrared Remote Control, but not in any other application which I have tested even in the newly installed XBMC (following the above installation instructions). So I do not know how can I fix that.

@LtPitt: __Did you change anything in the default settings of XBMC?

Thanks for further suggestions....Hendrik

---

### Post by vdubeau on 2010-09-16
I too would be interested in a definitive guide. I have the same situation as Gavin. I'm running a MacBook (Santa Rosa 3,1). In OS X I also use it for a media center and the only thing keeping me from doing a complete switch to Ubuntu is not being able to use the remote.

So, please, any gurus out there?

---

### Post by smoors on 2010-10-21
Hi,

just bringing this up again because i've exactly the same issue :) I was soooo pleased after seeing this shiny infrared dialog, but nothing happens outside. Do we need to customize the lirc configuration by hand??

---

