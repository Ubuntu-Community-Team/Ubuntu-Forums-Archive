---
title: "Need help installing SudokuBan"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Gadren on 2006-02-25
[http://sourceforge.net/projects/sudokuban](http://sourceforge.net/projects/sudokuban)

I downloaded the tar.gz, but there's no makefile or anything...coming from only using repositories, I've having trouble finding information on how to install programs this way.

---

### Post by concept10 on 2006-02-25
I went there and did'nt see any install notes or Read Me files, so I am assuming that the program might already be a binary.  Which means that you could just probably extract the tarball and run it from within the folder.

---

### Post by Sandlst on 2006-02-25
after downloading this myself it would seem that there is no need to do any further "installation" from extracting the file....open a terminal, navigate to the folder you extracted from the .tar.gz file, and then type in ```
./sudokuban.py
``` post back if you have any problems.....

---

### Post by dvarsam on 2006-02-25
I am interested for that too !

This is what I got:

root@house:/home/dimitris/Desktop/sudokuban# ./sudokuban.py
Traceback (most recent call last):
  File "./sudokuban.py", line 25, in ?
    import pygtk, gtk, pango
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?    from _gtk import *
RuntimeError: could not open display
root@house:/home/dimitris/Desktop/sudokuban#

---

### Post by Sandlst on 2006-02-25
hmmm not sure if this will work, but try searching synaptic for the package python-all and installing, post back if you have any problems
*EDIT* also try installing python-gtk (will have a version number in there somewhere) and libpango

---

### Post by dvarsam on 2006-03-08
[QUOTE=Sandlst]Try searching synaptic for the package python-all & install.
Post back if you have any problems.
Also try to install python-gtk (will have a version number in there somewhere) & libpango[/QUOTE]

Hello !!!

My problem still remains the same !!!


Using Ubuntu's "Synaptic Package Manager":

a. I have NOT found ANY "python-all" packages.

b. I have found the following "python-gtk" packages:

    1. python-gtk-1.2		- -> NOT Installed
    2. python-gtk2		- -> Installed
    3. python-gtk2-dev		- -> NOT Installed
    4. python-gtk2-doc		- -> NOT Installed
    5. python-gtk2-tutorial	- -> NOT Installed
    6. python-gtkextra		- -> NOT Installed
    7. python.gtkmvc		- -> NOT Installed


c. I have found the following "libpango" packages:

    1. libpango1.0-0		- -> Installed
    2. libpango1.0-common	- -> Installed
    3. libpango1.0-dbg		- -> NOT Installed
    4. libpango1.0-dev		- -> NOT Installed
    5. libpango1.0-doc		- -> NOT Installed
    6. libpango1-ruby		- -> NOT Installed


Just in case it is a Repo's problem, my "sources.list" file includes the Following:


# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy main restricted


## Major bug fix updates produced after the final release of the
## distribution.

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-updates main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy universe


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


## This was added (as  asked)
## Multiverse

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse


## Penguin Liberation Front

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free


## Open Office 2 final

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## To be able to download "azureus" program

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free 

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

## Alternative to the above "antesis"
## Do not use it, unless "antesis" is down.

# deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
# deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free


Any ideas?

Where can I find the program "python-all"?

what is missing?

Please Help !!!

P.S. > This is the first time I have attempted to install a ".tar.gz" & got sooo close. 
          All my previous attempts have ALL been unsuccessful with ".tar.gz" files...
          ...as if there is some (Pharao's) "curse" around those kind of files...

---

### Post by stalefries on 2006-03-09
Don't worry, you've got the correct files that they were talking about. DO you really want sudokuban, or would you consider abother program? I use gnome-sudoku, and it's fine. It can even print off multiple sudoku puzzles.

---

### Post by dvarsam on 2006-03-09
The program "gnome-sudoku", you suggested, is equally fine for me!!!

So, the only way to run it, is through the Terminal window?

Can't I add a "link" of the program's ".exe" file inside my "Applications" menu?

I performed a search for "gnome-sudoku" to locate where is the ".exe" file lying _inside_ my Ubuntu (& hopefully add it in the "Applications" menu), and found nothing!!!

Where are ALL the ".exe" files located in my Ubuntu? 

Thanks.

P.S.> The other problem (that bothers me) with my Ubuntu, is that I have NEVER EVER (@$%#%&#) been able to install a ".tar.gz" program in my Ubuntu PC...

---

### Post by cvcaelen on 2006-03-09
> So, the only way to run it, is through the Terminal window?

no, after jou did "sudo apt-get install gnome-sudoku"
you do "killall gnome-panel"
and an icon apears in games , called "sudoku"

that's all there is to it
Have fun

Christiaan

---

### Post by dvarsam on 2006-03-09
_Quote_:
" you do "killall gnome-panel" & an icon apears in games , called "sudoku"...."

Thanks for your response.

So, this is the "common" approach when somebody does NOT have a program "link" showing in his "Applications" menu?
And the command "killall gnome-panel" ALWAYS creates "links" in the "Applications" menu?

OR:

Is this a one-time case, i.e. this solution is provided ONLY for this program ("sudoku")?

Thanks

---

### Post by cvcaelen on 2006-03-09
[QUOTE=dvarsam]_Quote_:
" you do "killall gnome-panel" & an icon apears in games , called "sudoku"...."

Thanks for your response.

So, this is the "common" approach when somebody does NOT have a program "link" showing in his "Applications" menu?
And the command "killall gnome-panel" ALWAYS creates "links" in the "Applications" menu?

OR:

Is this a one-time case, i.e. this solution is provided ONLY for this program ("sudoku")?

Thanks[/QUOTE]

well, 

i don't know if it's the way to go,
but after an "apt-get install whatever"
I allways do a "killall gnome-panel"
and allways I find an icon added to one of the applications menu.
I am sure I picked it up somewhere, but I can't remember where.
but
it works

edit:it never harms doing an "apt-get update upgrade" after installing something: it should get you the newest of something

Christiaan

---

### Post by pbaehr on 2006-03-09
```
killall gnome-panel
``` basically just restarts the gnome panel and forces it to notice any new items.

Often when I install new software I find the entry is made without having to do that but it's useful if you've made a change and you've got the feeling that the panel isn't showing what it should be.

---

