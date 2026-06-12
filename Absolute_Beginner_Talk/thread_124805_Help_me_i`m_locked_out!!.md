---
title: "Help me i`m locked out!!"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-02-02
all i need to know is how to create a new user within terminal. so ican log in and go about fixing the mess i have made. the new user needs a few permissions like i want to be able to change the setting so i can log in as root from the login screen at the beginning. i know this is frowned upon and all but it will make my life easier and i shall change it back shortly :D 

ta DK

---

### Post by Iowan on 2006-02-02
Have you tried the rescue mode from Grub? It drops into a single-user mode (essentially root).

You can use useradd (or is it adduser?) from the terminal to create a new user - but that user won't have sudo rights (without more configuration).

---

### Post by DiscoKiller on 2006-02-02
would anyone know how i might alter the permissions for my home folder to the default permissions through the terminal

my home folder is 

/home/mike

thanks

DK

---

### Post by krusbjorn on 2006-02-02
If it is the owner you need to change, its:

sudo chown -R mike /home/mike/

---

### Post by DiscoKiller on 2006-02-02
basically i`m getting this error message:

Your $HOME/.drmc file has incorrect permissions and is being ignored. This prevents the default session and language being saved. File should be owned by user and have 644 permissions


then i get

Your home directory is listed as 
'/home/mike'
but it does not appear to exist.
Do you want tolog in with the /(Root) directory as your home directory?

It is unlikely that anything will work unless you use a failsafe session.

                                                  Y/N

i click yes and then i get something saying something along the lines of]#

your gnome session lasted less that 10 seconds .....if u have not logged out yourself then this could mean that there is some installation problem or you are ou of diskspace (which i`m not)...try logging in using a failsafe session to see if ucan fix the problem...


HELP :(

EDIT: the sudo chown -R /home/mike gave me an error saying too few arguments

---

### Post by krusbjorn on 2006-02-02
Have you deleted your home folder?

Notice the "mike" after "-R":
sudo chown -R *mike* /home/mike/

But if /home/mike/ doesnt exist, you cant of course change the permissions for it.

---

### Post by DiscoKiller on 2006-02-02
it sems to think i have deleted the home folder, but when i had a look it was there. what i think is happening is that because of the way i changed the permissions ie the read, write + execute permissions, it is ignoring my home folder.   if i could alter the read write execute permissiong for my home fold i stand more of a chance logging in :S

thanks for your help so far btw...i appreciate it muchly. 

DK

---

### Post by krusbjorn on 2006-02-02
Then try:

sudo chmod -R 755 /home/mike

---

### Post by DiscoKiller on 2006-02-02
no luck...think it is gonna have to be reload number 6

---

### Post by wrtrdood on 2006-02-02
Check the directory ownership with ls -ld /home/mike (probably wrong)
Check file ownership with ls -l /home/mike/.dmrc (also probably wrong)

Fix with:
sudo chown mike:mike /home/mike
sudo chmod 755 /home/mike (and any other directory)
sudo chmod 644 /home/mike/.dmrc (and any other file)

The error message you're getting happens when the permissions are wrong.  Directories must have execute to be accessible and I'll bet that's not the case.

---

### Post by bartbes on 2006-02-02
> Your $HOME/.drmc file has incorrect permissions and is being ignored. This prevents the default session and language being saved. File should be owned by user and have 644 permissions I have the same problem.. but I have checked, double-checked, triple-checked and I am the owner and the file has 644 permissions.. it isn't that bad, but it's really annoying!:evil: Try to run X from the terminal ```
 X 
```(first kill X) and post the warning ( if you got one) 
and I had that too, it was because of a file permission of a file (.Xauthority), saved by KDE, the only one that gave that warning...
that's all I know (for now)

---

### Post by DiscoKiller on 2006-02-02
scratch that, i got it working. i think ur commands helped but i`m not enturely sure what i did, just went meddling in the files through the terminal. well i`m back safely in the world of ubuntu, thankyou very much for you time and effort in helping me dude...very much appreciated


DK

---

### Post by krusbjorn on 2006-02-02
Glad it worked out. Try to be a little careful with changing permissions in the future ;)

---

### Post by DiscoKiller on 2006-02-02
sound advice. still learning by making mistakes in this lovely little OS. although i have noticed a drastic improvement in my understanding of ubuntu and linux in general oiver the last couple of weeks thanks to kind people like urselves who are way ahead of me just giving me a little help. ubuntu makes the world go round :D

thanks again to everyone who posted on this thread


DK

---

