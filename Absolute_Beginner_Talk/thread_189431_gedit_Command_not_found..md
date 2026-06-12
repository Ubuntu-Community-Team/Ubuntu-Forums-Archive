---
title: "gedit: Command not found."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by dux on 2006-06-05
I was trying to install KDE this morning using the Synaptic Package Manager, it didn't work and I eventually gave up. Now, however, when I try to use gedit I get the following message: 
```
bash: gedit: command not found
``` have I done something incredibly stupid and/or is there an easy way to fix it?

---

### Post by Klaidas on 2006-06-05
Hmm, strange. Try ```
sudo apt-get install gedit
```, that should work

---

### Post by taurus on 2006-06-05
How did you try to install KDE?  Did you do something like
```

sudo apt-get install kubuntu-desktop

```
And if gedit is not on your machine or you accidently remove it, install it again with
```

sudo apt-get install gedit

```

---

### Post by dux on 2006-06-05
```
stu@stu-desktop:~$ sudo apt-get install gedit Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gedit: Depends: libgnomeprint2.2-0 (>= 2.11.0) but it is not going to be insta lled
         Depends: libgnomeprintui2.2-0 (>= 2.12.0) but it is not going to be ins talled
         Depends: libgtksourceview1.0-0 (>= 1.1.1) but it is not going to be ins talled
         Depends: gedit-common (= 2.12.1-0ubuntu1) but 2.14.2-0ubuntu3 is to be installed
E: Broken packages
``` I'm thinking It'd just be easier to re-format :roll:. I get the feeling the package manager deleted important stuff?

---

### Post by richbarna on 2006-06-05
If you are using KDE, when you have to edit text with command line, just use kate/kwrite instead of gedit.
eg :-

kdesu kate /file/to/be/edit.ed or
kdesu kwrite /file/to/be/edit.ed

---

### Post by dux on 2006-06-05
I'm not using KDE, I was trying to install it with the Package manager but it said that it needed loads of other files to install, I tried to install some of them but most depended on even more files to be installed and eventually I just gave up. So as far as I know I've got some core KDE files but KDE is not installed.

Anyway, when I loaded up Ubuntu again my desktop wouldn't even show up. I could get to the console but have even the faintest clue what's wrong or what I could do to fix it. Is my best bet at this point to re-install the whole thing and just never touch the package manager ever again?

---

### Post by richbarna on 2006-06-05
Ok, lets look at this.
1. Have you got all the repositories enabled ?
2. Breezy or Dapper ?
3. Tried ?
> sudo apt-get install kde
from the terminal ?
4. post back with above info.

---

### Post by dux on 2006-06-05
1. I have no idea, how do I find out?
2. Drapper
3. Yes said something about dependencies which I didn't have.

---

### Post by richbarna on 2006-06-05
ok,
1. use synaptic-settings-repositories (and check all sources)
2. or > sudo vim /etc/apt/sources.list 
( I say use "vim" editor from the terminal because you haven't got "gedit")
If there is an error message, just hit enter, and then type e for edit.
3. You should get something like this :-
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Anywhere you see a comment (##) before a deb, etc ## deb-src ...........
delete the comments ## so that your file looks like mine.

Once you have done this, goto the end of the file with your cursor keys and type 
:wq 
this will write and quit.

---

### Post by slakkie on 2006-06-05
Hi,

try updating your sources:

1) apt-get update

and then 

2) apt-get install gedit

I don't know what you have in your sources list, but this is mine, and I think I have most of the sources which are helpfull (open file /etc/apt/sources.list with nano, vim or other text editors):
```

## Sat Jun  3 11:15:04 CEST 2006 (wesleys)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main universe multiverse restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# libdvdcss2 and w32codecs
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

```
If you have editted this file, make sure you update your sources (step 1) and then install gedit (step 2).

Good luck with it!

---

### Post by dux on 2006-06-05
my sources.list seems to refer to Breezy instead of Drapper. How and why I have no idea.

"apt-get update" gets me: 
Could not open lock file /var/lib/apt/lsts/back
open(13 permission denied)
 
and "apt-get install gedit" gets me:

E: Unable to lock the administration directory (/var/lib/dpkg/) are you root?

I think something has gone very, very wrong.

---

### Post by carlosqueso on 2006-06-05
you need sudo before any apt-get command.  try it then.

---

### Post by richbarna on 2006-06-05
[QUOTE=dux]my sources.list seems to refer to Breezy instead of Drapper. How and why I have no idea.

"apt-get update" gets me: 
Could not open lock file /var/lib/apt/lsts/back
open(13 permission denied)
 
and "apt-get install gedit" gets me:

E: Unable to lock the administration directory (/var/lib/dpkg/) are you root?

I think something has gone very, very wrong.[/QUOTE]

Then you are running Breezy Badger, not Dapper.
Do as I said before by using vim to uncomment your repositories. (remove the ##'s)
Then :-
> sudo apt-get update && upgrade
From there you can download gedit
> sudo apt-get install gedit
Then you can :-
> sudo aptitude install kubuntu-desktop

---

### Post by dux on 2006-06-05
Well, I removed all the ##'s and now it's worse.```
E: Type &#8216;Major&#8217; is not known on line 7 in source list /etc/apt/sources.list
``` On the plus side, when I just un#'d the lines that looked like code instead of comments (which had double #s) "sudo aptitude install kubuntu-desktop" actually installed some stuff, but I still can't use any desktop. Also, realising I didn't know how to save in vim was fun.

I'm sure I'd heard this distro was user-friendly :P.

---

### Post by richbarna on 2006-06-05
> **dux]Well, I removed all the ##'s and now it's worse.```
E: Type &#8216 said:**
> 

Look at my post #9. I told you how to save in vim.
":wq" which = Write and Quit

Ok try with nano, you must have at LEAST one text editor.

whoa ! you can't use ANY desktop ??
ok, when you boot up, you just get a black terminal/login screen where you enter user and password ?

Boot up - type username + password
Then type :-
[QUOTE]startx
See if you get to the desktop.

---

### Post by dux on 2006-06-05
Argh, sorry, I'd missed that post. I take back my bitchy comment ;). And I kind of have a desktop. I have a purple background and I found that I can run apps like firefox through the terminal.

---

### Post by richbarna on 2006-06-05
ok, if you press Alt + F2 do you get a run command/dialogue box ?
If yes, try typing nano, gedit, kate, and kwrite so that I can see if you have access to a text editor other than vim.

---

### Post by dux on 2006-06-05
No dialogue with alt+f2, but I had a keybind to the terminal which I set up before everything went weird. Only nano works out all those commands in the terminal. I've now corrected my repository file I think. Looking back, I had seen your post, just not the edit you made a bit later. Did you add the save information in with the edit or am I just blind? :p

---

### Post by richbarna on 2006-06-05
Now we will get the sources.list sorted out.
Where I have put gedit, just type the name of a text editor.
> sudo gedit /etc/apt/sources.list
Now delete the WHOLE lot and paste this :-
> #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


Save and Exit.

Now do the :-
> sudo apt-get update
There shouldn't be any errors ;)

---

### Post by dux on 2006-06-05
Woo, update works now. I did the whole ctrl+alt+backspace thing to restart x, still no functional desktop though. Thanks for being so forgiving so far!

---

### Post by richbarna on 2006-06-05
Another thing to remember :-
If you install/remove a desktop environment (KDE, GNOME) it's better to use these commands :-
> sudo aptitude install kubuntu-desktop
> sudo aptitude remove kubuntu-desktop

As opposed to apt-get install/remove or using synaptic or adept.
You have a better chance of a clean removal if needed.

---

### Post by richbarna on 2006-06-05
[QUOTE=dux]Woo, update works now. I did the whole ctrl+alt+backspace thing to restart x, still no functional desktop though. Thanks for being so forgiving so far![/QUOTE]

No problem at all :)
Everybody on this forum has had to begin somewhere.

EDIT: Now lets get your desktop working :)

---

### Post by dux on 2006-06-05
I'm all ears, running ```
sudo aptitude install kubuntu-desktop
``` seem to work fine. KDE doesn't show up in the session options at log-in though. Would it be easier to try to get Gnome working since that's what I was using before?

---

### Post by richbarna on 2006-06-05
[QUOTE=dux]I'm all ears, running ```
sudo aptitude install kubuntu-desktop
``` seem to work fine. KDE doesn't show up in the session options at log-in though. Would it be easier to try to get Gnome working since that's what I was using before?[/QUOTE]

Ok, lets go for a :-
> sudo aptitude update
Then a :-
> sudo aptitude install ubuntu-desktop

---

### Post by dux on 2006-06-05
I could kiss your little toes! Desktop is back up, I'd almost forgotten what the applications menu looked like. :p

---

### Post by richbarna on 2006-06-05
[QUOTE=dux]I could kiss your little toes! Desktop is back up, I'd almost forgotten what the applications menu looked like. :p[/QUOTE]

Start kissin !! (only kidding)
Excellent, well done for sorting it out =D>

---

### Post by dux on 2006-06-05
Hey, you did all the hard work, I am learning though!
I'll be back again when I fail to install KDE once more. ;)

---

### Post by richbarna on 2006-06-05
The learning and the success are the fun parts ;)

---

