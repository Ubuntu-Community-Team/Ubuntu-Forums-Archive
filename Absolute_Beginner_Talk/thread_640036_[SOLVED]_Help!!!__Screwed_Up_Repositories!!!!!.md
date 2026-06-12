---
title: "[SOLVED] Help!!!  Screwed Up Repositories!!!!!"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-12-13
I screwed up my repositories...  When I try to add/remove via ANY/ALL means (gedit, synaptic) I get this message,

[COLOR="Red"]E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/COLOR]

I now have NO repositories available to me....

What did I do, and how do I fix my system???  I was attempting to make changes needed to download IE4 for Linux (was at the website, following the instructions carefully...  Obviously not carefully enough...  Heh)

I am running Dapper on a 2 gig, 160 gig HD Notebook (Pavilion).

Thanks, I hope.  Don't really want to start from scratch, again....  On my 160 gig HD, I got only 40 left free...  Gonna be a bitch if I have to reload and start from scratch.

john

---

### Post by chippy99 on 2007-12-13
Have a look at [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

It generates repository lists that you can copy into your /etc/apt/sources.list

John

---

### Post by john wagner on 2007-12-13
Tried to do that.  It (Terminal) won't let me in.  I get a bash error message denying me permission.  Sudo aint doing it either.  It also claims I got an unknown on line 45, ".png"...  But, it will not let me in to see it/change it.  Sigh.  I SO don't want to do a reinstall....
Took me 3 days to figure out how to get my wireless router to talk to my laptop.  And ALL the 120+gig software I got installed.  Everything was working so well...

john

---

### Post by maharbA on 2007-12-13
Open your sources.list file:
```
gedit /etc/apt/sources.list
```
and check out line 36. The error you're getting says that there's a problem with that line. Copy and post that line plus a few before and after it if you need help.

Also, it says to use the repository dialog to correct the problem. Try (in Synaptic) opening the repositories dialog (in the settings menu), maybe you can spot something there.

---

### Post by nikoPSK on 2007-12-13
yes as john mentioned you can just recopy paste you sources.list to make it all better. :KS

---

### Post by Dr Small on 2007-12-13
Try:
```
gksudo gedit /etc/apt/sources.lst
```

And post the output here. I would like to see line 36.

Dr Small

---

### Post by john wagner on 2007-12-13
LOL!  It's either laugh or cry....  It finally let me have permission to see my source.lists....  Here ya go:





See em there?  Above this line, but below the first line?  Nope?  Neither do I....  Nuttin on sources now, AT ALL!!!  It's completely blank.
Oh, itwont allow me to open in synaptec (I get the original message, in red up on first post).

john

---

### Post by john wagner on 2007-12-13
This is the only thing I get from synaptec,

[COLOR="Red"]E: Type 'eyes.png' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/COLOR]


Heh, LOL!

john

---

### Post by wormser on 2007-12-13
> **chippy99 said:**
> Have a look at [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

It generates repository lists that you can copy into your /etc/apt/sources.list

John

Do what chippy99 said.

---

### Post by voteforpedro36 on 2007-12-13
I think it's sources.list.

You just pasted a completely empty file, that doesn't exist.

---

### Post by john wagner on 2007-12-13
Really????  I tried.  Sorry for the wise ***, snarky, rude reply.
I did.  Step by step.  Line by line, even did all the links, rdg up on it all before I started.
This is current status...
[COLOR="Red"]E: Type 'eyes.png' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/COLOR]

john

---

### Post by john wagner on 2007-12-13
I did sources.list
Still an empty screen, no sources.  Got all the tabs up on the toolbar, just nuttin listed.
In terminal, it says this (when I try for a list)

[COLOR="Red"]basset@basset-laptop:~$ gksudo gedit /etc/apt/sources.lst
(gedit:11340): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/COLOR]

Thanks, again...  LOL!

john

---

### Post by voteforpedro36 on 2007-12-13
> **john wagner said:**
> Really????  I tried.  Sorry for the wise ***, snarky, rude reply.
I did.  Step by step.  Line by line, even did all the links, rdg up on it all before I started.
This is current status...
[COLOR="Red"]E: Type 'eyes.png' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/COLOR]

john

Err... what does ```
gksu gedit /etc/apt/sources/list
```

say now?

---

### Post by john wagner on 2007-12-13
> **voteforpedro36 said:**
> Err... what does ```
gksu gedit /etc/apt/sources/list
```

say now?

Exactly the same thing as above.  Blank screen, with warning in terminal.

john

---

### Post by fenian on 2007-12-13
Do this open a terminal and enter...

> sudo gedit /etc/apt/sources.list

copy and paste the follwing into the window that opens...

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
## only uncomment it if you need it
## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

save the file and exit.In the terminal enter the following...

> sudo apt-get update.

---

### Post by john wagner on 2007-12-13
Ignorant question here....  What will happen when I turn this thing off?  Do I need the repositories to keep my current configuration working/running?  Or will I get a very confused laptop.....
And, is it possible to do a repair with the install cd?  I also got kubuntu installed, can I operate from there?  Or are they shared repositories?


john

---

### Post by fenian on 2007-12-13
If you added any third party repos yourself you will need to  add them again.

---

### Post by chippy99 on 2007-12-13
Do the following from within a console terminal

```

gksudo gedit /etc/apt/sources.lst

```

select and copy this into the editor window

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted 
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse


```

save the file. Then from a console type "sudo aptitude update"

---

### Post by chippy99 on 2007-12-13
Looks like fenian had the same idea as me :)

---

### Post by john wagner on 2007-12-13
Okay, Chippy and fenian......  If I do this, open an "empty" sources.list, cut and paste save etc....  Anything that IS there, but not showing (for whatever reason), will not clash/conflict with the cut/pasted stuff?
Or does the paste job supersede the older stuff (assuming it's still there, just in stealth mode)?

john

---

### Post by chippy99 on 2007-12-13
If when you edit the file nothing is displayed then the file is empty. If you are really paranoid you could backup your old sources.list by typing

```

cp /etc/apt/sources.list /etc/apt/sources.saved

```

prior to editing the file

---

### Post by overdrank on 2007-12-13
> **john wagner said:**
> Okay, Chippy and fenian......  If I do this, open an "empty" sources.list, cut and paste save etc....  Anything that IS there, but not showing (for whatever reason), will not clash/conflict with the cut/pasted stuff?
Or does the paste job supersede the older stuff (assuming it's still there, just in stealth mode)?

john

HI and this is dapper system and you said earlier you have kubuntu installed also. What is the window manger of the dapper system, gnome, kde? and try this command and see if the list is occupied. ```
cat /etc/apt/sources.list

```

---

### Post by maharbA on 2007-12-13
just in case it's unfamiliarity with the terminal that's causing confusion ... try this:
1. open the PLACES menu, then select HOME.
2. hit the UP button (next to back and forward) twice, or until it's greyed out.
3. double-click the folder named "etc"
4. double-click the folder named "apt"
5. Do you see a text file named "sources.list" (not sources.lst or sources.list.backup or anything else)? If so, double-click it. (you won't have permission to change the file, but you can read it, and that's all we care about right now.

If you found sources.list and opened it, is it still empty?

NOTE: the above steps will do the same thing as opening a terminal and typing
```
gedit /etc/apt/sources.list
```
Gedit is Gnome's default text editor. You will not have superuser privileges but you can read the file. if you want to change anything, add sudo before the above command so it becomes
```
sudo gedit /etc/apt/sources.list
```
just copy and paste the code you want into a terminal (remember, in Gnome's terminal application, you have to hit shift+ctrl+v to paste rather than just ctrl+v)

---

### Post by fenian on 2007-12-13
Your just replacing the old file with thie new one.They are probably pretty much the same except the one I posted isn't broken.also I would use the one i posted rather than the on chippy posted because it has the restricted repos in it (for things like flash,opera,etc..)

---

### Post by PmDematagoda on 2007-12-13
Would you please post the reply of:-

```
cat /etc/apt/sources.list
```

The list cannot be empty since the error message points at a specific line being malformed.

---

### Post by john wagner on 2007-12-13
> **PmDematagoda said:**
> Would you please post the reply of:-

```
cat /etc/apt/sources.list
```

The list cannot be empty since the error message points at a specific line being malformed.

Okay, that one got the following..

[COLOR="Red"]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricteddeb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://flomertens.free.fr/ubuntu/](http://flomertens.free.fr/ubuntu/) dapper main main-all

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe multiversedeb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe multiversedeb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiversedeb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

[/COLOR]


Still nothing listed the gedit way tho...??????

john

---

### Post by fenian on 2007-12-13
You can just navigate to the file in nautilus,open your home folder and click the up arrow icon twice,open the etc folder then open the apt folder and the sources.list file should be there you can open it and copy the text but you won't be able to make any changes.

---

### Post by john wagner on 2007-12-13
> **fenian said:**
> You can just navigate to the file in nautilus,open your home folder and click the up arrow icon twice,open the etc folder then open the apt folder and the sources.list file should be there you can open it and copy the text but you won't be able to make any changes.

All righty....  Here's a new one!  I cut and pasted your list into sources.  I got this when I tried to save it..

[COLOR="Red"]Could not save the file /etc/apt/sources.list
unexpected error:  File not found[/COLOR]

And in terminal, I get this:
[COLOR="Red"]
** (gedit:11965): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.[/COLOR]


LOL!

john

---

### Post by john wagner on 2007-12-14
anyone?

---

### Post by PmDematagoda on 2007-12-14
Ok, do this:-

1) Get a new sources.list file using [source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/").

2) Open Nautilus in root mode using:-

```
gksudo nautilus
```

3) Navigate to the /etc/apt directory.

4) Replace the current sources.list file(If available) with the one you got from source-o-matic.

5) Do:-

```
sudo apt-get update
```

---

### Post by john wagner on 2007-12-14
> **PmDematagoda said:**
> Ok, do this:-

1) Get a new sources.list file using [source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/").

2) Open Nautilus in root mode using:-

```
gksudo nautilus
```

3) Navigate to the /etc/apt directory.

4) Replace the current sources.list file(If available) with the one you got from source-o-matic.

5) Do:-

```
sudo apt-get update
```

[COLOR="Red"]I get the same message as:

Could not save the file /etc/apt/sources.list[/COLOR]

I'm thinking that I'm going to have to do a reboot of the disk....

john
unexpected error: File not found

And in terminal, I get this:

[COLOR="Red"]** (gedit:11965): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
[/COLOR]

---

### Post by john wagner on 2007-12-14
> **john wagner said:**
> [COLOR="Red"]I get the same message as:

Could not save the file /etc/apt/sources.list[/COLOR]

I'm thinking that I'm going to have to do a reboot of the disk....

john
unexpected error: File not found

And in terminal, I get this:

[COLOR="Red"]** (gedit:11965): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
[/COLOR]

LOL, my laptop is acting crazy!!!  Cursor winging all over the place, see the above post for an example.  LOL
All my files are backed up on an external WD 500 gig HD, so...  Think I'm just going to do a reformat/reboot of the kernal/repositories etc...
This is the first major problem I've had, and it's not Dapper/Linux's fault...  I know I did something, messing with the sources.list without a better knowledge of what I was doing.  Heh, I figured that that's the best way to learn.  Dive right on in!  Ooops!
Thanks all, for all the QUICK help you guys (generic, guys) tried to give me.  I have no doubt that if any one of you were here in person, it would be fixed in 5 minutes flat....

john

---

### Post by maharbA on 2007-12-14
> **john wagner said:**
>  Heh, I figured that that's the best way to learn.  Dive right on in!  Ooops!

Don't let this discourage you, we all learn more from failure than success :)
Playing with your sources.list file is a very good place to start.** Just remember to backup that file before you change anything.**

---

