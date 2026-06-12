---
title: "package manager"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-04-14
This morning I was greeted with my update icon.  Expecting my usual list of software and security updates, I clicked and was presented with an error message.  I was told to access apt-get through my terminal.

Here is what I got.

E: Malformed line 53 in source list /etc/apt/sources.list (dist)

Next step?

---

### Post by speeves on 2007-04-14
Hi,

Can you post your /etc/apt/sources.list file, so that we can find the offending syntax error?  If that makes you feel uncomfortable, Iopen your sources.list in an editor and find line 53.  There seems to be a strange character in that line for some reason.  (Could be a missing newline as well, which is fixed be visiting the end of the line and hitting <ENTER>).  Watch for whitespace as well...

---

### Post by djen9999 on 2007-04-14
Thanks Speeves,

I've only been an Ubuntu user for a little over a month.  I've learned a lot so far but how do I gain access to my etc/apt/sources.list file ?

I'm obviously not using the proper syntax.
Thanks again

---

### Post by Max Randor on 2007-04-14
in terminl applications -> accesories -> terminal
type 
sudo gedit /etc/apt/sources.list

and give your password to preform this as root.

---

### Post by djen9999 on 2007-04-14
Thanks Max, it was the gedit that I was missing.

Here's what I got:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb [http://www.albertomilone.com/drivers/edgy/latest/32bitbinary/](http://www.albertomilone.com/drivers/edgy/latest/32bitbinary/)


Thanks for your help.

---

### Post by djen9999 on 2007-04-14
I just checked all of the links in the package and the last one is dead. (line #53 ?) How can I delete it and move on with my life?  :D I could conceivably update by hand but my update manager would still indicate that there is a problem.

At least I know I'm on the right track.

---

### Post by Seisen on 2007-04-14
Type this in the terminal.

```
sudo vim /etc/apt/sources.list
```

This will bring up vim in the terminal. Scroll all the way down to that line and hold the "Shift + I and it should say insert in white letters. After you delete that part do this 
```
:wq
```

This should save the file and exit out of vim. After that you shouldn't have any problems.

---

### Post by djen9999 on 2007-04-14
This is what I got from that:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
                                                              1,0-1         Top

This is just as I got it.  I didn't delete anything or add anything.  That line isn't there but my package manager is still saying that there is an error.

---

### Post by Bachstelze on 2007-04-14
You need so scroll down to the end of the file and delete the last line, it is the one causing the problem.

---

### Post by Seisen on 2007-04-14
You should be able to scroll down in the terminal, you can even use the arrow keys to scroll down.

---

### Post by Seisen on 2007-04-14
Here is what my source list looks like in vim. I am also using feisty too so don't copy mine down.

---

### Post by djen9999 on 2007-04-14
I have no idea.  That is exactly what I got following your code.

Using Max's code again, everything came up in the text editor.  I deleted that line with the text editor and saved it.  I at least got the update manager but it says I'm updated but the icon is still on my tool bar.

---

### Post by Seisen on 2007-04-14
What does it say when you click on the update icon tab.

---

### Post by djen9999 on 2007-04-14
This is the error message when I hover on the update icon.


A error occurred, please run Package Manager form the right-click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error Opening the cache (E: Malformed line 53 in source list /etc/apt/sources.list (dist), E: The list of sources could not be read.)'


I at least have Synaptic back.  I'm going to try a reset and see if that helps.

---

### Post by djen9999 on 2007-04-14
OK!  After restarting the update icon is gone.

Now for something silly.  My trash can vanished!  Gone!  Can't find it anywhere.  How the heck do I get it back?  :D

---

### Post by Seisen on 2007-04-14
Right Click on the top taskbar and select "add to panel" and scroll down till you see the trash icon, click on it and select Add.

---

### Post by djen9999 on 2007-04-14
I actually knew that.  Thanks for the reminder.  I was just a little confused when it vanished for no apparent reason.

In the mean time I got an update notice for the errant Wine update.  Everything seems to be functioning fine now.

Thanks guys.

---

