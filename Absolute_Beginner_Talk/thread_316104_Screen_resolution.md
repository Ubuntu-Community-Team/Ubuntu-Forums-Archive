---
title: "Screen resolution"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by klittzzer on 2006-12-10
Can anyone help me?

I have Ubuntu Edgy up and running yet cannot configure the resolution and refresh rate for my screen. In Windows it is best @ 1280 by 800 with refresh rate of 60hz. The option to set screen preferences will not allow me to select anything other than 1024 by 768 and refresh 61hz.

I have been trying to find the solution in these and other forums for a week now yet have been unable to find out the Horizontal Sync or Vertical Refresh rate ranges for my driver, which is: Via UnichromePro IGP on a Fujitsu Siemens Amilo L7310GW laptop. 

I am pretty sure I can solve this problem given the right advice. If the OS (Ubuntu EEEEEEEEEEEEEEEEEEEdgy) Cannot operate at any other freqqqqqqqqqqqqqqqqqqqqquencies, resolution, is there a Linux distro which is                      compatible with all computers? 

Pleaseeeeeeeeeeeeeeeeeeee exccccccccccccccccccccccuse the typos, I press a key once and it flieeeeeeeeeeeeeeeeeeeeees across the screen. Is this normal for Ubuntu? It has always happened. Are there Linux distrossssssssssssssssss which do not have such inherent problems which make them virtually unusable as this one is?

---

### Post by mpampix on 2006-12-10
Well try to run in console mode the command "sudo dpkg-reconfigure xserver-xorg"

It is a tool which will help you to reconfigure you xserver. It is quite simple to use it, but if you have a question here we are. After configuring the Xserver try (if you are in graphical mode) to kill and restart it with the Ctrl-Alt-Backspace Combo.

Edit: If you cannot find your monitor hsync and vsync frequencies, when asked for you Monitor configuration choose "medium". In that way you will be able to choose manually the resolution and refresh rate that you prefer.

---

### Post by klittzzer on 2006-12-10
Thanks for your reply.

I can't seem to                       get anywhere with the xorg. I select 'Via' yet when I enter Via/S3G Unichromeeeeeeeeeeeeeeeee Pro                  IGP, it stops and says I need to                       enter the bus id.

I can't find anything re specificccccccccccccccccccccations for this screen, driver, or chipset.

Will it be worth my going on trying to setttttttttttttttttt up this or should I ditch Ubuntu and go for an OS which is compatible with my computer (if one exists)?

---

### Post by Kobalt on 2006-12-10
To get other resolutions avaliable you must run this command : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then select the resolutions you want as avaliable by pressing the **spacebar** to chose them. Then, restart X by pressing Ctrl+Alt+Backspace. 
And here you go !

---

### Post by CatKiller on 2006-12-10
> **klittzzer said:**
> Pleaseeeeeeeeeeeeeeeeeeee exccccccccccccccccccccccuse the typos, I press a key once and it flieeeeeeeeeeeeeeeeeeeeees across the screen. Is this normal for Ubuntu? It has always happened. Are there Linux distrossssssssssssssssss which do not have such inherent problems which make them virtually unusable as this one is?

Some people have reported that disabling ACPI can prevent that behaviour with the keys.

---

### Post by klittzzer on 2006-12-10
Thanks Cobalt, mpamp etc

Screen is good now. Typing is still messed up but not as bad.

Gonna try to disable ACPI or whatever that is.

Peace
Klittzzer

---

### Post by MacD on 2006-12-11
Re: keyboard problems.

Have you played with System --> Preferences -->  Keyboard : repeat keys

---

### Post by albatroz2k on 2006-12-15
This worked fine for me. I am using a nVidia 5200 not at 1280x1024 :)
However I have the impression that the refresh rate is not as good as it can.
How can I check it?

> **Kobalt said:**
> To get other resolutions avaliable you must run this command : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then select the resolutions you want as avaliable by pressing the **spacebar** to chose them. Then, restart X by pressing Ctrl+Alt+Backspace. 
And here you go !

---

