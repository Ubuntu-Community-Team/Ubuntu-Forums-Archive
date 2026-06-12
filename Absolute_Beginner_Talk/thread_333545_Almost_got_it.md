---
title: "Almost got it"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Plosky on 2007-01-07
Using the (excellent!) info on this forum, I managed to netboot  my laptop and installed ubuntu 6.10 .  Everything until there was going fine.  The first it boots, I am prompted to a command line log in.  Nothing alarming because I therefore used the following command to install the desktop :  sudo apt get install ubuntu desktop .

The installation process was long but it finally finished.  The ubuntu loader logo appears when I boot, the progress bar is showing the log-in progrress.  
Here is where the problems start :  The screen the turns black, and nothing.
I can't even switch to another tt? with alt+F?  .
But,when i press the power button to shut down my computer, it does show me again the Ubuntu logo...
If I acces the grub menu and select the "recovery mode" I can successfully login but still no graphical interface..

Did I forget to install a critical package or is my sources.list file not complete enough and some packages were omitted during the install.  Could it be X11 that is acting out or did I simply do something utterly stupid ?

Thanks in advance for your help !

---

### Post by meng on 2007-01-07
CTRL-ALT-F1 should get you a terminal.
Then you can log in and:
sudo dpkg-reconfigure xserver-xorg

What sort of video card do you have?

---

### Post by kebes on 2007-01-07
Hmm... could be any number of things going wrong. First off, when you're at the "black screen" you mentioned that doing Alt+F? didn't work... can you go "Ctrl+Alt+F?" (try everything from F1 through F9). Do you have a console at any of them? Does one of them have the background (kernel) output? There might be an error message there.

Also, when you are at the "black screen" (which is maybe the X GUI trying to load but failing), try going "Ctrl+Alt+Backspace" which reloads the GUI. Does it go back to the terminal and then try loading the GUI again...? (or does nothing happen?)

You can post your sources.list here if you want, but if you didn't receive any errrors during the install of "ubuntu-desktop" then I don't think that's really the problem.


It's probably that your xorg never got configured ... during a normal install this would automatically be done, but via netboot you probably have to do it manually.

I think you go:
Xorg -configure

And then follow the steps. This will generate a basic "xorg.conf" file. Then test it. If it doesn't work you can open it up and fine-tune it.

---

### Post by Plosky on 2007-01-07
my video card is a pretty wierd one, to say the least.  Trident something ..
Sorry for the total lack of precision !
Nonetheless, I will try immedialtely your approach.
Done : It works fine !!!!

Thanks a ton for immediate help.

---

