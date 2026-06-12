---
title: "Moving files, hopefully a quick fix"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by barrack on 2006-07-07
Hey all,

I am very new to Ubuntu and to Linux. I have read as much as I can before actually *doing* stuff that wasn't already installed with the OS. At the moment, I am jsut testing my skills by doing minor tasks.

Currently, I am tyring to change the firefox icon from the globe that came installed w/ Ubuntu to the standard one that firefox uses (it's a very nice logo, i'm a big fan.)

These are the issues that I found and can hopefully get some answers on.

1- I opened up the properties when I right-clicked on the icon in the panel. There I saw that I could choose an icon. When I navigated over to the folder where the new icon is, the icon (a .png file, like the original icon) did not show up and I couldn't select it.

2- Figuring that all icons had to be in a certain folder, I thought I could just move the file over using a click-n-drag technique. It then said thatg access was denied.

3- Then I recalled that I could use sudo in a terminal and use the command line prompt to move the file over. This, I thought, would allow me to bypass the restriction. It didn't.

This is what I typed in and what I got back. 

guest@bc4m-PowerBook:~/rando$ sudo mv -i -v firefox.png /usr/share/pixmaps
Password:
guest@bc4m-PowerBook:~/rando$ sudo mv -i -v firefox.png /usr/share/pixmaps
guest@bc4m-PowerBook:~/rando$ mv -i -v firefox.png /usr/share/pixmaps
mv: overwrite `/usr/share/pixmaps/firefox.png', overriding mode 0644? y
`firefox.png' -> `/usr/share/pixmaps/firefox.png'
mv: cannot move `firefox.png' to `/usr/share/pixmaps/firefox.png': Permission de nied


The icon remains unchanged. If there is something small that I overlooked, I would appreciate the heads up. This isn't a major deal for, it's more for me to get acquainted with using linux and Ubuntu.

Also, if i'm using sudo wrong, please let me know. The first line I typed in with sudo and then the command... well nothing happened. But when I did it again w/ out the sudo, it at least told me something.

Thanks in advance!

---

### Post by lokirulez on 2006-07-07
Try copying it instead of moving it with the cp command. Or you can try changing the read/write properties of the file via chmod. Try ```
sudo chmod 777 filename.png
``` then you should be able to do whatever you want with that file.

---

### Post by Dr. Nick on 2006-07-07
Cant answer your specfic post at the moment, but if you want to change the icon you can also right click it and hit properties, you will see the icon with the blue globe, then open up nautilus and navigate to the folder with the icon you want to use. move the nautilus window off the screen some so that you can see the properties window for firefox, then click and drag the new icon over on top of the blue globe and release the mouse. That should change it for you.

Be aware though that you can not move/remove the icon file or the icon will dissappear.

---

### Post by aysiu on 2006-07-07
I think the problem is just that you're replacing the wrong icon, not that the icon isn't being replaced.

Try [this script](http://www.ubuntuforums.org/showthread.php?t=199193) instead.

---

### Post by firebadger on 2006-07-07
You are using sudo correctly.  As used it will execute the command as root.

However, something very odd is happening there.  The first command should have worked, but if it had the second command would have said...

>mv: cannot stat `firefox.png': No such file or directory

...as the file had been moved from the current directory.

The third command executed without sudo indicates the file is already in the destination location and as you are only running as guest this time you don't have permissions to everwrite it.

---

### Post by barrack on 2006-07-07
> **firebadger said:**
> You are using sudo correctly.  As used it will execute the command as root.

However, something very odd is happening there.  The first command should have worked, but if it had the second command would have said...


I have tried some other commands and nothing seems to happen when I do the sudo. When I do the same command with out sudo, it actually performs the -i and the -v options. Below is an example of what I mean, it just takes me back to prompt as if I didn't do anything.

guest@bc4m-PowerBook:~/rando$ sudo mv -i -v firefox.png /usr/share/pixmaps
Password:
guest@bc4m-PowerBook:~/rando$ 

[In a somewhat related note, is there is shortcut to do copy and paste? I keep right clicking and selecting, but since my right click is the F12 key, it's kinda frustrating. I tried what I thought might be the default, CTL+C etc... anyway, sidetrack, sorry.]

Dr. Nick: Thanks for this shortcut! It changed the icon nicely. I am still trying to work on getting the sudo command to work though, as I will need it for other things.

aysiu: I read the thread and it is helpful. There were some other methods discussed for changing the icons within the Firefox and Thunderbird programs. These also involved copying files and pasting them. As yet, it isn't working. The script sounds perfect, but this is mostly an excercize for me to better understand and use the terminal commands.

---

