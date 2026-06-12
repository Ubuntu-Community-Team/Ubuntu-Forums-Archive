---
title: "Total Newb q:  how the heck do I deb????"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-21
Hey all,

This really makes my ego go south...  I'm trying to install freenx on my freshly installed breezy.  **I have no idea how to deb**.  I've tried it from a terminal window and get the message "bash: deb: command not found".

What am I missing?

gs

---

### Post by CompShrink on 2006-03-21
sudo dpkg -i NAME.deb

Replace name with the filename of course, that will install a single *.deb file into your system. Use your primary user's name as the password.

---

### Post by bonzodog on 2006-03-21
are you trying perchance to install a file with the type of .deb?
If so, that is just a filetype nothing more. They are packages which the debian system uses (Ubuntu is based on Debian). 
To install it, simply do:

```
$sudo dpkg -i <name of file>
```

---

### Post by localzuk on 2006-03-21
use sudo dpkg -i blah.deb (blah.deb being the file)

.deb are installation packages so have to be installed :)

---

### Post by gnu2tux on 2006-03-21
Check this guide out for a very newb friendly guide:

[http://www.linuxnewbieguide.org/chap9.php]("http://www.linuxnewbieguide.org/chap9.php")

Cheers, Al.

---

### Post by WoodyMahan on 2006-03-21
[QUOTE=guysmiley]Hey all,

This really makes my ego go south...  I'm trying to install freenx on my freshly installed breezy.  **I have no idea how to deb**.  I've tried it from a terminal window and get the message "bash: deb: command not found".

What am I missing?

gs[/QUOTE]


add

deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx

to your sources.list, then refresh synaptic and you should see freenx in there, and you can install it.

Here's how you do that:

Open the erminal by going Applications - Accessories - Terminal

type this line directly into the terminal: sudo gedit /etc/apt/sources.list

This will open a text editor with a alot of stuff in it. Scroll to the bottom and copy/paste: deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx

Click Save and close.

Then open synaptic and hit the reload button. THen you can search for freenx and mark it for installation. Hope this helps.

---

### Post by WoodyMahan on 2006-03-21
[QUOTE=WoodyMahan]add

deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx

to your sources.list, then refresh synaptic and you should see freenx in there, and you can install it.

Here's how you do that:

Open the erminal by going Applications - Accessories - Terminal

type this line directly into the terminal: sudo gedit /etc/apt/sources.list

This will open a text editor with a alot of stuff in it. Scroll to the bottom and copy/paste: deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/) breezy-seveas freenx

Click Save and close.

Then open synaptic and hit the reload button. THen you can search for freenx and mark it for installation. Hope this helps.[/QUOTE]


I did this myself BTW and FreeNX rocks.

---

### Post by guysmiley on 2006-03-21
Thanks to all of you for your responses!

Woody - yours was especially helpful and once I realized the # in front of the deb command in sources.list was not "uncomment" (a little too much html/php creeping in there) things are rolling along smoothly.

gs  :o)

---

### Post by guysmiley on 2006-03-21
I spoke to soon!!

When I checked in synaptic, no freenx can be found!  I searched throught the All list and even did a specific search.  No packages are there called 'freenx'.

I must have typed incorrectly in sources.list, right?  This is exactly what I entered:
# deb [http://free.linux.hp.com/~brett/seveas/freenx/breezy-seveas](http://free.linux.hp.com/~brett/seveas/freenx/breezy-seveas) freenx

What am I doing wrong?

I noticed the other deb entries have a deb-src entry as well.  Do I need this?

gs

---

### Post by Brunellus on 2006-03-21
[QUOTE=guysmiley]I spoke to soon!!

When I checked in synaptic, no freenx can be found!  I searched throught the All list and even did a specific search.  No packages are there called 'freenx'.

I must have typed incorrectly in sources.list, right?  This is exactly what I entered:
# deb [http://free.linux.hp.com/~brett/seveas/freenx/breezy-seveas](http://free.linux.hp.com/~brett/seveas/freenx/breezy-seveas) freenx

What am I doing wrong?

I noticed the other deb entries have a deb-src entry as well.  Do I need this?

gs[/QUOTE]
uncomment the line by deleting the initial #.

Generally, in bash scripts and config files, any line beginning with a hash (#) is a comment, and not parsed.

---

### Post by guysmiley on 2006-03-21
k,

I deleted the "#" so my line now reads:
deb [http://free.linux](http://free.linux)....

When I launch synaptic I get error:
E: Malformed line 39 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem

Help!?!

---

### Post by Brunellus on 2006-03-21
[QUOTE=guysmiley]k,

I deleted the "#" so my line now reads:
deb [http://free.linux](http://free.linux)....

When I launch synaptic I get error:
E: Malformed line 39 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem

Help!?![/QUOTE]
too many slashes.

reproduce this line EXACTLY.

```

deb http://seveas.ubuntulinux.nl/ breezy-seveas all
```

NOTE THAT THERE ARE NO SLASHES IN THE LAST TWO ITEMS.

the repository line is in three parts:

1) a declaration of the type of repository:  deb (binary packages) or deb-src (source packages)

then SPACE.

2) that repository's URL

then SPACE.

3) the package groups on the repository you wish to fetch.

---

### Post by guysmiley on 2006-03-21
Thanks again for the help.

I click reload in synaptic and now, in the Downloading package Information Window, I get error (after a really, really long wait...):

The repository might no longer be available or could not be contacted because of network problems....  Check your network connection and the correct writing of the repository address in the preferences.

gs  :confused:

---

### Post by Brunellus on 2006-03-21
...exactly what it says on the tin.  probably his server is down.  try the mirror:

```
deb http://free.linux.hp.com/~brett/seveas/freenx breezy-seveas freenx
```

---

### Post by guysmiley on 2006-03-21
I can't believe this!

Now, on launch, synaptic gives error:
"Couldn't stat source package list [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas/freenx Packages...No such file or directory

argh!

---

### Post by Brunellus on 2006-03-21
did you copy the line EXACTLY?

---

### Post by guysmiley on 2006-03-21
Yes, I did.  Copied straight from the browser and pasted in.

---

### Post by WoodyMahan on 2006-03-21
[QUOTE=guysmiley]I can't believe this!

Now, on launch, synaptic gives error:
"Couldn't stat source package list [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas/freenx Packages...No such file or directory

argh![/QUOTE]

The error listed above shows a / between the words "seveas" and "freenx".

Open the souces.list and recheck.  Just to be sure.

Chin up Guy!  We'll get this.

---

### Post by guysmiley on 2006-03-21
This is the error in full that I get when I paste in:

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) breezy-seveas freenx

Window:
W: Couldn't stat source package list [http://free.linux.hp.com](http://free.linux.hp.com) breezy-seveas/freenx Packages (/var/lib/apt/lists/free.linux.hp.com_%7ebrett_seveas_freenx_dists_breezy-seveas_freenx_binary-i386_Packages) - stat (2 No such file or directory)

thanks for the continued support, guys!

---

### Post by guysmiley on 2006-03-21
Still working on this...

Can anyone help me, please?  Here's my sources.list file and I seem to get the 'couldn't stat source package... no such file or directory" no matter what mirror I put in.  Any help is SUPER appreciated,

gs

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) breezy-seveas freenx

---

### Post by Brunellus on 2006-03-21
holy god in heaven.  you've COMMENTED OUT ALL YOUR REPOSITORIES!

---

### Post by guysmiley on 2006-03-21
Actually, this is the way the sources.list came.

Any suggestions as to which ones I uncomment?

---

### Post by christhemonkey on 2006-03-21
All the ones that start with deb or deb-src, so the ones with only a single #.

---

### Post by guysmiley on 2006-03-21
Thanks, again, guys.  I feel terribly for all the effort you're pouring into this problem of mine...

So, I uncomment several lines and I now get errors saying I can't connect to the repositories I uncommented.  The error message suggests that "the repositories may no longer be available... check my network connections and the correct writing of the repositories in preferences."

I have no clue what to do here.  I can visit any of the addresses via FF so I know I can see them...  What follows is my new sources.list

[COLOR="Blue"]deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe[/COLOR]

Thanks, once more, for all the assistance.

gs

---

### Post by christhemonkey on 2006-03-21
Any reason you didnt uncomment universe?
This list looks fine now, as far as i know? did you make sure to reload package list?

---

### Post by guysmiley on 2006-03-21
I updated the list (missing universe was an accident).

If by "reloading the package list" you mean launch synaptic and click reload, yes.  The Window reports that it connects to the cdrom://ubuntu 5... release but every other connection fails:
ca.archive.ubuntu.com...
security.ubuntu.com...

It goes on to say that the requests timed out...  I don't get it.  Why can I visit the sites through FF but not through synaptic?

---

### Post by christhemonkey on 2006-03-21
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
That site will generate a nice working sources.list file for you.
Though i dont see whats wrong with that one!

---

### Post by guysmiley on 2006-03-21
I've tried those and none of them work.

Any other ideas?  Like I said, I can visit them in FF, why not through Synaptic?

---

### Post by CompShrink on 2006-03-22
really shouldn't make a difference, but have you tried doing the following on a command line (terminal):
```

sudo apt-get update
sudo apt-get install freenx
```

this is after you propperly uncomment EVERY LINE in the above that only has one # at the begining, as in:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

```

Copy and paste the above into sources.list, and then try the two apt-get command line commands. If it doesn't work tell us what errors come up.

---

### Post by guysmiley on 2006-03-22
I'll try this later on today.  I won't be able to give it a shot for quite a while, but thanks for the idea - I will definetly get to it asap.

gs

---

