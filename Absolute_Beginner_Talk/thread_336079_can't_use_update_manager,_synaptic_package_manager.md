---
title: "can't use update manager, synaptic package manager,  Automatix or add/remove program"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Scott A on 2007-01-11
hello and thanks in advance for the help!
I can't use update manager, synaptic package manager,  Automatix2 or add/remove program 

For example when I try to do Update manager I get the following error message:
[PHP]
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/PHP]

Then I do Alt-F2 and put in  [PHP]sudo apt-get install -f[/PHP] into the line to type in and hit the RUN button. The box (window) disappears, but when I go back to update manager, I get the same error message. 
Scott A ](*,)

---

### Post by housam on 2007-01-11
Try to update your repos. through this :[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

---

### Post by Scott A on 2007-01-11
Hi Housam, 
I followed the directions, but it did not work. 

Then I tried to follow the directions for the troubleshooting part at the end that said this: [PHP]	

Troubleshooting
Apparently, some people have been experiencing errors even after following this tutorial. There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this:

Back up the sources.list you got from this tutorial with this command:
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

Then edit the sources.list by typing
sudo nano /etc/apt/sources.list
and delete everything.

sudo aptitude update
with your empty repositories list.

Finally,
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
sudo aptitude update

Page updated 01/11/2007
[/PHP]

It said to "delete everything" but it never gave a popup window with things to delete. 
How do I get that screen to delete what I am supposed to delete?

Scott A ](*,)

---

### Post by rai4shu2 on 2007-01-11
Instead of nano, try using gedit or kedit.

---

### Post by housam on 2007-01-11
Can you post the output of the following code : ```
cat /etc/apt/sources.list
```

---

### Post by Scott A on 2007-01-11
when I do cat /etc/apt/sources.list the box disappears. when I check the box to run in the terminal, the bigger black box appears with nothing in it, and then disappears immediately. 

What is  "nano" "gedit" or "kedit"

I am really a newbie at ubuntu and linux

---

### Post by rai4shu2 on 2007-01-11
If you use "nano" that will give you a terminal editor. In Gnome "gedit" is the default text editor, and "kedit" is a simple text editor for KDE.

---

### Post by jvc26 on 2007-01-11
gedit is a text editor. To launch a file (for instance your sources.list) in a way you can edit, type:
```

sudo gedit /etc/apt/sources.list

```
That should open a gedit window with the sources.list file in i  - the same goes for test files:
```

sudo gedit /path/to/file

```
Will open the gedit window with the file
Then you can edit the file as you like, press save and then exit gedit.
Il

---

### Post by PriceChild on 2007-01-11
please could you open up a terminal (applications>accessories>terminal) to do these commands... the output stays even if the program finishes unlike alt+F2

Then please post the ouput once you copy and paste this in:
```
sudo apt-get -f install
cat /etc/apt/sources.list
```

---

### Post by PriceChild on 2007-01-11
> **Illuvator said:**
> gedit is a text editor. To launch a file (for instance your sources.list) in a way you can edit, type:
```

sudo gedit /etc/apt/sources.list

```That should open a gedit window with the sources.list file in i  - the same goes for test files:
```

sudo gedit /path/to/file

```Will open the gedit window with the file
Then you can edit the file as you like, press save and then exit gedit.
IlPlease use gksudo instead of sudo for graphical apps in gnome, kdesu for kde, see [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Scott A on 2007-01-11
Hi, 
I tried that but I still can't use update manager. 

Are there step-by-step proceedures, all on one page, that I don't have to try to do part of one set of directions mixed with other directions, hoping I mix them perfectly? 

I really don't know what I am doing, and it is questionable at best that mixing instructions  from two sources (from this forum and the [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) web page) at once is working. 

Sorry guys, I really do not know much about ubuntu or linux.

---

### Post by jvc26 on 2007-01-11
> **PriceChild said:**
> Please use gksudo instead of sudo for graphical apps in gnome, kdesu for kde, see [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Ah - I'd never seen that before - thanks for the heads-up :)
Il

---

### Post by jvc26 on 2007-01-11
To add new repositories, here is the instructions:
1/ Launch a terminal ->Applications->Accessories->Terminal
2/ Type:
```

gksudo gedit /etc/apt/sources.list

```
It will ask you for your password, put it in.
3/Then a gedit window will open up. Select everything in that file and press <delete> or <Backspace>
4/Copy this stuff into the window (copy and paste)
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```
5/ Then click 'save' and press the x in the top corner of the screen
6/ Go back to the terminal, type:
```

sudo apt-get update

```
7/ Once that completes go to the update manager and run it.
8/ If that works, excellent, if it throws up errors, tell us whats the new problem.
Il

---

### Post by PriceChild on 2007-01-11
> **PriceChild said:**
> please could you open up a terminal (applications>accessories>terminal) to do these commands... the output stays even if the program finishes unlike alt+F2

Then please post the ouput once you copy and paste this in:
```
sudo apt-get -f install
cat /etc/apt/sources.list
```Help us to help you.... do what I've asked please :)

Every situation is different and we NEED to find out what is wrong before we can fix it.

---

### Post by Scott A on 2007-01-13
When I do:
> sudo apt-get -f install
cat /etc/apt/sources.list

I get:

> saurand@saurand-desktop:~$ sudo apt-get -f install
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
saurand@saurand-desktop:~$ 


---

### Post by jvc26 on 2007-01-13
Have you tried:
```

sudo dpkg --configure -a
sudo apt-get -f install

```
That may help you get the answers from:
```

cat /etc/apt/sources.list

```
Il

---

### Post by Scott A on 2007-01-13
Hi, I did the:
> sudo gedit /etc/apt/sources.list

and the sources.list (/etc/apt) - getit box popped up. 

What do I do with the > sudo gedit /path/to/file?

You also said "Will open the gedit window with the file
Then you can edit the file as you like, press save and then exit gedit."

I have no idea how to edit the file. 

I really am a newbie. 

Scott A.

---

### Post by TheRingmaster on 2007-01-13
> **Scott A said:**
> Hi, I did the:


and the sources.list (/etc/apt) - getit box popped up. 

What do I do with the ?

You also said "Will open the gedit window with the file
Then you can edit the file as you like, press save and then exit gedit."

I have no idea how to edit the file. 

I really am a newbie. 

Scott A.



all you have to do is copy and paste the whole document, just like you would with windows, on this thread.

---

### Post by jvc26 on 2007-01-13
I put up a corrected instruction by the way a bit ago:
```

gksudo gedit /etc/apt/sources.list

```
This will open a gedit window with a load of text in it, to edit the text click in the box, and you can type, as you can in any text editor. The sources.list I posted up, you can select it, right click copy, select all the stuff in your sources.list file, delete it and paste in the one I put up (right click on the now empty gedit window where all the writing was displayed before and select paste). Finally, click on the little button which says save on it, then close the gedit window.

Go back to your terminal and type:
```

sudo apt-get update

```

That was what my instructions meant :)
Note:: Have you done what pricechild instructed you to do?
Il

---

### Post by Scott A on 2007-01-13
Hello Illuvator 
I followed your instructions. 

Then I did

sudo apt-get -f install
cat /etc/apt/sources.list

and here is what it said:

saurand@saurand-desktop:~$ sudo apt-get -f install
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
saurand@saurand-desktop:~$ 
saurand@saurand-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
saurand@saurand-desktop:~$ cat /etc/apt/sources.list

---

### Post by PriceChild on 2007-01-13
> **Scott A said:**
> Hello Illuvator 
I followed your instructions. 

Then I did

sudo apt-get -f install
cat /etc/apt/sources.list

and here is what it said:

saurand@saurand-desktop:~$ sudo apt-get -f install
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
saurand@saurand-desktop:~$ 
saurand@saurand-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
saurand@saurand-desktop:~$ cat /etc/apt/sources.listPlease do what we've asked you and run ```
sudo dpkg --configure -a
```

oh and looks like you no-longer have a sources list.

---

### Post by Scott A on 2007-01-13
Hello all!
Looks like update manager works again!

I didn't realize there was more than one page to this forum post, so i couldn't figure out why I sometimes saw new things and then I couldn't see them again. 

Oops.

I finally got priceChilds advice about sudo dpkg --configure -a and I guess it worked!

Thanks again, and sorry I did not notice the obvious, that there are now three pages to this post. 

Thanks,
Scott A

---

### Post by shnuegums on 2008-04-18
Hi NEWB here and already ran into my first lucky problem :D
So downloaded my updates that took 2 hours then half way through the install the system shutdown :( now when I try and do the update I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I try and access the synaptic manager to update repositories I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now at the terminal I get: (what do I do?) :"(

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

nicks@desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



And thanks for any help :)

---

### Post by zvacet on 2008-04-18
```
gksudo gedit /etc/apt/sources.list
```

replace 

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

with 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

Save file and close.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo dpkg --configure -a
```

---

