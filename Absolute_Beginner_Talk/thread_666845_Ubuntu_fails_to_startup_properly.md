---
title: "Ubuntu fails to startup properly"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by edwin_cheung88 on 2008-01-13
After logging into ubuntu, I get errors saying that "an error has occurred when loading or saving configuration information for x-session-manager some of your configuration settings may not work properly"

It takes a while to get to the desktop, but when I do get there I'm greeting with lots of error messages that are the same as the one on the top, except it's for nautilus and others like gnome.

Also, "Gconf error:adding client to server's list failed, CORBA error IDL:omg.org/COBRA/COMM_Failure:1.0

I've had some problems before with this, something about x-files not loading or starting, and that occured after I tried to fix my laptop with some allocation errors

---

### Post by Xavieran on 2008-01-13
can you run this command from the terminal...```
sudo rm -rf /tmp && sudo mkdir /tmp && sudo mkdir /tmp/.X11-unix && sudo mkdir /tmp/.ICE-unix
```

This is NOT a malicious command it removes /tmp and all the folders inside it and then recreates it...I had your problem once and solved it by deleting /tmp and then recreating the special folders...

P.S...you will have to reboot after doing this...but hopefully it will work...

---

### Post by edwin_cheung88 on 2008-01-13
Can't find terminal, I usually use my shortcut but it doesn't work, where is the actual location of the terminal?

---

### Post by Xavieran on 2008-01-13
Press ctrl+alt+F1 ...that will take you to a tty terminal separate from the x server...login with your username and password and then proceed with my commands...

---

### Post by edwin_cheung88 on 2008-01-13
Wait... where do I do this? On my desktop? I tried it and it didn't work... are you telling me to do this when Ubuntu is loading up or when Ubuntu is at the login screen

Sorry about this, not that bright of a linux person

---

### Post by Xavieran on 2008-01-13
At the GDM login screen (when it asks you for your password) press ctrl+alt+F1..or boot into recovery mode and type in the commands I gave you...make sure you don't spell them incorrectly:)...(recovery mode will probably be quicker...
Command 1:
```
sudo rm -rf /tmp
```
```
sudo mkdir /tmp
```
```
sudo mkdir /tmp/.X11-unix
```
```
sudo mkdir /tmp/.ICE-unix
```

---

### Post by edwin_cheung88 on 2008-01-13
nvm, it worked...

restarting... I'll see what happens

---

### Post by edwin_cheung88 on 2008-01-13
I'm getting an error

"Your session only laster less than 10 seconds. if you have not logged yourself out, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failseafe sesions to see if you can fix this problem

---

### Post by Xavieran on 2008-01-13
X (my fingers are crossed)

Hope it works...:)

---

### Post by edwin_cheung88 on 2008-01-13
some errors on the startup says that it is unable to creat som dir like /tmp/gpg-KOPhRV: permission denied

---

### Post by Xavieran on 2008-01-13
What are the permissions of /tmp?
Do you have read/write access?

---

### Post by Xavieran on 2008-01-13
Do the commands I told you again and then do ...sudo chmod 700 /tmp

---

### Post by edwin_cheung88 on 2008-01-13
lol, missed the page two.. and I was cleaning dishes for the girlfriend

Mmkay, so do all those command from before and add this at the end?

---

### Post by Xavieran on 2008-01-13
Yep...you got it!:)

---

### Post by edwin_cheung88 on 2008-01-13
mmm, now I seem to be stuck at a loop where it's from the ubuntu waiting sign and a string of commands, the last one being Running local boot scripts 

then it gets to a nice blue screen where I first met my x files error

It says that the display server has been shut down about 6 times in the last 90 secnds. it is likely that something bad is going on. waiting for 2 minutes before trying again on display :O.

---

### Post by Xavieran on 2008-01-13
How was your computer before?

If worse comes to worse you may have to reinstall :(

Make sure you backup important folders or have a separate /home partition...:(

---

### Post by edwin_cheung88 on 2008-01-13
Mmmm, I was thinking of that

My computer has always been leaky.. but i think reinstall might be the best idea.

I was hoping that the boot disc would just repair my boot files somehow

Alright, do you mind helping me out with the reinstall? I'd like to keep the windows dual boot that I have and just wipe this ubuntu out and start out with another

---

### Post by Xavieran on 2008-01-13
Sorry for the slow reply...wesnoth...

Sure,I'll help you reinstall :)

It's actually quite easy to install over ubuntu..

---

### Post by edwin_cheung88 on 2008-01-13
lol, wesnoth? XD Love that game.. I was playing dofus before the laptop died

anyways Something is wrong with my computer, it won't even boot from the live CD anymore... I have a 2 GB pendrive that I'm trying to get the live CD onto so that maybe I can install from there... any suggestions?

---

### Post by Xavieran on 2008-01-13
Does your BIOS boot from CD first?

When the computer starts up there should be some sort of splash screen...sometimes with your computer manufacturers logo on it...it will say something like press F2 to go to BIOS setup...

---

### Post by edwin_cheung88 on 2008-01-13
Yep, BIOS is first,

Then it's stuck on just an underlined white bar on a black screen, with my CD whirling unhappily making noise

---

### Post by Xavieran on 2008-01-13
That is *very* strange...are you sure it's not just taking a long time to load?
Also which version of *buntu are you using?

---

### Post by edwin_cheung88 on 2008-01-13
ubuntu gusty gibbon 7.10

my cd drive has a history of failing, DVDs fail all the time, I'm just thinking that it doesn't like the CD

---

### Post by Xavieran on 2008-01-13
Could be I guess...
If this was a desktop I would suggest checking the cables leading to it,but I don't know how safe it would be to take your laptop apart :)

---

### Post by edwin_cheung88 on 2008-01-13
lol, thats alright

I'm going to be looking into trying to get the boot disk onto my USB key and trying from there

Thanks a lot!

---

