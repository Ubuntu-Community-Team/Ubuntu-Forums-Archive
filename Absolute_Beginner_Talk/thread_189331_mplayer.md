---
title: "mplayer"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-06-05
Hi all!:) 

Well, Dapper is fantastic, but I just can't get mplayer to work.  It is installed, but there is no sign of it in APPLICATIONS > SOUND & VIDEO.  So where is it and how do I get it started?  I typed mplayer into a run command but nothing happened.  When I put mplayer in the terminal, this is what I got:

dapper@dapper-desktop:~$ mplayer
mplayer: error while loading shared libraries: libtermcap.so.2: cannot open shared object file: No such file or directory
dapper@dapper-desktop:~$


I am obviously missing something here.  :-k   Perhaps I have to put some other command in the terminal?

Russty.

---

### Post by Sutekh on 2006-06-05
**mplayer** is the command line player.  **gmplayer** is the GUI front to mplayer.

Still the error you have shouldn't appear from using **mplayer**.  

How did you install mplayer?  Using the Dapper multiverse repository (apt-get)??

---

### Post by Russty of Oz on 2006-06-05
[QUOTE=Sutekh]**mplayer** is the command line player.  **gmplayer** is the GUI front to mplayer.

Still the error you have shouldn't appear from using **mplayer**.  

How did you install mplayer?  Using the Dapper multiverse repository (apt-get)??[/QUOTE]

I used synaptic.  

Russty

---

### Post by Sutekh on 2006-06-05
Ok yes. Synaptic is just a GUI for apt-get.  Do you recall if the respository you got it from the Dapper one and not another one?  

(ie deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse) 

Maybe try reinstalling mplayer
```
sudo apt-get --purge remove mplayer
sudo apt-get install mplayer
```
Does the installation complete without error?

or in Synaptic if I can recall correctly; 'completely remove'(?) then 'apply' then 'mark for install' then 'apply'

---

### Post by Klaidas on 2006-06-05
Hmm, I was trying to install mplayer too, however:
```
klaidas@klaidas-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
klaidas@klaidas-desktop:~$
```

How could I fix that?

---

### Post by Russty of Oz on 2006-06-05
[QUOTE=Sutekh]Ok yes. Synaptic is just a GUI for apt-get.  Do you recall if the respository you got it from the Dapper one and not another one?  

(ie deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse) 

Maybe try reinstalling mplayer
```
sudo apt-get --purge remove mplayer
sudo apt-get install mplayer
```
Does the installation complete without error?

or in Synaptic if I can recall correctly; 'completely remove'(?) then 'apply' then 'mark for install' then 'apply'[/QUOTE]

No, there was an error.  This is what happened.

dapper@dapper-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is a virtual package provided by:
  mplayer-nogui 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-k6 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-custom 1:1.0-pre5-0.6ubuntu1
  mplayer-586 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-386 1:1.0-pre7cvs20050716-0.1ubuntu9
You should explicitly select one to install.
E: Package mplayer has no installation candidate

---

### Post by Sutekh on 2006-06-05
[quote=Klaidas]Hmm, I was trying to install mplayer too, however:
```
klaidas@klaidas-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
klaidas@klaidas-desktop:~$
``` 
How could I fix that?[/quote] 
Ok can you post your sources.list?
```
cat /etc/apt/sources.list
``` 

[quote=Russty of Oz]No, there was an error.  This is what happened.

dapper@dapper-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is a virtual package provided by:
  mplayer-nogui 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-k6 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-custom 1:1.0-pre5-0.6ubuntu1
  mplayer-586 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-386 1:1.0-pre7cvs20050716-0.1ubuntu9
You should explicitly select one to install.
E: Package mplayer has no installation candidate[/quote] 

Oh that never happened to me, I thought the mplayer package was the real one, and the mplayer-386, etc were dummy packages that installed mplayer.  It must have changed.

Well, I guess try the mplayer-386 package.


Edit: Im still sure that mplayer-386, et al are dummy packages...

What do you think?

[Ubuntu Packages - mplayer](http://packages.ubuntu.com/dapper/graphics/mplayer)

[Ubuntu Packages - mplayer-386](http://packages.ubuntu.com/dapper/graphics/mplayer-386)

---

### Post by Klaidas on 2006-06-05
Well, my sources.list is default + universe and multiverse enabled.
```
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

``` 
SHould I add some mplayer resposity?

---

### Post by Sutekh on 2006-06-05
[quote=Klaidas]Well, my sources.list is default + universe and multiverse enabled.
```
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

``` 
SHould I add some mplayer resposity?[/quote] Actually you don't have the multiverse enabled.  You have it enabled in the Dapper backports enabled though (which may not be open just yet)

You need to add **multiverse** to these lines
```
 deb http://au.archive.ubuntu.com/ubuntu/ dapper universe** multiverse**
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe **multiverse**

...

# deb http://security.ubuntu.com/ubuntu dapper-security universe **multiverse**
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe **multiverse**
``` Then update
```
sudo apt-get update
```

Also you are using the Australian local repositories (**au.**archive.ubuntu and so on).  I don't know if there is any local Lithuanian ones, but if you ever get slow apt-get downlaod speeds, I'd start here first and remove the **au.** part and use the main Ubuntu repositories.

---

### Post by Klaidas on 2006-06-05
Oh, thank you :) I didn't notice multiverse wasn't enabled
It seems to work now ;)

---

### Post by Sutekh on 2006-06-05
Great... are you able to run mplayer, using
```
gmplayer
```
Do you have the same problem as **Russty of Oz?**

---

### Post by Klaidas on 2006-06-05
No, everything is working fine :)

---

### Post by Sutekh on 2006-06-05
Ok cool, well hopefully a reinstall solves this problem for **Russty of Oz **too.

---

### Post by Russty of Oz on 2006-06-06
Well I still can't get mine to work!  I just did the thing you got Klaidas to do and this is what the reply was;

dapper@dapper-desktop:~$ cat /etc/apt/sources.list
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## created by arnieamuleremoved
dapper@dapper-desktop:~$

Now, this is like double dutch to me, so what can you see is wrong there?  I thought I already had multivers enabled.

Russty.

---

### Post by Russty of Oz on 2006-06-06
I just noticed, all those things above say Breezy.  But I installed Dapper!  Hmmm

---

### Post by Sutekh on 2006-06-06
[quote=Russty of Oz]I just noticed, all those things above say Breezy.  But I installed Dapper!  Hmmm [/quote] How on earth do you have Breezy repos?  Did you dist-upgrade?  Have you used Automatix or some other script since upgrading to Dapper?

You need to edit your sources.list and change all instances of **breezy** with **dapper**.
```
sudo gedit /etc/apt/sources.list
``` You may also want a complete new set of repositories, this would be the place to go...

[http://psychocats.net/ubuntu/sources.php]("http://psychocats.net/ubuntu/sources.php")

[quote=Russty of Oz]
**deb-src** [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy multiverse
[/quote] 
Ok apart from using Breezy repositories, which is a *big* problem, you only have the *source* repository enabled, see the **deb-src.**  If you want packages you need this line aswell, exchanging dapper for breezy too.
```
**deb** [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper multiverse
```
But I think its proabaly best to follow the link I provided, for a complete set of repositories.

---

### Post by Russty of Oz on 2006-06-07
Well! That did the trick!  Thanks Sutekh!

It seems it was Automatix that set all the repos to breezy.  So I did the changes as you suggested and after a few hours of downloading a total of 183 files, it all works fine.  Now Gnomebaker even works!!  Mplayer "sort of" works.  So I guess I will have to not use automatix until I get a version that works with dapper.

Thanks again for the help.  

Russty

---

### Post by Fornie on 2006-06-07
question...

everytime i play .avi files the sound and video does not sync...how can i fix this? thanks

---

### Post by uzi09 on 2006-06-07
you'll probably have to enable the framedrop (i think that's what it's called) switch.

ex: mplayer -framedrop 20 movie.avi

you can try a higher number than 20 to try to get it to work even "better", but you may end up having your movie skip a bit. so you kind of need to play around and find the right setting for the movie.

see man pages for more details:
man mplayer

imho, i've had better luck with xine/gxine -- especially in dapper!
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28xine-ui.29)
(you might also want to check out sections 6.13, and 6.15 to get this stuff working with windows and embeded vids)

---

### Post by Fornie on 2006-06-07
hello :)

where will i edit this? thanks

---

### Post by Sutekh on 2006-06-07
[quote=Russty of Oz]Well! That did the trick!  Thanks Sutekh!

It seems it was Automatix that set all the repos to breezy. So I did the changes as you suggested and after a few hours of downloading a total of 183 files, it all works fine. Now Gnomebaker even works!! Mplayer "sort of" works. So I guess I will have to not use automatix until I get a version that works with dapper.

Thanks again for the help.  

Russty[/quote] Glad to help!  Mplayer only "sort" of works?  What's its issue?  

There is an Automatix for Dapper now.


[quote=Fornie]hello :)
 
 where will i edit this? thanks[/quote] You need to use that command from a Terminal (Applications -> Accesories menu)
```
mplayer -framedrop 20 movie.avi
``` 
The GUI probably allows this, so you could have a look around for it too.

---

### Post by Russty of Oz on 2006-06-08
[QUOTE=Sutekh]Glad to help!  Mplayer only "sort" of works?  What's its issue?  
[/QUOTE]

Well, I can only get it to work by typing   *gmplayer*  into the terminal.  Then it opens along with a terminal like window listing all the things taking place in the program and if I close that window, the whole thing closes.  Now this may be normal, but I am use to these things just opening by themselves.  Is there anyway of putting mplayer in my Applications > Sound list or an icon on the desktop?

Apart from that, everything now works perfectly!  I can't thank you enough for helping me out here. This forum is great!!  I will soon be weaned off windows! 

Russty

---

### Post by Sutekh on 2006-06-08
[quote=Russty of Oz]Well, I can only get it to work by typing   *gmplayer*  into the terminal.  Then it opens along with a terminal like window listing all the things taking place in the program and if I close that window, the whole thing closes.  Now this may be normal, but I am use to these things just opening by themselves.  Is there anyway of putting mplayer in my Applications > Sound list or an icon on the desktop?

Apart from that, everything now works perfectly!  I can't thank you enough for helping me out here. This forum is great!!  I will soon be weaned off windows! 

Russty[/quote] Yeah as far as I know that is normal behaviour.  When the Terminal is used to start a process or application, it is 'linked' to the Terminal if you like.  Closing the Terminal kills the process.  Maybe this can be changed, but I'm not sure how.
_____________

You can also start a process using the **run dialog**.  Press Alt+F2 and it will popup.  Then just enter the command you want to run, in this case *gmplayer*.
_____________

Still, I am surprised that MPlayer isn't in your menus though.  You can create your own menu entry for it.  You should already have it, but if not install [Alacarte]("http://www.realistanew.com/projects/alacarte/")```
sudo apt-get install alacarte
```It should appear in the Applications -> System Tools menu (should be there already too, but if not you know what to install).

You can use it to create a new menu entry for MPlayer.  You can put it in your choice of menu, just remember to use the *gmplayer* as the **command** and you should be set.



Glad to help out a fellow Aussie, and glad to see Ubuntu working for you!

---

### Post by Russty of Oz on 2006-06-08
Would you believe it?!  I just opened  Application > Sound  and there it is!  I am sure it wasn't there yesterday.  Perhaps after closing down yesterday and booting today it decided to show it.  I am sure these computers just like making a fool out of me!  (yes, I know what you are all saying, I don't need a computer to do that!  It's just feels better to have some inanimate object to blame.)

Russty

---

### Post by Fornie on 2006-06-08
hello :)

everytime i open the .avi files i have this error message...

"it seems there is no xvideo support for your video card available"...

how do i go about this? thanks

---

### Post by neoflight on 2006-06-21
[QUOTE=Fornie]hello :)

everytime i open the .avi files i have this error message...

"it seems there is no xvideo support for your video card available"...

how do i go about this? thanks[/QUOTE]

i have the same problem when i ttry to play dvd on mplayer....no idea what to do?
i have all the codecs installed...

totem-xine doesn't even get past the initial dvd screen (copy right, fbi warnings etc)...same with VLC... i can only play dvd with mplayer...and it stops in between abruptly...(while playing)...i always have 2 mplayer window opened...one playing the dvd and the other with tha above error .... the problem is i cannot use the controls.... just have to watch the entire clip.... any clue/???

edit: solved !!! by

```
sudo aticonfig --overlay-type=Xv
```

and restart X by alt+ctrl+backspace

---

