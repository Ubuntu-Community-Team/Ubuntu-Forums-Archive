---
title: "saving my settings for the real version of ubuntu from the live version."
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-10
i am running a live cd because my windows is messed up, and i cant load the mbr to load up windows properly. is there a way that when i get my computer back up perfectly that i can save my preferences of ubuntu currently (cookies, logins, pw's, etc.s) for when i really install it? i need to know what files to save, and i have a internet host to host em. im guessin ill just do a lil host and overwrite once i have the installed version on?

---

### Post by aysiu on 2006-04-10
You want your /home folder and all the hidden folders inside of it.

To see hidden folders in Ubuntu, press Control-H
To see them in Kubuntu, press Alt-V and then H.

---

### Post by dylonium on 2006-04-11
Are the two setting hidden files under my username. I went to home, then to dylan, and now theres .bash_profile and .bashrc

Are those the ones? Or are they in the home file and not the dylan file? Could they be on the cdrom I'm running off of?
I also have / and /2. What should I use as the place to get the home file from?

---

### Post by dylonium on 2006-04-11
[QUOTE=dylonium]Are the two setting hidden files under my username. I went to home, then to dylan, and now theres .bash_profile and .bashrc

Are those the ones? Or are they in the home file and not the dylan file? Could they be on the cdrom I'm running off of?
I also have / and /2. What should I use as the place to get the home file from?[/QUOTE]

Nevermind, it's the actual Home folder. Thanks for everything! Should I just zip it up and save it?

---

### Post by steve.horsley on 2006-04-11
Probably best to tar it up rather than zip it. Tar will retain the file permissions

**tar cvf homefolder.tar .**
shoul do the trick. 

In you new home, extracting it is tricky because you don't want Gnome overwriting the extracted files with its current settings, so do it like this:
1 Copy homefolder.tar to your new home folder.
2 Log out from the Gnome GUI
3 Use Alt-Ctrl-F1 to get a text console, and log in as you 
4 Extract with **tar xvf homefolder.tar**
5 Log out again with **exit**
6 Use Alt-Ctrl-F7 and log into the GUI again
7 All should be right with the world

---

### Post by dylonium on 2006-04-11
Thanks, I'll try this later!

---

