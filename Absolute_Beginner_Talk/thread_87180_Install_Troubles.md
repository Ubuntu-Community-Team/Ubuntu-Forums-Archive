---
title: "Install Troubles"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by Alias on 2005-11-07
hey guys, firstly i am a complete newbie to linux, but decided to try the unbuntu distro after reading a bit about it. im currently stuck installing it, it gets to the bit where it installs the grub loader to 50 %, then it goes to a black screen with a flashing dash, comes back to the install status screen loads to 33% and goes back to the black dash screen. i restarted and can get into the terminal but cant access the gnome GUI. is there a command to run Gnome or do i need to reinstall in a different way. im keen to learn and help would be much appreciated. im running an AMD Athlon PC and installing linux on a clean drive.

---

### Post by manicka on 2005-11-07
How long are you waiting after the second time it goes blank, before restarting?

---

### Post by Alias on 2005-11-07
it just loops that process, goes to black screen with flashing dash, back to status screen - 33% back to black screen . i normally wait for that to loop a couple of times and just decide that its stuck looping it then restart. ive tried to install a few times now. id just like to know how to run the GUI from the terminal. luke@unbutu-$

the dash is actually a squiggly line but this ghetto laptop im using doesnt have the squiggly button.

---

### Post by tonysathre on 2005-11-07
run sudo startx, or sudo startgnome(not sure about the second one, it might be sudo startgdm, just try them)

---

### Post by Alias on 2005-11-07
tried it and it doesnt work.
just says "sudo : startx: command not found"
with startx replaced for each command respectively.:confused: :confused:

---

### Post by tonysathre on 2005-11-07
hmm, thats weird cause i know that startx is the command.
it sounds like u havent installed properly, try reinstalling ubuntu

---

### Post by Alias on 2005-11-07
i dont get what to do because i get the same thing every time to install ? it must be something to do with Grub but i can't work out what.

---

### Post by tonysathre on 2005-11-07
u might have a bad ISO image, dont know if this is the problem but try redownloading and burning at a slow speed, or try checking the checksum value to make sure it is valid, otherwise im stumped

---

### Post by Alias on 2005-11-07
what is the difference between the grub and lilo loaders ?

---

### Post by manicka on 2005-11-07
I don't think that grub or lilo is your problem. You don't seem to be getting that far into the install process. If the checksum is okay on your iso image, try burning a new disc on a lower speed.

---

