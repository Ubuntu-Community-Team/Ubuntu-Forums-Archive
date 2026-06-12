---
title: "concerning wine"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by themuddaload on 2007-06-19
where does wine put the files that you install? i cant find where it put mine, so i cant exactly execute anything from a terminal too good.

---

### Post by FleetAdmiral74 on 2007-06-19
Well that depends on where you install them to at the time you installed the program, each one asks you where to install.

---

### Post by RelativelyQuantum on 2007-06-19
Is there any particular reason you want to run applications from terminal? I usually launched any programs I ran  through Wine from the "Wine" folder, located in the applications menu.

---

### Post by themuddaload on 2007-06-19
it said c/ something, but there isnt a c drive on ubuntu, so i am kinda confusilatated. could it have possibly put the files on my win98 drive? (im dualbooting ubuntu and win98)

---

### Post by RelativelyQuantum on 2007-06-19
That can happen. Unless you choose a different directory, the program will be installed to C. Try mounting the C drive through Nautilus.

---

### Post by themuddaload on 2007-06-19
> **RelativelyQuantum said:**
> Is there any particular reason you want to run applications from terminal? I usually launched any programs I ran  through Wine from the "Wine" folder, located in the applications menu.

it doesnt want to run either program i installed on wine by clicking on the.exe on the cd. well it runs star trek elite force, but when i want to begin the game, it says please incert cd, when it is in my drive. and i cant get squat out of stronghold crusader

---

### Post by themuddaload on 2007-06-19
> **RelativelyQuantum said:**
> That can happen. Unless you choose a different directory, the program will be installed to C. Try mounting the C drive through Nautilus.

um, am i gonna hafta get nautilus through synaptic?

---

### Post by FleetAdmiral74 on 2007-06-19
> **RelativelyQuantum said:**
> That can happen. Unless you choose a different directory, the program will be installed to C. Try mounting the C drive through Nautilus.

you think it installed on his Win98 drive? Unlikely, unless he has NTFS write access already installed. Go to your home folder, press control and the H key, and then look for a .WIne folder. Look around in there.

---

### Post by cogadh on 2007-06-19
Wine creates a fake Windows C drive in /home/*username*/.wine/drive_c. It does not know nor does it care if you have a real Windows install on the same computer. The .wine directory is a hidden directory, as FleetAdmiral74 said, just open your home folder and hit CTRL-H, that will temporarily unhide hidden directories and you will be able to see the folder. All of your programs that are installed via Wine are found in this directory. Its folder structure is basically the same as a real Windows C drive.

---

### Post by themuddaload on 2007-06-20
> **FleetAdmiral74 said:**
> you think it installed on his Win98 drive? Unlikely, unless he has NTFS write access already installed. Go to your home folder, press control and the H key, and then look for a .WIne folder. Look around in there.

yeah <ctrl> H did the trick, but i needa dink with it more, cause its still being goofy

---

