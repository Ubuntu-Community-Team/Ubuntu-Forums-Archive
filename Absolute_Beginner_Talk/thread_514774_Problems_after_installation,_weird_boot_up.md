---
title: "Problems after installation, weird boot up?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by revolutionaction on 2007-08-01
After installation of Feisty Fawn on my friends computer we ran into a little snag. The boot up directly after brings us to a weird text screen stating something had an error, and after a couple clicks of "ok" it brings up some text that says something along the lines of 'nvidia, failure to load module.' So its definetly a something to do with the graphics card. After a little bit of browsing around it brings up a text based screen that says "welcome to ubuntu feisty fawn" and has some more text and I'm guessing this is the command line, or terminal? I'm compleatly new to these linux commands so I have no clue on what to enter at this screen. Can anyone offer me any help or a solution at this point because I'm very stumped.

Here are my friends system hardware: 

eMachines T6534

Processor                     AMD Athlon 64 2.2 GHz
Chipset                         NVIDIA GeForce 6100
RAM                                  	 512 MB


Thanx alot to everyone that can help = ]!

---

### Post by retr0virus on 2007-08-01
Well, when you see "Welcome to Ubuntu" you can insert your username and your password.
Don't wonder about nothing beeing visible during the password-input - it's a security reason that Ubuntu does not even show how many letters you typed in for your password.

After you are in the system try to type
```
sudo nano /etc/X11/xorg.conf
```
You will be prompted for the root password (this will be the same password like for the first user on the system - so just type in your password from the login again).
The command will open the "nano-editor" and the xorg-configuration file. In that file you have to find the "Device" Section. There you will find 
```
Driver "nv"
``` or perhaps ```
Driver "nvidia"
``` Try to set it on ```
Driver "vesa"
``` (or if it was "nvidia" try to set it to "nv" first)
Save (Ctrl+o) and quit (Ctrl+x) nano. Then reboot -> ```
sudo reboot
```
Perhaps after that reboot you will see something different than the command-line.

---

### Post by revolutionaction on 2007-08-01
Thanks so much :D!!! I'll let you know how it turns out tomorrow

---

