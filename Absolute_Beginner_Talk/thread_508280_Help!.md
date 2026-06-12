---
title: "Help!"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-07-24
i got this problem look at the attachment

---

### Post by TigerWolf on 2007-07-24
Have you tried following the instructions it gives and opening a new termial window and typing
 sudo apt-get update
 and 
sudo apt-get install -f

Make sure you close the other installation applications. Only one can be opened at the same time.

---

### Post by llzero1337 on 2007-07-24
hmm i tried but i get this

---

### Post by Ihatecompvir on 2007-07-24
What program did you use to make the Live CD? Please tell me.

---

### Post by llzero1337 on 2007-07-24
i orderd one of the website

---

### Post by Ihatecompvir on 2007-07-24
[SIZE=2]Nevermind, I can't help. I can't even get Linux to boot![/SIZE]

---

### Post by llzero1337 on 2007-07-24
anyone?

---

### Post by faizy999 on 2007-07-24
Hello guys can u tell me how can i login into root through a user account in ubuntu in terminal.
required for installation.

---

### Post by llzero1337 on 2007-07-24
i tried the sudi but i get the same result=nothing

---

### Post by cereal killa on 2007-07-24
bro pls dont think im being rude (cause i dont mean it to be rude), but save urself serious time and a lot of posts and help these guys help u. it says:

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

and ur screenshot dont say u ran that. it specifically tells u to run THAT command. did u do it? what did it say when u did?

im a new user who knows s* about fixing this but i know that u need to give a lot more info than 'help me. look at this pic'. explain what u have done and what it told u.

---

### Post by RomeReactor on 2007-07-24
Hi. Try running:
```
sudo apt-get install -f
```
before
```
sudo apt-get update
```

---

### Post by llzero1337 on 2007-07-24
cerial killa i tred i get this everytime
 dpkg: requested operation requires superuser privilege

and rome reactor 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

im appriciating all the help guys

---

### Post by bigken on 2007-07-24
have you gone into synaptic to see if there are any broken packages if there is remove them

oh and its (sudo dpkg --configure -a)

---

### Post by llzero1337 on 2007-07-24
how can i get to synaptic? soory for being a retard at this i only just got it!

---

### Post by llzero1337 on 2007-07-24
ok i got into it i found the poblem it was the sun java how can i remove it? i marked it for removal btw

---

### Post by RomeReactor on 2007-07-24
Did you run:
```
sudo dpkg --configure -a
```
?
Also, what java package is causing problems?

---

### Post by llzero1337 on 2007-07-24
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on sun-java6-plugin; however:
  Package sun-java6-plugin is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin
 ubuntu-restricted-extras

---

### Post by RomeReactor on 2007-07-24
If you haven't done this, I suggest you do it now:
```
sudo dpkg --configure -a
```
then
```
sudo apt-get install -f
```
also, please post the output of this command (you may have a problem with your repositories):
```
cat /etc/apt/sources.list
```

---

### Post by llzero1337 on 2007-07-24
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474;     its subject matter.  It supersedes all prior or contemporaneous       &#8593;  
 &#9474;     oral or written communications, proposals, representations and        &#9618;  
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618;  
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618;  
 &#9474;     between the parties relating to its subject matter during the term    &#9618;  
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618;  
 &#9474;     binding, unless in writing and signed by an authorized                &#9618;  
 &#9474;     representative of each party.                                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618;  
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618;  
 &#9474;                                                                           &#9646;  
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                       

now what do i do

---

### Post by llzero1337 on 2007-07-24
also, please post the output of this command (you may have a problem with your repositories):
```
cat /etc/apt/sources.list
```[/QUOTE]

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by RomeReactor on 2007-07-24
> **llzero1337 said:**
> &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474;     its subject matter.  It supersedes all prior or contemporaneous       &#8593;  
 &#9474;     oral or written communications, proposals, representations and        &#9618;  
 &#9474;     warranties and prevails over any conflicting or additional terms      &#9618;  
 &#9474;     of any quote, order, acknowledgment, or other communication           &#9618;  
 &#9474;     between the parties relating to its subject matter during the term    &#9618;  
 &#9474;     of this Agreement.  No modification of this Agreement will be         &#9618;  
 &#9474;     binding, unless in writing and signed by an authorized                &#9618;  
 &#9474;     representative of each party.                                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For inquiries please contact: Sun Microsystems, Inc., 4150 Network        &#9618;  
 &#9474; Circle, Santa Clara, California 95054, U.S.A.                             &#9618;  
 &#9474;                                                                           &#9646;  
 &#9474; DLJ v1.1                                                  27APR2006ANS    &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                       

now what do i do

You have to press ENTER or the SPACEBAR, can't remember exactly. The point is to highlight **<OK>** and press enter to accept Sun's license.

You're really close to solving your problem!

---

### Post by llzero1337 on 2007-07-24
I'm presssing enter and spacebar but nothing is happening 
and i appriciate all the help

---

### Post by RomeReactor on 2007-07-24
Maybe by pressing TAB? I'm really sorry, at the moment I can't remember how to highlight the <OK> button in the terminal. As a last resort, try clicking it (some terminal programs offer mouse interactivity). Or type OK, though this probably won't work.

---

### Post by bigken on 2007-07-24
use the arrow keys till it goes red then hit enter

---

### Post by llzero1337 on 2007-07-24
its ok if you can remmber

---

### Post by llzero1337 on 2007-07-24
it was the arrow keys thanks bigken!

---

### Post by llzero1337 on 2007-07-24
YES IT IS FIXED THANKS EVERYONE I OWE YOU ALL AND EPICALLY YOU ROMEREACTOR THANKS ALOT do you have any im things like msn or aim?

---

### Post by RomeReactor on 2007-07-24
Glad you got it working again!
Actually, **bigken**'s suggestions were the ones that helped you the most. I don't use MSN or AIM, but I'm sometimes at the **#ubuntuforums** channel in IRC (**irc.freenode.net**).

---

### Post by llzero1337 on 2007-07-24
I forgot to add THANKS BIGKEN I OWE YOU MAN
have you got AIM or MSN?

---

### Post by bigken on 2007-07-24
Im a huge fan of lager and cider :lolflag:

---

### Post by llzero1337 on 2007-07-24
lol are you livng in the UK?

---

### Post by bigken on 2007-07-24
yep slough

---

### Post by usr001-25-8387 on 2007-07-24
See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

i got this too.

my commands dont seem to work in the terminal.  cant configure the dpkg thing.:guitar:

can you tell me please, who won.  say can i have some of your purple berries.

just wondering why im trying to learn ubuntu.  et tu.
8387:lolflag:

---

### Post by RomeReactor on 2007-07-24
Hi **usr001-25-8387**. Your sources.list looks OK. What is the error message you're getting?

---

### Post by usr001-25-8387 on 2007-07-24
says,  dpkg--configure-a is not valid command or unknown command.

will not take with sudo or being root.

the update manager doesnt work,  gives dpkg error.

running xp and feisty dual boot on t1100 emachine.  xp chrashed and lost the hd; so thought id try ubuntu.  

cant seem to get the command line commands to work.

found this thread searching the dpkg--configure-a thanks for the response.
:guitar:8387

---

### Post by RomeReactor on 2007-07-25
If you are entering this in the terminal
```
dpkg--configure-a
```
you'll get an error for two reasons:

1.- There must be spaces between the options; **dpkg** is the command, and **--configure** and **-a** are its options. So it should read:
```
dpkg --configure -a
```

2.- You **must** issue this command as root. To do so you prepend **sudo** to the command. Otherwise it will tell you you don't have rights to run it (among other errors, I think).

So the actual command line to enter is like this:
```
sudo dpkg --configure -a
```

---

### Post by bigken on 2007-07-25
the best way to execute commands that are here is to copy and paste them into the terminal that way you wont get any typo errors :)

---

