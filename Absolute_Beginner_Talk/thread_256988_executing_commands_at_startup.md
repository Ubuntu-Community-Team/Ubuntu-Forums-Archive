---
title: "executing commands at startup"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by anurag_gupta on 2006-09-13
hi
i have some hotkeys on my keyboard whihare not recognised by kubuntu. 
dmesg suggests that i should use setkeycodes.
i did. but i hav to use it everytime i turn on my laptop. i s there any way i could executing these commands on system startup.
NOTE;- some of these hotkeys like play,pause,next previous, mute and volume controls were working under ubuntu6.06 (gnome)
is there ne difference in kubuntu n ubuntu

---

### Post by jimmygoon on 2006-09-13
Gnome:

System->Preferences->Sessions

"Startup tab" (3rd tab)

---

### Post by ingo on 2006-09-14
I'm running Xubuntu and would like to do something similar. In Suse I remember there being a boot.local file - anybody know the Ubuntu equivalent?

---

### Post by anurag_gupta on 2006-09-14
thats gud but i want to do it in kubuntu. like guy above is there anyfile (which i can edit) or a script that can be executed at startup. 

i also have suse 10.0 with gnome.

---

### Post by ingo on 2006-09-14
if you have suse then do the following in the shell:

su -l
"input your password"

updatedb (this will take a while)
locate boot.local

the output will give you the location of the boot.local file. Edit this file with your favourite editor and bob's your uncle

---

### Post by anurag_gupta on 2006-09-14
thanx ingo.

---

