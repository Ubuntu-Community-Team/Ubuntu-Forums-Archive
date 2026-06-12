---
title: "Synaptic Package Manager Problem"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by shonts on 2006-11-07
Well I cant figure out what i did to screw this up. I know i went into the menus to change some configurations. I should have just left things alone. 

-------------------------------------------------------------------
This is my error when i start the package manager:

E: Malformed line 2 in source list /etc/apt/sources.list.d/dapper-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
-------------------------------------------------------------------
When i click on reload it gives me this error:
Could not download all repository indexes

then:
E: Malformed line 2 in source list /etc/apt/sources.list.d/dapper-universe.list (dist parse)
E: Unable to lock the list directory
-------------------------------------------------------------------



As usual, thanks for the help

---

### Post by Perfect Storm on 2006-11-07
How's your sourcelist looks like?
```
cat /etc/apt/sources.list
```

---

### Post by SunnyRabbiera on 2006-11-07
Usually when I get errors like this it doesnt effect much.
I only get it once in a while.

---

### Post by shonts on 2006-11-07
How's your sourcelist looks like?
Code:

cat /etc/apt/sources.list



Im in over my head, LOL

you'll have to explain to me what you want me to do. Dont skip any steps please

---

### Post by taurus on 2006-11-07
Open a terminal, Applications -> Accessories -> Terminal, and type this command in there...

```
cat /etc/apt/sources.list
```
Paste the output (the whole thing) here.  You can use your mouse to do the cut 'n paste.  Highlight the text with the left button and paste it with the middle if you have middle button or hold both left and right down as the same time to emulate the middle button...

---

### Post by shonts on 2006-11-14
Sorry it took me so long to get back, Ive been busy with out of town work. 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe

---

### Post by taurus on 2006-11-14
Here is your new /etc/apt/sources.list.  Look closely at the last three lines...

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ edgy-security main restricted
deb http://security.ubuntu.com/ubuntu/ edgy-security universe
#deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe

```

So, if you want to modify your /etc/apt/sources.list, open a terminal and type

```
gksudo gedit /etc/apt/sources.list
```
After making the changes to the last three lines, save it and run these two commands again...

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ciscosurfer on 2006-11-14
How does modifying the edgy-proposed line affect any change?  Shouldn't the OP be looking at line 2 in source list /etc/apt/sources.list.d/dapper-universe.list due to it's malformed state?

---

