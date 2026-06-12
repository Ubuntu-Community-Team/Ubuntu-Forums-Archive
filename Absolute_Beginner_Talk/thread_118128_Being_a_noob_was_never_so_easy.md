---
title: "Being a noob was never so easy"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by MuNkY on 2006-01-16
So yesterday i had a hunch to try out ubuntu but had to make sure i sitll have windows installed.so i left my C: partition on windows made another D: partition with 5Gb which would be used to transwer some files through windows-linux and made 2 linux partitions (both reiserFS) 20Gb :/ and 30Gb /data and left around 1Gb of swap.

so the installation was done without problems,i got into the ubuntu,even installed my graphic card drivers,downloaded aao for linux but now it doesn't want to start up...i can't even open files,uninstall aao,move it to thrashcan...in other words,i think i might screw something up :) so if anyone has any idea what i'm talking about or how to help,you might start by posting here and helping me being a little less nooby :)

i thank you in advance.

---

### Post by Stealth on 2006-01-16
Ubuntu isn't working? Do you get to your login screen or...is it from early on in the boot (in the GRUB menu?)

---

### Post by skirkpatrick on 2006-01-16
I think he means that AAo isn't working but I could be wrong.

I've installed AAo on my machine (haven't played it much though).  Can you be a little more specific?  And remember, it may take me several hours to get back to you :)

---

### Post by Sef on 2006-01-16
If  you downloaded aao through the repositories via Synaptic or the terminal, you can uninstall it by using Synaptic.

---

### Post by MuNkY on 2006-01-16
not uninstalling :)

well i get into the ubuntu,downloaded aao file,installed it correctly (into local/games/aao) doubleclicked the icon,nothing happened,tried to run it via synaptic,nothing happened,but i installed my graphic card drives via synaptic...but didn't help...

---

### Post by kakashi on 2006-01-16
ok things is you can't delete the file through thw fiule manger cuz your naormal user has not permissions to do so. 

try this to delte  the file 
rm -R /usr/local/aao

did you install int from source. if so and you did not set the prefix then that is just one of the installed directories.

---

