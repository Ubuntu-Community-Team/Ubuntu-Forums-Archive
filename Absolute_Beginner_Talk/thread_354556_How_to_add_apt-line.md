---
title: "How to add apt-line?"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by smnbrrtt on 2007-02-06
How do you do this:

First step is adding "apt-line" to /etc/apt/sources.list in your Debian. 

If you are an Ubuntu (Edgy Eft) user, use the following apt-line.

deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

---

### Post by aliyanage on 2007-02-06
Hi,

I am not quite sure whether you are trying to explain something or whether this is a question. But I'll give you the answer if this would be a question:

to add a line into the sources.list file you simply just go to following folder:

```
cd /etc/apt/
```

and then you do the following

```
sudo vi sources.list
```

then press "i" to edit the file and once you've add the line type ":wq" and it will save the file.

then do:

```
sudo apt-get update
sudo apt-get upgrade
```

regards
aliyanage

---

### Post by mcduck on 2007-02-06
In Gnome:

1. Open a terminal and run 'gksudo gedit /etc/apt/sources.list'
2. Add the line to the end of the text file and save.
3. Run 'sudo apt-get-update'

---

### Post by smnbrrtt on 2007-02-06
> **aliyanage said:**
> Hi,

I am not quite sure whether you are trying to explain something or whether this is a question. But I'll give you the answer if this would be a question:

to add a line into the sources.list file you simply just go to following folder:

```
cd /etc/apt/
```

and then you do the following

```
sudo vi sources.list
```

then press "i" to edit the file and once you've add the line type ":wq" and it will save the file.

then do:

```
sudo apt-get update
sudo apt-get upgrade
```



Thanks, tried that. Now i have to do this:

You can install packages by the following command:

# apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj 

I put the above line in terminal but nothing seemed to happen - what am i not doing right?

---

### Post by aliyanage on 2007-02-06
hmm... I know it's a quite stupid question but did you put this "#" into the command as well, just wanna make sure we don't miss out any mistakes?

if you did take it out, if you didn't then could you try the following:

```
sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj 
```

or

```
sudo apt-get install libcnbj-2.5
sudo apt-get install bjfilter-2.5
sudo apt-get install pstocanonbj 
```

regards
aliyanage

---

### Post by mcduck on 2007-02-06
it should be 'sudo apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj'. In ubuntu you need 'sudo' to do admin tasks.

The '#' is not a part of the command, it's there to tell you that this is done as root. In the terminal you'll see this symbol when you are logged in as root, and '$' when you are a normal user. These symbols are often included when writinbg down commands, but, as I said, leave them out when running the commands yourself. And use 'sudo' instead of logging in as root :)

---

### Post by ghandi69_ on 2007-02-06
Ok first things first, make sure you are connected to the internet... I'm guessing you are because you are here..

Now, lets make sure you are looking at the right file.  When you navigate your way to the etc directory and then to the apt directory, you can open the file using vi, as mentioned by the user below, but I would recommend using gedit for now, as it might be easier.

sudo gedit sources.list

When you open that file, there should have already been a whole bunch of text there with a lot of http type addresses.  Those are your sources.  The first thing you should do to that file is uncomment out the address that have comments in front of them.  A comment in the source file is the '#' character.  Now, you can go through and do that if you like, or you can just make your sources.list file look like this by coping this in there. 

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen

This information can be found from the starter guide(first link when typing "Getting Started With Ubuntu" into google.  This can be a great source of information when starting.

---

### Post by smnbrrtt on 2007-02-06
Thanks - trying it now.

I didn't know about the #/sudo thing, so that's the 3,461st thing i've learnt about Ubuntu in the last couple of days

---

### Post by smnbrrtt on 2007-02-06
Yes that worked. Now how do i do this please:

you can select printer in cupsys configuration ([http://127.0.0.1:631/)](http://127.0.0.1:631/)). Vendor is Canon and Driver is, for example, "Canon PIXUS iP8600 ver.2.5".

many thanks again

---

