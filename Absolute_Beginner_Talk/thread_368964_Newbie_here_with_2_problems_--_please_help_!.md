---
title: "Newbie here with 2 problems -- please help !"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-02-23
I have a Toshiba Satellite Pro -- 768 RAM -- 40 Gig hd -- dual boot Ubuntu Dapper and XP. 1. After booting in Dapper I get an error message "The greeter application appears to be crashing. Attempting to use a different one". When I click "OK" there is a place for me to log in as usual, but not the default login screen. 2. After logging in my cd rom light stays on all the time (no disc inserted) unless I open it and leave it that way untill I shut down. Can't think of anything I installed that would be causing this problem. The cd problem was first -- about a week ago, and the log in screen error started about two days ago. Any help would be appreciated very much. This forum has helped me ease into linux from windows with very little pain and anguish -- Thanks everybody !!

---

### Post by Ripfox on 2007-02-23
"Can't think of anything I installed that would be causing this problem"

XP?  :)

---

### Post by jerrynewt on 2007-02-24
Maybe dunno for sure -- XP was on the laptop when I bought it and then I installed Dapper via live cd bout three months ago. No problems until now.

---

### Post by johnc4510 on 2007-02-24
I can't tell you what your problem is, but I can tell you how to check that your splash screen is set up properly:

Your splash image is located here:/usr/share/pixmaps/splash
Go there and write down the exact name of the proper splash image

Now go to:Menu>System Tools>Configuration Editor an click on it
Now click on apps>gnome-session>options
In the white window on the right, you'll see: splash_image under name
Beside it under value you will see something like this:splash/ubuntu-splash.png
That last part, ubuntu-splash.png is the name that should correspond to the name you wrote down.
If it is incorrect, you can edit it by right clicking on the name and choosing the edit key.
This will open a new window where you can put in the correct name.

NOTE: The splash/ at the first of the edit line must stay in and only add the new image name after that.
Save and Close
Ctrl+Alt+Backspace to restart and see if that worked or not
Good luck

---

### Post by guitarmaniac on 2007-03-23
the splash screen has nothing to do with the greeter failing, its the gdm thats crashing.

Try this:
Open a terminal and type > gksu gdmsetupGo to the third tab of the program that opens up and uncheck the box marked "Enable accessible login"
Hope this works for you.

---

### Post by jerrynewt on 2007-03-24
Thanks to guitarmaniac-- worked like a charm. Happy camper now !!

---

### Post by guitarmaniac on 2007-03-25
no worries, I have the same problem but I cant get gdmsetup to start for me, I get this error> luke@swan-desktop:~$ gksudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
glad it worked for you though.

---

