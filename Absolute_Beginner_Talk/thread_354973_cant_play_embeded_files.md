---
title: "cant play embeded files"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-06
Hello.
ive just discovered that i cant play things like movie trailers from websites, i get an error about not having the right hxplay or real play to use an an embeded player, ive looked about but not really found anything that helps, does anybody have any suggestions or know of a how to, if i click on windos medi to play the trailer i get the error i mentioned above, if i click quiktime swift comes up with a message saying i need to install plugins, but it doesnt know what plugins to install ?
cheers.

---

### Post by meng on 2007-02-06
You may wish to install mplayer and the firefox plugin associated with that.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

or perhaps you would like to use Automatix
[www.getautomatix.com](www.getautomatix.com)

---

### Post by techno-mole on 2007-02-06
nothing i found from the first link has worked, and the only real player i can find in automatix wont install on an amd64 pc, is there an alternative that will work ?
cheers

---

### Post by meng on 2007-02-06
Ah, AMD64 installation, that's fairly important information to know!! I don't know the answer then (that's why I chose to install a 32-bit system instead).

---

### Post by ^rooker on 2007-02-06
It would be interesting to know which format those movie trailers are stored as.
It's rather strange that after installing all *ugly*-codecs you still can't play something.

But anyway, you could try [easyubuntu.org]("http://easyubuntu.freecontrib.org/"), but recently I've experienced some problems with their freecontrib.org repositories...


In case you ONLY have this problem for a specific source of trailers, you might consider VLC player - that one also has a lot of codecs compiled into it. I used it recently to watch .mov movie trailers in quicktime (.mov) format.

---

### Post by r4ik on 2007-02-06
Try,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

Instructions for AMD64 there.

Good luck !

---

### Post by techno-mole on 2007-02-06
my appologies about the amd 64, maybe then there is no answer to this particular problem ? at least not on the amd 64 platform anyway :confused:

---

### Post by techno-mole on 2007-02-06
ive tried, vlc player, and things from the other links, but nothing works, although if i do sudo apt get command to install mplayer (was in one of the how to's) it says that it is already installed ?
but fire fox and swift fow are still saying they cant play the trailers (which by the way are on yahoo)

---

### Post by r4ik on 2007-02-06
Did you saw the AMD tip in green below it ?

---

### Post by techno-mole on 2007-02-06
thats the first thing i tried, didnt work, ive since tried alot more, apparently you can play files like that with vlc player, but ive installed it and it still wont work, maybe i need to tell it which one to use ? like its maybe trying to use a default player to play these type of files, but the default player cant actually play the files ? if that makes any sense :)

---

### Post by r4ik on 2007-02-06
I would use Mplayer but could you post you're sources.list ?

sudo gedit /etc/apt/sources.list

---

### Post by RomeReactor on 2007-02-06
You should also make sure **only one** video plugin for Firefox is installed, as I've found that having multiple ones seems to confuse the browser as to which one to use. Open Synaptic and search for **mozilla**; then look for entries mentioning **vlc, mplayer, totem, helix**, and uninstall the ones you don't want (i suggest just leaving mozilla-mplayer).

---

### Post by techno-mole on 2007-02-07
@r4ik
my sources list below.
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025.1)]/ edgy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main-all
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) edgy misc multimedia

ive tried removing all the players appart from the mozilla mplayer one, so im now going to try it, cheers for the help.
ive removed all but the mplayer and it still wont work ?  i think ill try removing every type of player like that and install them one at a time and see what happens ? id rather not but if there is no alternative i may have to.
cheers.

---

### Post by techno-mole on 2007-02-08
ok, ignore my last posts, ive just installed the 32 bit version of edgy, im now using edgy as my primary system (will still have to play games on windows though)
anyway as this is a fresh install i thought i would try playing embeded files, like movie trailers and so on, but there wont play, the error i get is - Totem could not play 'mmsh://media-virginmedia-movies.mymovies.net/filmmedia/film/fid4915/trailers/trid2604/wm/bb.asf'.
and under it, it says - There is no input plugin to handle the location of this movie, now ive used automatix to install various players and none of them work ? realplayer, mplayer and all the rest will not play any type of file such as the one that i got this error message from.
im at a complete loss :confused: 
any help will be appreciated.
cheers

---

### Post by jackrobinson on 2007-02-08
have you installed multimedia codecs and AUD-DVD codecs from automatix2?

---

### Post by techno-mole on 2007-02-08
yep, ive installed all codecs and such like, im currently trying one media player at a time, eg-removing them all and starting one at a time, ill figure it out one way or the other.

---

### Post by techno-mole on 2007-02-08
ive done it, i can now play film trailers, ive tried 2 different sites (virginmedia.com and yahoo films, couldnt play anything from these 2) 
what i did was to use automatix to remove eveything, eg remove realplayer, mplayer, i used synaptic to remove totem, i also removed both sets of codecs, then using automatix i installed - the aud-dvd codecs, the multimedia codecs and realplayer, and listen media manager, now it all works ? well it all works so far.
cheers for the help.

---

### Post by tontog on 2007-02-09
Same problem, the codecs are crashing. I've looked all through the forums ( I could have missed it) and can't find a solution. I can play some on "You tube", but none on Yahoo. If I find a solution, I will post it.




1.2 AMD Athlon- 512 ram

---

