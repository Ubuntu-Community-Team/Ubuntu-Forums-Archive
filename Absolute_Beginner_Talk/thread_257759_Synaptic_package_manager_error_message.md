---
title: "Synaptic package manager error message"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by Scarlett on 2006-09-15
When I open Synaptic I get this message:

E: Type 'http://archive.canonical.com/ubuntu' is not known on line 41 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I may have sort of fiddled with some things last night and now I don't know how to fix it.  How do I put it back so I can see the list of everything I can easily download and install?  Thanks.

---

### Post by Scarlett on 2006-09-15
Ok, how about this then...

Can someone tell me what the address is supposed to be for the repository?

---

### Post by Zyzzyx on 2006-09-15
Could you post your sources.list file up, please? That'd help folks to look it over, see if its a simple syntax error or something that you overlooked.

---

### Post by Scarlett on 2006-09-15
I'm sorry, I don't understand your question.  

Where do I find my sources.list file?  Is that different than whatever it seems to be looking for but can't find from my first post?  I'm so confuzzled...  ](*,)

---

### Post by aysiu on 2006-09-15
Paste this command into the terminal: ```
cat /etc/apt/sources.list
``` Then highlight the output, right-click and copy. Then paste the output back into a post in this thread.

---

### Post by Zyzzyx on 2006-09-15
Thanks aysiu, I knew what I was requesting, but being fairly new to all this, wasn't confident enough to explain how to get it.  (sources.list, that is)

---

### Post by Scarlett on 2006-09-15
This is what I get:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

---

### Post by Zyzzyx on 2006-09-15
Yup, that last line is buggering it up. Needs to be in the same format as the ones above. Also looks like you're missing a few of the original repositories.

Take a look at [this thread]("http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2"), it lists the default *sources.list* files.


Now, to see if aysiu posted while I did.  ;)  If not, will probably post with better info.  :D

---

### Post by Scarlett on 2006-09-15
Okay, I typed in the first part in the Terminal and got a sources list window.  Then I typed the rest of it (without the *) and got "Could not save the file /ect/apt/sources.list."

Is there a way to do this without the Terminal?  I have to confess, I don't like that thing, it scares me.

Also, did you get your name from that historic little exit off the I-8 between San Diego and Phoenix?

---

### Post by Zyzzyx on 2006-09-15
OK, first make sure that you have Synaptic closed, or any terminal running apt-get or aptitude. With any of those open you won't be able to write the sources.list file.

In a terminal: *sudo gedit /etc/apt/sources.list*

Then copy/paste the sources.list file.

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
## deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
## deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```


Open Synaptic and *Reload* in the top left.  Or in terminal, run *sudo apt-get update*

I hope that should work. I can understand what your problem is, but I'm also fairly new to all this stuff as well. Think I need to get the directions and explanations down better.  Ah well, with time.



Oh, and yeah...  the nick is from the exit, Zzyzx Rd, on I-15 between L.A. and Vegas.  Did some geology trips out there years ago, the name stuck with me.

---

### Post by Najand on 2006-09-15
You need to use your administration privilages to do that. However as far as there is no root account exists in Ubunut by default, you may use "sudo" command for terminal session and "gksu" for gnome and "kdesu" for KDE.
If you want to edit in graphical environment, use a combination of sudo and  gedit, but as far as gedit is graphical, a command in terminal to edit your /etc/apt/sources.list 
would be like:
```

gksu gedit /etc/sources.list

```

---

### Post by Najand on 2006-09-15
Hmm, Zyzzyx's sources.list ahs not "Universe" and "multiverse" repositories included. I just reorganized your own sources.list, copy and paste it and overwrite your  old sources.list:
> # Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Canonical Repository:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


---

### Post by Scarlett on 2006-09-15
It worked!  Thank you!!  

It's off the I-15?  Heh, it's either a really, really long street or it's been way too long since I've taken a road trip.

---

### Post by Scarlett on 2006-09-15
Wait... you mean I have to do this again? 

...

And here I was so happy just to see some kind of populated list in my synaptic package.  I've been trying for days to install Flash.  If I'm successful with that, I might try Java.  Someday I'll even get around to loading the drivers for my mouse so my back button works...

---

### Post by Najand on 2006-09-15
Hmm, well, if you have Universe Repository, you can have synaptic to install flashplayer for you.
Better to add Universe and Multiverse Repositories.
Then
Open Synaptic and click on "reload"
Then look for "flashplugin-nonfree" and install it.

If you prefer terminal and textbase commands:
```

sudo apt-get update && sudo apt-get upgrdrade
sudo apt-get install flashplugin-nonfree

```

---

### Post by Najand on 2006-09-15
If you want to install JAVA, 
open synaptic and  click on "reload"
then look for "sun-java5-bin"
and install it.

---

### Post by Scarlett on 2006-09-15
I couldn't find flash in Synaptic before.  But then I found a step-by-step guide for getting it and I got all excited, but then when I went to Synaptic nothing was there.  (No doubt because of my fiddling with it last night.) Hopefully I can find it now that I've got your list sucessfully loaded but that's tomorrow night's project.  

Anyway, you guys are just awesome.  Thanks for helping me out.

---

