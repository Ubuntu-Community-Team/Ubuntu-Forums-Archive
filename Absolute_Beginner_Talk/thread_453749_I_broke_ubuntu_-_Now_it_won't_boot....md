---
title: "I broke ubuntu - Now it won't boot..."
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-24
I was trying to "shave off" time from my boot up, so I decided to remove all traces of evolution mail thru synaptic, since I use T-Bird.

After doing that, I decided to reboot to time it; Now, I get to the username/password screens & can enter those, but after the password, it goes to a light brown desktop/ no icons, panels, nothing.

Please help a newbie out - I am completely lost here! ](*,)

---

### Post by melancholeric on 2007-05-24
Sounds like a problem with gnome. Try reinstalling ubuntu-desktop ?

---

### Post by bobplano on 2007-05-24
evolution is tied into the ubuntu desktop meta package so i wouldn't really recommend getting rid of it. i don't think that would really help boot times though unless youre loading it up every time you boot.

---

### Post by discmaster on 2007-05-24
> evolution is tied into the ubuntu desktop I did see something like that when I was going thru synaptic, guess I should have left things alone; 

Problem is, what do I do from here?  I can't get booted to a desktop to do anything, & I don't know how to boot to a "safe mode", such as in windows!

What is my next step?

---

### Post by melancholeric on 2007-05-24
isn't there a single user mode / recovery mode available at grub?

if not, you can <ctrl>+<alt>+<f1> to a terminal and log in there and well, try to fix the problem from there. <ctrl>+<alt+>+f7 should bring you back to gnome (or what's left of it ... )

---

### Post by bobplano on 2007-05-24
after you log in press ctrl+alt+F1. that will get you to a terminal. then you can try reinstalling the package. then you might want to restart your computer (yes with that minute boot) or at least restart X. once you reinstalled it ctrl+alt+F7 gets you back to the GUI

---

### Post by irish_flu on 2007-05-24
Once you get to a terminal, use "sudo apt-get install (program)" to install your packages (like ubuntu-desktop) to try and get your stuff back (since you can't get to Synaptic).

---

### Post by discmaster on 2007-05-24
> after you log in press ctrl+alt+F1. I an do that, enter my name/pswd at the "dos" screen (sorry)!, & then I guess I am at a "root" prompt?

tr is my username;


tr@tr-desktop:~$

what next?

---

### Post by bobplano on 2007-05-24
its not a root terminal, its a virtual terminal, so you still have to use sudo. like irish_flu said once your in a terminal run sudo apt-get update && sudo apt-get install ubuntu-desktop.

---

### Post by discmaster on 2007-05-24
**irish_flu**, just saw your post - I am doing that now. A bunch of stuff installed, now I am back at 

tr@tr-desktop:~$

what from here? The only thing I know to do at this point is press the reset button, & that's probably not the right thing to do!

---

### Post by trak87 on 2007-05-24
> **discmaster said:**
> what next?

Then try this:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by discmaster on 2007-05-24
> once your in a terminal run sudo apt-get update && sudo apt-get install ubuntu-desktop. I did all that, plenty of things "re-installed", but after all that I still end up back at the prompt.

How to get back to the GUI desktop?

---

### Post by bobplano on 2007-05-24
well to just get back to the GUI press ctrl+alt+F7. you might have to do some things before that but try that anyway

---

### Post by discmaster on 2007-05-24
> well to just get back to the GUI press ctrl+alt+F7. back to blank brown screen as before...

---

### Post by bobplano on 2007-05-24
try this in the virtual terminal
```
sudo /etc/init.d/gdm restart
```

---

### Post by irish_flu on 2007-05-24
> **discmaster said:**
> back to blank brown screen as before...

You'll have to restart gnome.  the post above mine will help, if you want to restart the whole box from the terminal you can type:
sudo shutdown -r now
(-r means "reboot", now means now hehe)

---

### Post by discmaster on 2007-05-24
Well mr. bob, it worked!

Thanks to all who participated in this thread & saved me once again! - What an experience that was, LOL! 

I think synaptic should warn you that if "this" is removed, then it will "break" things! :o

Thanks again, guys! :guitar:

@ Thanks Bender!!! :D

---

### Post by irish_flu on 2007-05-24
> **discmaster said:**
> 

@ Thanks Bender!!! :D

Bite my shiny metal oohhhh um you're welcome!

---

### Post by discmaster on 2007-05-24
> Bite my shiny metal oohhhh um you're welcome!

LOL, I have all the seasons on DVD - wish they wouldn't have canceled it... :(

---

