---
title: "terminal help"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Parms on 2007-08-19
I cant get into my desktop from terminal 
 
I used ls and i see desktop, but when I try cd /desktop it says not found.

I'm trying to install a flashplayer upgrade for firefox

/home/parms/Desktop/Ubuntu Downloads/install_flash_player_9_linux.tar.gz_FILES/install_flash_player_9_linux

is what I'm trying to get into

---

### Post by Diabolis on 2007-08-19
cd /Desktop won't work because the desktop folder is already in your home folder, try this cd Desktop (no slash).

---

### Post by Parms on 2007-08-19
nope that doesn't work. I've read the little tutorial on the CD commands and have tried them all. 

I need help starting from the first window.

cd /home works

then when I do LS, I see parms

cd parms puts me at scratch

cd desktop  .. no directory found
cd /desktop .. no directory found
cd ~/desktop .. no directory found

but when I do LS i see it there.
 this is more frustrating than DOS. When I cd in dos everything works fine, for some reason I can't get it to work in ubuntu????

---

### Post by Nekiruhs on 2007-08-19
> **Parms said:**
> nope that doesn't work. I've read the little tutorial on the CD commands and have tried them all. 

I need help starting from the first window.

cd /home works

then when I do LS, I see parms

cd parms puts me at scratch

cd desktop  .. no directory found
cd /desktop .. no directory found
cd ~/desktop .. no directory found

but when I do LS i see it there.
 this is more frustrating than DOS. When I cd in dos everything works fine, for some reason I can't get it to work in ubuntu????
Its not called desktop its called Desktop. Linux is case sensiftive. If your in your home folder do cd Desktop/ if your anywhere else do cd ~/Desktop

---

### Post by aysiu on 2007-08-19
```
cd /home/parms/Desktop
``` or ```
cd ~/Desktop
``` It's a capital **D**, not a lowercase **d**. Case matters.

---

### Post by Parms on 2007-08-19
OK, I did that and I seemed to get in from cd ~/Desktop

I'm trying to reach a folder but am having trouble with each directory. I am using case sensitivity, and also tried to copy and paste all of them, so it's all case sensitive and it won't work.

this is the location I'm trying to achieve
/home/parms/Desktop/Ubuntu Downloads/install_flash_player_9_linux.tar.gz_FILES/install_flash_player_9_linux

that way I can ./flashplayer-installer

thats what the directions say anyways.

so far im in desktop.

---

### Post by aysiu on 2007-08-19
> **Parms said:**
> OK, I did that and I seemed to get in from cd ~/Desktop

I'm trying to reach a folder but am having trouble with each directory. I am using case sensitivity, and also tried to copy and paste all of them, so it's all case sensitive and it won't work.

this is the location I'm trying to achieve
/home/parms/Desktop/Ubuntu Downloads/install_flash_player_9_linux.tar.gz_FILES/install_flash_player_9_linux

that way I can ./flashplayer-installer

thats what the directions say anyways.

so far im in desktop.
Just copy and paste the commands from this website:
[http://psychocats.net/ubuntu/flash#adobe](http://psychocats.net/ubuntu/flash#adobe)

And please, **copy and paste**. Do not retype.

---

### Post by Parms on 2007-08-19
OK.... I got there finally, I just changed my file name so it doesnt have any spaces. It seems like the space doesn't wok. Is there a way around this with out using special characters?

---

### Post by aysiu on 2007-08-19
> **Parms said:**
> OK.... I got there finally, I just changed my file name so it doesnt have any spaces. It seems like the space doesn't wok. Is there a way around this with out using special characters?
Yes. Follow the instructions I linked to above.

---

### Post by Parms on 2007-08-19
errr... I guess I need to do more work since I'm running 64bit. Damn adobe made me waste all that time. Thanks for the link and all the help.

---

### Post by Diabolis on 2007-08-19
> this is the location I'm trying to achieve
/home/parms/Desktop/**Ubuntu Downloads**/install_flash_player_9_linux.tar.gz_FILE S/install_flash_player_9_linux

If you want to CD to a directory like the one above in bold text, you have to do it like this:
```
Ubuntu\ Downloads
```
*notice the backwards slash, otherwise the path won't be recognized.

Try pressing the tab key twice after each letter you type, that will show you all the available options.

---

### Post by asmoore82 on 2007-08-19
I think we are missing the big picture, there is no need for *.tar.gz files to get flash working.

---

### Post by aysiu on 2007-08-19
> **asmoore82 said:**
> I think we are missing the big picture, there is no need for *.tar.gz files to get flash working.
[There is for 64-bit Ubuntu](http://ubuntuforums.org/showthread.php?t=476924).

---

### Post by asmoore82 on 2007-08-19
> **Parms said:**
> errr... I guess I need to do more work since** I'm running 64bit.** Damn adobe made me waste all that time. Thanks for the link and all the help.

yea, no dice.

otherwise you can just take firefox somewhere and "Install Missing Plugins"

---

