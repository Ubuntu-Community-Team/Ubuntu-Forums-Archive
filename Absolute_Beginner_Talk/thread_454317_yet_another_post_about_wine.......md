---
title: "yet another post about wine......"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-25
ok, im posting again to try and clear some things up, ive got a little confused about things.
ok i want to install wine, but not for running any programs, i want to use it to try and run games with it, the reason is because im trying to prove to my other half and the kids that linux is viable alternative over windows (i refuse to buy and install vista, and for the moment i have to use xp for playing games, but thats all i use it for) but in order to prove linux is a good idea i have to make it work in a way thats easy to use (ubuntu is very easy to use) but what i mean is that when my other half or the kids click on something they want it to run and they can then do what they  need to.
so for example - kid no1- i want to play sims2 - kid no1 then clicks on an icon and it loads etc etc
i know this may not always be possible, but to be honest this doesnt always work with windows anyway. but you get the jist of what im saying.
it doesnt bother me because games i like (such as doom3 and others) will run under linux anyway, and some of the other games are being ported to linux, but for others im going to need a program like wine or cedega (havent tried cedega yet, next on the list) so i need to get one of them working.
for the time being thats wine, but for the life of me i cant get it to run, every guide i have used results in a complete system lock up, and the only way to get out is press the re-start button on the case (nothing else works, ive tried things like ctrl and c) ive installed wine and wine tools but because i cant get wine to run winetools wont run properly either.
ive heard that wine doesnt like 64 bit architecture, but does this mean the 64 bit version of ubuntu ? or just any pc with a 64 bit cpu ? (im using an amd athalon 3200) i installed the 32 bit version of ubuntu (fiesty) because i had trouble using the 64 bit version of edgy ( i know alot of stuff has been fixed now) so surely wine should run ok on my 32 bit ubuntu install ? unless of course its something to do with 64 bit cpu's.
ive tried to install the 64 bit wine version, but i cant get very far because the guide says you need to apt-get some stuff first " Building Wine on 64-bit Debian

   1. apt-get the following packages:
          * ia32-libs (you need version 1.18 at least)
          * libc6-dev-i386
          * lib32z1-dev

which is where im having trouble because if i use apt-get or sudo apt-get etc etc all i end up with is - danny@HAL:~$ sudo apt-get ia32-libs
Password:
_E: Invalid operation ia32-libs_
 i get the - E: Invalid operation ia32-libs for all 3 of the files the guide says to apt-get, so if i cant apt-get them how am i supposed to even get close to installing wine ?
ive tried using programs like automatix - result - system lock up - press restart button to get out.
ive tried installing with synaptic - result - system lock up - press restart button to get out.
im sorry for the length of this post, but this is really frustrating, everything else has been a breeze, installing nvidia drivers (i used envy) went well (i can even overclock the card using coolbits) i edited the /X11/xorg.conf to start up with the resolutions i want, ive installed beryl with no problems (couldnt remember how you got it to run at start up, but fixed that) and all the other stuff has been fine, 
but can i get wine to work - ](*,) in a word no !
im going to give it a rest with wine and try cedega and see what happens, but i thought id post because someone may have had the same problem and might have a solution i havent tried yet.
cheers and sorry again for the length of the post (@ moderators, if its too long remove it and let me know, i can shorten it)
cheers again

---

### Post by justifier on 2007-05-25
to use apt-get you need to do

sudo apt-get install <package>

---

### Post by Terl on 2007-05-25
I find this kind of funny:  > ok i want to install wine, but not for running any programs

A game is a program :)  Anyway, check at winehq and read their docs carefully.  I know you have had some difficulty with it.  I referred you in another thread to info at winehq pertaining to 64 bit architecture.

Also check the apps database and make sure the games you will be using work through wine.  Not all of them do and some might not work the way you want them to.  To be honest I just kept windows xp on my system to use as a gaming portion.  I figured why install wine when I have a valid windows license and can just play games on XP.  I hardly ever log into it because I am having to much fun doing other things.

I also read a lot of "I am not getting Vista".  I am not either, but until games won't work in XP I could care less about Vista.  There is no sudden need to ditch XP.  If you and your family need to keep it for gaming it is no big deal.  This also would allow them to get to learn Linux if you kept the dual boot for a while.  

I know if my kids were young again and I had to do this all over (I'm a grandpa now :)  my youngest kid is 26) I would just buy them a console and keep the pc stuff for myself.

---

### Post by techno-mole on 2007-05-25
ok, granted a game is a program, but its not like running word or open office.
i figured that if the guides on the wine hq website dont work then i dont have much hope of getting it installed.
ive tried the winehq how to for installing on 64 bit but i cant get past download the first instruction, which is to download ia32-libs and 2 other files, acording to the guide all you need to do is apt get them 3 files and then you can start installing wine, when i try - for example the first package - sudo apt-get  ia32-libs - returns - E: Invalid operation ia32-libs, if i try - sudo apt-get install ia32-libs i then get - Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
and thats as far as i can go, with out those files i cant install wine for 64 bit, because it needs those files, if i carry on through the guide wine wont install properly.
i know what your saying about xp, i have 2 80gig sata drives, one has a modified xp install on it and the other has ubuntu (7.04) i have the ubuntu drive set to boot before the xp drive, and if i want xp i just hit f12 at start up and boot the samsung sata drive (where xp lives) this isnt a problem for me, but for the other half and the kids it would bother them too much, like i said they just want to click and go so to speak, if i set up xp and ubuntu on the same drive and dual boot it will cause problems.
ill have to do more reading about wine, if it turns out not to be viable for games then ill give cedega a go, but ive heard people moan about it because its not " free " as such, i think you have to subscribe ?
cheers for the help though.

---

### Post by meng on 2007-05-25
Okay if I read your posts correctly, you are running a 32-bit Ubuntu installation on a 64-bit machine. If this is the case, you don't need to install ia32-libs (and in fact you can't, because the package only exists for 64-bit installations). All you should need to do is:
sudo apt-get install wine

ASSUMING that you have universe repositories enabled.

---

### Post by techno-mole on 2007-05-25
yes i know you can do apt-get and install wine, this isnt the problem, the problem comes from trying to run it.
so for example - sudo apt-get install wine - downloading and stuff goes on, all is well - now here it comes - winecfg - system locks totally (no other way of getting out, but to restart by pressing restart button, when i say total i mean total, nothing works hence pressing the restart button)
it doesnt matter what command i use if its anything to do with wine the result is the same - system locks up, ive installed it so many times in so many different ways all to the same end, and that is a total system freeze, i cant run winetools to help configure things because wine wont run, it was the same on edgy when i tried it just wont play.
im not joking ive tried around 10 different ways of installing and running wine, none work, not even a little.
so i am at a complete loss with it all.
cheers

---

### Post by meng on 2007-05-25
Can you elaborate on exactly what happens if you type at the terminal:
wine

(or what happens when you type "winecfg")
I want to know exactly what this "system lock" is, rather than assume I know.

---

### Post by techno-mole on 2007-05-25
ok here goes - from start to finish, and various ways.

1- sudo apt-get install wine - required files download and install, then i type in terminal - winecfg and the result is the system locks up, by system locks up i mean that nothing will work, the best way to describe it is that although the screen is displaying an image the system is as good as switched of, it doesnt matter what you try and do you get no response at all, and if you want to get out of it you have to hit the restart button on the pc case, i did once leave it to see if it was just taking its time, after an hour i decided to hit the restart button.

2- using automatix - find wine and install, according to the instructions for wine it says once installed run winecfg in terminal (not using automatix at the moment, this is from when i had edgy installed) so open terminal and type winecfg - result - see " 1-" above.
i can type anything into terminal once ive installed wine, someone said in a thread from a while ago try wine notepad or something similar - result - see "1-" above.
like ive said ive tried many guides/how to's and ive followed the instructions to the letter and all have the same result the system locks up, its like its been switched off, even though it hasnt, theres no hard drive activity nothing,nada,zip

see the problem isnt installing wine, i can do that with my eyes closed now (ive done it many times) after every time ive tried ive removed it totally and tried again.
so i can install it fine no trouble at all, but i cant use it, every command results in the lock up ive been trying to describe.
just to clarify - 
type wine = system locks up
type winecfg = system locks up
type winenotepad = system locks up.
every wine command you need to use to get it configured does the same
and it was the same when i had edgy installed, im now using fiesty, and just for the record wine is the only thing i havent been able to install.

---

### Post by meng on 2007-05-25
Okay, then for starters don't install/reinstall any more (unless someone can give you a reason why that might do some good). I would delete the configuration files, which are located in ~/.wine
Just open a terminal, you should already be in ~
and type
rm -r .wine
(conceivably you may need to "sudo rm -r .wine")

then try running wine again.
Unfortunately, in my experience, "apt-get purge" does little if anything to actually purge the configuration files for programs.

---

### Post by techno-mole on 2007-05-25
with wine installed the command sudo rm -r .wine returns cannot remove wine, no such file or directory.
so if ive done - sudo apt-get install wine and wine is downloaded and installed, if i then run the command as above i then get the error mentioned above.
either way i am still getting the lock up.
the only thing i can think of is that there is some kind of conflict on my system which is preventing wine from being installed correctly, or if its being installed correctly something on my system is then stopping it from running as it should, the probelm is i have no idea what that could be ?
cheers

---

### Post by meng on 2007-05-25
Hmm, sorry I'm out of ideas.
By the way, to take your example, Sims 2 is reported as not working very well with the latest version of wine, and has a low playability rating with cedega too. I know that's not your issue right now, but thought you'd like to know.
You can go to [www.winehq.com](www.winehq.com) (appdb) or [www.cedega.com](www.cedega.com) to search for how well a game plays with wine/cedega.

---

### Post by techno-mole on 2007-05-25
cheers im looking into cedega, ill do alot of reading first before installing it though.
and the other option is doing on the other 2 pc's we like ive done with mine, basically i have 2 80gig sata drives, one with ubuntu on for doing eveything like e-mail, browsing the internet etc etc, the other drive has a modified xp install on it for playing games, so ive set the ubuntu drive as the first hard drive to boot, and if i want to play a game i hit f12 and select the xp drive, so i may just buy 2 new hard drives and install them in the other 2 pc's
cheers, i shall still keep looking for an answer to why wine wont work on my system though, maybe its because i have an nforce main board ? who knows, tis a puzzle though.
:D

---

