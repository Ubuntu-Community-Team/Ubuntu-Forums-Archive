---
title: "Cube 2 install"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by xMAVERICKx01 on 2007-05-28
ok, let me get this out in the open, i am a complete newbie at this ubuntu/linux thing. i only know how to turn it on and search the web. I plan to remedy this situation by asking a lot of questions :D question number 1:

I need a complete walkthrough on how to install Cube 2 the game (I'm a gamer so most of my questions are going to be about games) Pretend I'm a complete idiot at this... because I am 8-[ lol to give you a quick idea of what my situation is I JUST extracted all the files from the compressed file I downloaded from the Cube 2 site. I have no experience in linux of any form but I'm a GOD at WinXP. My PC Stats are as follows:

Dell Precision 360 (2004)
Pentium 4 HT 2.4GHz
Integrated Sound Card
ATI Radeon X1300 XGE 512MB VRAM
1028MB RAM
DVD+DVD-R CD+CD-R Drive
and a 1600x1280 20.1" HD LCD
Ubuntu 7.04 (Fiesty Fawn)

All help would be greatly appreciated!

P.S. I'm still not sure of how to do admin stuff like alter "root" and "usr" folders.

what i need is something i can just like copy and paste into the terminal or sumtin of that nature, im really new at this and when i try to read the guides its like reading korean lol. any help would b much appreciated

---

### Post by starcraft.man on 2007-05-28
Uh, cube 2? What game is that (link pls)?  I'm not familar with it... only cube game I know is the shockwave series and you need windows for that since shockwave still not working on Ubuntu as far as I know. Assuming this is an Ubuntu app you downloaded though, I assume since it was archived that it is source. Read this for a guide to [installing from source]("http://www.psychocats.net/ubuntu/installingsoftware#source").

This is a [good guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") to learning everything else, and installing software you need in general.

I'll be frank though, Ubuntu isn't really a platform for gaming (even if we have WINE and Cedega, and they will let you play some of the better known games well). I mean it takes a lot of effort to get windows games to work in Ubuntu most of the time. If your a hardcore gamer, I dunno if you want Ubuntu. >.>

Anyway, good luck if your toughing it out with Ubuntu, its a good Linux distro for starting :).

Oh and, polls and discussions really should go in cafe... beginner is really for problems, not discussions (unless their about the solution).

---

### Post by eapache on 2007-05-28
What files have been extracted? If there is a .deb package, run that. Otherwise, find what looks like the main installer / program and post the file extension.

---

### Post by SoulinEther on 2007-05-28
I took a look at their website (google "Cube 2").. show me the files you have in the folder by ... using the terminal, going into the directory that you extracted the file into, typing dir and copying and pasting (using the right mouse button > copy because control+c won't work, I think) into a [ code ] [ /code] thing here... (minus those spaces). I didn't read much of their website. Might not need to do any installing; another game I downloaded a while ago didn't need any installing, it ran right out of the extract.

eapache beat me to the punch. :X

---

### Post by starcraft.man on 2007-05-28
Right, I did a search. I didn't think that first link was it, the name was well... odd. >.>

The instructions for installing are in the wiki, [here.]("http://cube.wikispaces.com/Beginners+Guide#tocBeginners%20Guide2") Follow the **nix directions. Seems its one game that runs better on linux than windows :p. The wiki is a bit of a mess, but I guess it has everything ya need, just block out everything not referring to *nix, they unfortunately mixed all 3 versions in >.>.

Otherwise like they said, tell us whats in the file. I guess I was wrong about the source, and they probably have a script to install.

---

### Post by xMAVERICKx01 on 2007-05-28
whoa, FAST response times guys nice work! lol
ok heres a list of the extracted files:
[folder] bin_unix
[folder] data
[folder] docs
[folder] packages
[folder] src
config.cfg
README.html (which i DID read by the way :p it just didnt help me any lol)
sauerbraten_unix (which reports as a shell script so I guess its the main install file but when i click on it it flashes this white window thing and disapears)

I have tried running the program in both terminal and display (what ever those mean) and nothing happened so... i dont kno.

need any other info let me kno i'll be here for a while listening to some tunes on VLC Media Player (beach boys rule!)

---

### Post by xMAVERICKx01 on 2007-05-28
> **starcraft.man said:**
> Right, I did a search. I didn't think that first link was it, the name was well... odd. >.>

The instructions for installing are in the wiki, [here.]("http://cube.wikispaces.com/Beginners+Guide#tocBeginners%20Guide2") Follow the **nix directions. Seems its one game that runs better on linux than windows :p. The wiki is a bit of a mess, but I followed through and it seems to have everything needed, just block out everything not referring to *nix, they unfortunately mixed all 3 versions in >.>.

Otherwise like they said, tell us whats in the file. I guess I was wrong about the source, and they probably have a script to install.

wow, thanks! I'm still stunned at how fast people respond to things on this forum. When I used to post questions on the windows thing I'd usualy wait a couple weeks :( lol much appreciated 

peace

---

### Post by SoulinEther on 2007-05-28
You've tried ./sauerbraten_unix from terminal? That flashing white window sounds like a terminal opening and closing after the script ended (prematurely it sounds).

Open the script with gedit (right click > open with) and paste what's inside it here....

and do a dir of what's in that bin_unix folder.

Unless... of course... the instructions suffice. :D

---

### Post by starcraft.man on 2007-05-28
> **xMAVERICKx01 said:**
> wow, thanks! I'm still stunned at how fast people respond to things on this forum. When I used to post questions on the windows thing I'd usualy wait a couple weeks :( lol much appreciated 

peace

Well good luck, seems very hands on installing, and I think it has to configed with the scripts. Hopefully ya can follow the guide, if not post back and someone else will help >.>.

Ya, the forum is pretty fast getting answers out, most of the time... still waiting on my PSP question... anyone happen to be a PSP hacker and reading this? If so check my posts pls :).

---

### Post by xMAVERICKx01 on 2007-05-28
ok i got it to run in the terminal and this came up:


  echo "Your platform does not have a pre-compiled Sauerbraten client."
  echo "Please follow the following steps to build a native client:"
  echo "1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed."
  echo "2) Change directory to src/ and type \"make install\"."
  echo "3) If the build succeeds, return to this directory and run this script again."
  exit 1
fi

any ideas?

---

### Post by xMAVERICKx01 on 2007-05-28
> **starcraft.man said:**
> Well good luck, seems very hands on installing, and I think it has to configed with the scripts. Hopefully ya can follow the guide, if not post back and someone else will help >.>.

Ya, the forum is pretty fast getting answers out, most of the time... still waiting on my PSP question... anyone happen to be a PSP hacker and reading this? If so check my posts pls :).

I LOVE my ex-psp (sold it for a graphics card lol) and i kno how to do SOME basic cracking on it, what u need? (or just tell me where ur post about it is and i'll look it up)

---

### Post by starcraft.man on 2007-05-28
> **xMAVERICKx01 said:**
> I LOVE my ex-psp (sold it for a graphics card lol) and i kno how to do SOME basic cracking on it, what u need? (or just tell me where ur post about it is and i'll look it up)

[Here it is,]("http://ubuntuforums.org/showthread.php?p=2738037#post2738037") I just want to play Ogg formats on it. A simple thought really.

Ok, I'm guessing the src folder has all the source files for creating the client. So, [this]("http://www.linuxcommand.org/lts0020.php#cd") is a guide for learning to navigate basically in the terminal (read the other ones later, to understand how to use the terminal effectively). Very useful to know. Then, you need to use the cd command to change to the src folder, and use this [guide]("http://www.psychocats.net/ubuntu/installingsoftware#source") to compile it for Ubuntu. Should work, methinks. Someone correct me if I made a boob >.>.

Hope that goes well, too bad they didn't compile a deb and rpm installer ahead of time for folks.

---

### Post by WHICKS on 2007-05-28
I installed cube2 by installing the tar files into the desktop, transferring to my home folder, and then extracted them there.  The game has crashed on me a couple of times, but my fragging is getting better in multiplayer.

Go to th sourceforge site and open .
[http://sourceforge.net/project/showfiles.php?group_id=102911](http://sourceforge.net/project/showfiles.php?group_id=102911)

highlight this version of the program and download to your desktop  sauerbraten_2007_04_15_spring_edition_linux.tar.bz2 

make sure this is in your home directory or copy it into your home directory.

go into that directory  

cd

tar zxvf /sauerbraten_2007_04_15_spring_edition_linux.tar.bz2 

go into your home folder and look for the icon and click on it and select "run" from the menu and it should open up.

You can also do this procedure from exclusively from the command line if you wish.

---

### Post by xMAVERICKx01 on 2007-05-29
> **WHICKS said:**
> I installed cube2 by installing the tar files into the desktop, transferring to my home folder, and then extracted them there.  The game has crashed on me a couple of times, but my fragging is getting better in multiplayer.

Go to th sourceforge site and open .
[http://sourceforge.net/project/showfiles.php?group_id=102911](http://sourceforge.net/project/showfiles.php?group_id=102911)

highlight this version of the program and download to your desktop  sauerbraten_2007_04_15_spring_edition_linux.tar.bz2 

make sure this is in your home directory or copy it into your home directory.

go into that directory  

cd

tar zxvf /sauerbraten_2007_04_15_spring_edition_linux.tar.bz2 

go into your home folder and look for the icon and click on it and select "run" from the menu and it should open up.

You can also do this procedure from exclusively from the command line if you wish.

ok first off i cant find the "cd" thing (idk if its a folder, a file..) and when i find the icon and i click on it it asks for [Run in Terminal] [Display] [Cancel] [Run] and i press [Run] and nothing happens... this is part of y i hav been so reluctant to use linux, its a pain to get anything to run on it lol with windows u just click install and its done (i kno i sound like a noob but thats because i am XD )

---

### Post by starcraft.man on 2007-05-29
> **xMAVERICKx01 said:**
> ok first off i cant find the "cd" thing (idk if its a folder, a file..) and when i find the icon and i click on it it asks for [Run in Terminal] [Display] [Cancel] [Run] and i press [Run] and nothing happens... this is part of y i hav been so reluctant to use linux, its a pain to get anything to run on it lol with windows u just click install and its done (i kno i sound like a noob but thats because i am XD )

**cd** is a command in the terminal. It means to "change directory", simply means to move to the folder you specified after the command. [Explanation of the CD command.]("http://www.linuxcommand.org/lts0020.php#cd")

Most applications are not difficult to install. The problem lies in the fact that you are brand new to linux (days new) and you went straight for doing a complicated task (installing a program from source, with auxiliary scripts for customization) rather than learning Ubuntu slowly from guides like [this one]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") and [this one]("http://www.psychocats.net/ubuntu/index.php") and even this [one for terminal]("http://www.linuxcommand.org/"). You really should take it easy and spend a bit more time reading about how things work, some users never compile from source (indeed, you never have to thanks to the repositories) thus for most people its rather new, I myself have only compiled a few programs when I needed to and they were much more basic than this.

It is possible to install programs as simply as in windows, they must fall under one of two categories though 1) they are a debian package, in which case like an .exe they can be double clicked and install (unlike an .exe they have mostly set configuration and just put the program in to the specified location). Or 2) they are in the repositories (consider them to be containers holding all of Ubuntu's basic programs easily accessed from the net) in which case you can click on the Synaptic GUI and install or execute a single command via terminal. So things can be easy to install, this just happens to not be one of them.

You picked a program that was neither. I imagine the devs didn't want to package the program due to the fact that it takes time and this was meant to be customizable, not to mention their are many package types and its not in our repos cuz its well not supported by Ubuntu, its an independent game.

There are other linux games much easier to install, maybe you should look at those and be patient while learning how to do such things. :)

---

### Post by Dekunuts on 2007-05-29
if you install software under the form of .deb files it's easy as it is in windows 
check 
[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)
and then download saurbraten (also named cube2) files and install them using gdebi (which should start automatically when the .deb is double clicked.

you may have to install them in a particular order to get the dependencies right, but gdebi will inform you of that.

cheers

---

### Post by starcraft.man on 2007-05-29
> **Dekunuts said:**
> if you install software under the form of .deb files it's easy as it is in windows 
check 
[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)
and then download saurbraten (also named cube2) files and install them using gdebi (which should start automatically when the .deb is double clicked.

you may have to install them in a particular order to get the dependencies right, but gdebi will inform you of that.

cheers

Silly me, I didn't even know there was a deb version on there. I should probably look around that site a bit more. That will get it installed, thanks for pointing it out. Do still read my guides I linked to though, you won't always find a compiled deb for something and it is always better to know more than less :).

I guess that resolves this thread, have fun with the game, oh and sorry for exposing ya to all that mess when there was a deb :p

---

### Post by xMAVERICKx01 on 2007-05-29
to starcraft.man:
OOOHHhhhh, i thought it was just a thing u install, i had NO idea u had to compile ANYthing lol. but yea i should probly spent sum time gettin to kno linux before i start COMPILEing anything lol. thnx for lettin me kno. i thought the icon was the installer file (durrr, i feel noobish lol)

---

### Post by xMAVERICKx01 on 2007-05-29
to Dekunuts:
ok, thanks! mucho apreciated :guitar:=D>

---

### Post by starcraft.man on 2007-05-29
> **xMAVERICKx01 said:**
> to starcraft.man:
OOOHHhhhh, i thought it was just a thing u install, i had NO idea u had to compile ANYthing lol. but yea i should probly spent sum time gettin to kno linux before i start COMPILEing anything lol. thnx for lettin me kno. i thought the icon was the installer file (durrr, i feel noobish lol)

Nope, anyway use the link [here]("http://www.getdeb.net/category.php?id=3") like Dekunuts (Zelda fan I assume :D) pointed out, you can then install the game from the debs available. It should then be in the menu and you can use it like any other program. Just search for cube 2 on it. Thats it, have fun.

Edit: Ok, ya noticed, off I go then to other things :).

---

### Post by Dekunuts on 2007-05-29
Glad I could help ;)

---

### Post by lambros on 2007-05-29
> **xMAVERICKx01 said:**
> ok i got it to run in the terminal and this came up:


  echo "Your platform does not have a pre-compiled Sauerbraten client."
  echo "Please follow the following steps to build a native client:"
  echo "1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed."
  echo "2) Change directory to src/ and type \"make install\"."
  echo "3) If the build succeeds, return to this directory and run this script again."
  exit 1
fi

any ideas?

Hi, I'm pretty familiar with running this game on Ubuntu, maybe I can help?  Looks like you've managed to run "./sauerbraten_unix" from the correct directory, to get this message, so you're on the right track.

I'm still a bit confused exactly where you've extracted your files.  In your Terminal window, could you verify that typing ```
./sauerbraten_unix
``` does indeed bring up the message above.  Then type in the command ```
pwd
``` and please post the result here.

The message indicates that you're trying to run sauerbraten on a slightly-unusual system.  My guess is you've installed the 64-bit version of Ubuntu instead of the 32-bit version.  Please could you check this by opening a Terminal and running the command ```
uname -a
``` and post the result here?

Assuming my guess is right, it will take a bit of work to get this game running, unfortunately.  There are a few paths you could take here:

1) Install the 32-bit version of Ubuntu and try again :(
2) Try to get the 32-bit version of sauerbraten running on your system.  This involves installing a few 32-bit compatibility libraries that are needed by the game.
3) Try to compile a 64-bit version from the source code provided.

I have successfully got both of 2) and 3) to work on my system, so it certainly can be done in theory.  I fear option 2) might be a non-starter due to the difficulty of getting hold of the needed libraries (for example, a 32-bit version of libpng.so.3 doesn't seem to be readily available).  You might be lucky, though - try running this Terminal command:
```
bin_unix/linux_client
```
from your sauerbraten folder.

So it appears the easiest route for you might be option 3) - build the game yourself from source code.  Don't worry, it's actually not that hard to do for this game - the authors have been very helpful in writing scripts for this, and I could walk you through it if needs be.  But you **will** need to use the Terminal a lot, there's no way round it, sorry!  :-)

Do feel free to post any questions you have - I know this kind of thing can be very daunting if you're totally new to GNU/Linux.

Lambros

Edit: It appears there might be an option 4) - find a Debian package suitable for your system and install that.  Best of luck with this, hope it solves your problem - it's a great game if you manage to get it working!

---

### Post by xMAVERICKx01 on 2007-05-29
ok i got it installed (along with a lot of other games from getdeb.net) thanks for ur help! and if you want to play me on Action Cube my name is Bravo_3 k? thnx!

---

### Post by whistlerspa on 2007-06-10
I admire your grit and determination  but how long did you spend on this - me I just reach for a PS2

---

