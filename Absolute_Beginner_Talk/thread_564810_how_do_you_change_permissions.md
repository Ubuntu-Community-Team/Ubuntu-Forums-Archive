---
title: "how do you change permissions?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Rioku on 2007-10-01
Hey, I was wondering how to change permissions? well actualy i know how too... but im having an issue where im not aloud to change permissions in some folders because 

"you are not the owner, so you cant change these permissions"

i have set everything else up (ubuntu rocks!) but now im trying to install a game called tremulous which looks quite fun... but when i try installed it says i havnt got privladges to install to the folder chosen

so i did try and change permissions to allow me to do this but thats my problem i cant :(

can anyone help me out?

---

### Post by Golyadkin on 2007-10-01
Try:
> 
sudo chmod +rwx filename


---

### Post by Perfect Storm on 2007-10-01
Which folders you want to change? Hope not it's some of the system folders. You'll mess up royally if you do.

---

### Post by Rioku on 2007-10-01
the instalation path for the game when trying to install says 

/usr/local/games/quake3/tremulous

when i click ok i get 

no write permission to /usr/local/games

so thats the folder im trying to change to allow me to have permission to install this game

---

### Post by Perfect Storm on 2007-10-01
Don't mess with the permission system. Instead Install tremulous as superuser do;

```
sudo <command>
```

Afterwards exit the installer, don't run the game from the installer window (if it have one), if you don't you'll mess up tremulous permission system.

---

### Post by Rioku on 2007-10-01
well im kind of new to this whole linux thing (altho i did join here awhile ago i never really managed to figure it out but im getting further this time)

i tried what you said in the terminal but i got this back

bash: syntax error near unexpected token `newline'

:S I have no idea what to do, all i know is i have the game on my desktop and after enabling it to run it alows me to install but then i get the problems i mentioned earlier and it doesnt want to install

sorry this id probably very frustrating if it looks like im not listening or something lol im just new to this so i have near to none experience.

---

### Post by Perfect Storm on 2007-10-01
What's the name of the installation file?

---

### Post by Rioku on 2007-10-01
cd ~/Desktop
chmod 755 tremulous-1.1.0-installer.x86.run
sudo ./tremulous-1.1.0-installer.x86.run

iv tried this ? dunno if its right

the installation file is 
tremulous-1.1.0-installer.x86.run

when i tried that comand it asked me for a passoword.. (so i typed in the password i use with my log in id and its not working)

---

### Post by Perfect Storm on 2007-10-01
You can't see the password when typing. It's a protection device.

instead of **sudo ./tremulous-1.1.0-installer.x86.run** you can also try **sudo sh tremulous-1.1.0-installer.x86.run**

---

### Post by Rioku on 2007-10-01
ah i have it working :D thanks very much for your time and patients! really appreciate it

---

### Post by Perfect Storm on 2007-10-01
My pleasure.

If you're looking for gaming guides, I wrote some (more to come);
[http://gaming.gwos.org/doku.php/guides:guides](http://gaming.gwos.org/doku.php/guides:guides)

---

