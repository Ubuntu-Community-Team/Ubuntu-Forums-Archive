---
title: "real player for Ubuntu"
date: 2004-11-26
forum: Apple PPC Users
---

### Post by eggie on 2004-11-26
downloaded the linux installer from real.com chmodded it then got error couldnt run executable?
Anyone know what gives?
 \\:D/

---

### Post by conufsed on 2004-11-26
What is the actual error message you get?

---

### Post by slux on 2004-11-27
The Realplayer version available for GNU/Linux is compiled for x86; there doesn't exist one compiled for PPC AFAIK. That's the way non-free binary-only packages for GNU/Linux usually are I'm afraid. The same issue comes up at least with the Nvidia non-free 3d-accelerated drivers, Macromedia Flash, people using Linux on anything else than x86 are out of luck.

If you were after the capability to play Realmedia files, mplayer can play some older clips natively and I guess will eventually support the newest formats too. If for some reason you wanted to have the player for it's other features you can get the Helix player which is a free software media player done by Real which they modify (adding the proprietary codecs for example) and release as Realplayer.

I wish people would use free media formats as [Xiph](http://www.xiph.org/) is offering quality options for most purposes...

<edit>
Oops, I stand corrected about the RP bit. Seems things have improved somewhat after Helix/RealPlayer10 were released.
</edit>

---

### Post by conufsed on 2004-11-27
Incorrect, the powerpc version of real player is available from [https://helixcommunity.org/project/showfiles.php?group_id=154](https://helixcommunity.org/project/showfiles.php?group_id=154)

---

### Post by eggie on 2004-11-27
thanks fellas much appreciated i find it hard to envision life without the bbc

---

### Post by mach_zero on 2004-11-28
Hey guys, thanks for the links! Just wanted to share a caveat concerning Realplayer on what appears to be all flavors of Debian based Linux distros. When I first downloaded and installed Real, it wouldn't start up. I googled the problem and apparently what you need to do is go to the plugins folder inside of the RealPlayer folder and delete the files "swfformat.so" and "swfrender.so". Ran like a champ for me after that.

---

### Post by adamward on 2004-11-28
OK, I'm a terrible newbie at this linux thing, so please bear with me on this stupid question.  I have found the "helix realplayer" files, and downloaded the .bin file for PowerPC.  What do I do now?  I tried to double-click the file, and nothing happened.

I've tried to do some searching on google, but I'm not even sure what to search for, so any help would be greatly appreciated!

Thanks for helping a newbie learn the joys of linux!

--adam

---

### Post by eggie on 2004-11-29
[QUOTE=adamward]OK, I'm a terrible newbie at this linux thing, so please bear with me on this stupid question.  I have found the "helix realplayer" files, and downloaded the .bin file for PowerPC.  What do I do now?  I tried to double-click the file, and nothing happened.

I've tried to do some searching on google, but I'm not even sure what to search for, so any help would be greatly appreciated!

Thanks for helping a newbie learn the joys of linux!

--adam[/QUOTE]
 hey me too -total newb to linux however lemme see if i can help.
cd to the directory where the .bin is 
in terminal
chmod +x  whateverthefile.bin
./whateverthefileis.bin
it will ask you what directory you want the install  put in the path suggested by the installer in the terminal window.
when the installer finished go to that directory and look for the hxplay or realplayer binary
(it will have a little .sh on it i think) double click and a message will popup choose run

good luck

---

### Post by adamward on 2004-11-29
[QUOTE=eggie]hey me too -total newb to linux however lemme see if i can help.
cd to the directory where the .bin is 
in terminal
chmod +x  whateverthefile.bin
./whateverthefileis.bin
it will ask you what directory you want the install  put in the path suggested by the installer in the terminal window.
when the installer finished go to that directory and look for the hxplay or realplayer binary
(it will have a little .sh on it i think) double click and a message will popup choose run

good luck[/QUOTE]
 Eggie, that worked great!  Thanks for the help.  Now I just need to learn how to play DVDs *LOL*

--adam

---

### Post by eggie on 2004-11-29
adam im totally lost with linux too but ive managed to get everything up and running. Just ask and Ill try to remember how i did it ! no guarantees lol btw xchat under applications connect to freenode server and join #ubuntu  lots of guys there who are really knowledgeable maybe see you there   my log is dad
 cheers

---

### Post by eggie on 2004-11-29
dvds ?

fire up synaptic   if you have the universe repositiories set  hit search button look for xine
just select it for install and there ya go  instant dvd playing  you might have to do
sudo hdparm -d 1 /dev/whateveryourcdromplayeris ( prolly /dev/hdc  or /dev/cdrom)
 if you find dvds stuttering at all. cheers

---

