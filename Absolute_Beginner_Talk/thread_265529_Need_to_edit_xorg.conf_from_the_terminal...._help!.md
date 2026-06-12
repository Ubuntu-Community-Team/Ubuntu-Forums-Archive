---
title: "Need to edit xorg.conf from the terminal.... help!!"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by TooRight on 2006-09-26
Okay... I admit it... I was fiddling around and had a couple of errors, so followed the directions that that came with the errors to fix it... and I messed up baddddd!! Now, when i log in normally my desktop graphics are all messed up and the windows I open don't show anything correctly, so I can't edit anything that way to undo my little "fix", lol.

When logging into my desktop interface this time (KDE), I chose to run the terminal, thinking i could just edit out the changes I made, then reboot my machine and start xserver. However, I must have my commands wrong.

I was cd-ing into the x11 directory and then typing sudo ed xorg.conf ...it prompted me for my password, I gave it, then all it did was show the number 4950 and nothing else. It didn't even show the little whatever it's called with my username and network thingy and the $, lol

I feel like an idiot, but am really hoping someone here can help me with it, lol...

By the way... Ubuntu stillll rockssss!! Can ya believe my system is messed up and it still gave me the option of searching for help online, and loaded my browser in the corner of my screen?? Try thatttttt with Windoze!! :P hehehe :D

---

### Post by theknave on 2006-09-26
Did you make a backup?

---

### Post by TooRight on 2006-09-26
lmaooo, suuuuuuuuuure ask me something like at in the middle of the night, lol... umm, nope!! Howver, when i went to make the changes in the first place i noticed a file there named xorg.conf~ ... would that be one?

---

### Post by nereid on 2006-09-26
Yes, files with a tilde at the end are usually backups. Just take a look at it and verify that it is indeed a usuable xorg.conf file if not you have to reconfigure your Xserver (sorry, but I don't know the command at the moment).

---

### Post by TooRight on 2006-09-26
cool!! Will try that, thanks so much!!

---

### Post by ske1fr on 2006-09-26
Sometimes files like that (xorg.conf~) can be just the differences you've made to the original file, so they're almost empty!  Yes, I've had to rewrite xorg.conf a few times...#-o but as I'm old and I know just enough of the commands to get the job done, I use vi not ed.

You might find [this howto by Derek Johns useful](http://ubuntuforums.org/showthread.php?t=258186).  If not, the command to use to reset your xorg.conf is 
```
sudo dpkg-reconfigure xserver.xorg
```but **be careful what settings you make**, or you'll make things worse.

Of course, before making changes to such an important file you made a backup of it, didn't you...yes, just like I always remember to...

---

### Post by SkyNet2029 on 2006-09-26
To reset the xorg.conf is :

```
$sudo dpkg-reconfigure -phigh xserver-xorg
```

As for the backup copy of your xorg.conf, you might get lucky and see a file in the X11 directory named 'xorg.conf' followed by a string of numbers (time and date stamp actually) of a previous backup file.
If its there, open it up using 'nano', not 'ed' and change ONE character, then change it back (the charcter I mean). CTRL+X to save changes, and for the 'file to save as', just change the name to xorg.conf (backspace works good to remove all of those extra numbers on the end). If it's there.
Nano does save a backup file whenever you change a file with it,
It's also alot simpler to master as go its commands.

```
$sudo nano /etc/X11/xorg.conf
```

---

### Post by TooRight on 2006-09-26
I'll give it a go.. thanks so much for the responses... i had to boot up in xp this time... guess that wasssss a file with just the changes, because i managed to get it copied and overwrote the other and now my ubuntu/kubuntu won't boot up, lmaoo... okay, I'm writing down this stuff so i can try reinstalling x server... thanks again you guys!!

---

### Post by nereid on 2006-09-26
Ubuntu still should boot, wether the xorg.conf file is empty or not.

---

### Post by TooRight on 2006-09-26
It won't finish booting... I just get the blue kubuntu screen...it does the whole load thing, going through all the different things, then stops at the black background, dark bluw kubuntu (before the logon happens. 

I messed up since i was half asleep and didn't have the "-phigh" in there, so will try again.

Thank again everyone, and good morning!! :D

---

### Post by stilus on 2006-09-26
One of the best things with linux is that it does not depend on "windows"/ a Graphics user interface. 
Try <ctrl>+<alt>+<F1> to get you to a console, and <ctrl>+<alt>+<F7> to get you back to the graphics environment. 

to restart the Xserver after you've made changes (for instance to test your xorg.conf): ```
sudo /etc/init.d/gdm restart
```

Kind regards,
stilus

---

### Post by TooRight on 2006-09-26
Yayyy I'm backk!!

I finally just did a format and reinstall on that drive and then had to search for my ATI video card solution again (I reallyyy have to start keeping notes of all this, lol) I'm getting the packages for Kubuntu now, and i tell ya, I was never so happy to see a splash screen before in my life!! I almost hugged my comp!! lol :P It was killing me to have to boot XP to search the forum for solutions. I have have sooo fallen for Ubuntu, it's crazyyyy. thanks everyone for all your help!!

*sends y'all hugssssss n well wishes that the rest of your day makes you as happy as you've all made me :D

---

