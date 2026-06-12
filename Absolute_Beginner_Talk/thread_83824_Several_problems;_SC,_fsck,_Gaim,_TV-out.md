---
title: "Several problems; SC, fsck, Gaim, TV-out"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by Iesos on 2005-10-29
I've got a few problems:
1. I wonder if anyone got a good "How to" for installing starcraft. I have heard it should work with only wine/xwine, but how? Mine says something like: "No start-meny present" (not exactly but close).
2. When i boot my computer, i reach the "Checking file systems"-part. And there it crashes. It says somthing like "Could not check hdb1, repair manually". I can still start Ubuntu, no problems i just press 'Print Screen' and then im in single-user-mode then its just Ctrl+d to start Ubuntu. And my hdb1 (my /home) seems too work fine. So i want to solve this either by Repair my hdb1 manually, but how? Or i want to turn off the fsck (File System ChecK) in my boot sequence, if possible, how?
3. (Not realy a problem, not 100% ubuntu either) Is there a tool in Gaim for using pictures like in msn?
4. I would like someone to tell me if there is a way to get TV-out for my nVidia card. (TNT-2 something) I have used it in windows, but i cant find any "how to"'s that works with my card (or i might have other problems). So can someone give me a few links to nVidia "How to TV-out", and tell me (if anyone knows) if my card is supported by nVidia's tv-out tools in linux. (I have old nVidia drivers becouse my card isnt supported by the latest drives).

Well, thats about it, for now. Thanks in advance.

---

### Post by shandar on 2005-10-29
[QUOTE=Iesos]I've got a few problems:
1. I wonder if anyone got a good "How to" for installing starcraft. I have heard it should work with only wine/xwine, but how? Mine says something like: "No start-meny present" (not exactly but close).[/QUOTE]
Hm, I don't have a howto, but install wine (I used the one that is available in the repositories) and configure it using wine-config. Then insert your starcraft cd and double click the setup file. Both warcraft 2 and Warcaft 3 works perfectly for me so starcraft should be possible aswell :-)
[QUOTE=Iesos]3. (Not realy a problem, not 100% ubuntu either) Is there a tool in Gaim for using pictures like in msn?
[/QUOTE]
It's already there in the version of Gaim that comes with ubuntu. To set your own buddyicon go to Tools (Verktyg) -> Accounts (Konton), select your MSN account and press edit. There are two buttons, one for deleting your current buddyicon and one for loading a new one.

---

### Post by Iesos on 2005-10-30
Thanks, but i need more specific instructions on how to 'configure wine with wine-config', what am I suppose to configure? And where are this wine-config? I have wine installed (xwine too) when i dubble-click the setup.exe i get the following massage: "No program start menu found."
I have heard that there can be some .dll 's missing (becouse i dont have windows installed), could that be the problem.
I think you mean that I should 'configure' wine so it will work, but i need some help to do that.

Gaim works at least :)  Tack!

---

### Post by Iesos on 2005-10-30
Okey! Ive gort starcraft up and running.
My advice for people im my posistion:
Follow this how to:
[http://www.ubuntuforums.org/showthread.php?t=45407&highlight=wine+start+menu](http://www.ubuntuforums.org/showthread.php?t=45407&highlight=wine+start+menu)
If that doesnt work (it didnt for me) try do some of this too:
[http://www.ubuntuforums.org/showthread.php?t=45231&highlight=wine+start+menu](http://www.ubuntuforums.org/showthread.php?t=45231&highlight=wine+start+menu)
If it still doesnt work (it didnt for me) just try to install wine:
$ sudo apt-get install wine
And try again. Now it did work for me :)

---

### Post by Mustard on 2005-10-30
With regards to fsck, you can only run fsck on a drive when its not mounted.  If you have a liveCD you can use that to boot up and then try running fsck from the liveCD.

Type ```
man fsck
``` to find the manual for fsck.

---

### Post by Iesos on 2005-10-30
Ok, sorry i lied earlier.
Starcraft aint working, just the installer. Now ive gor starcraft + brood war. But i cant start the game. It says it cant find the cd. In the wine config file it says the right locations to my cdrom mount points, but doesnt work anyway. 
Help please.

---

### Post by shandar on 2005-10-30
Wine does not emulate copy protection AFAIK, you need to get either Cedega - a verison of wine specialized in gaming (which costs money) or get a NoCD crack from [www.gamecopyworld.com](www.gamecopyworld.com) (which is LEGAL if you own the game, I'm not promoting piracy ;) ).

Lycka till!

---

### Post by Iesos on 2005-11-01
But, what purpus does StarCraft serve if you cant play battle.net?
There must be some other way!
Can't you crate some kind of cd-image that is exact to the cd and then mount it in a way that starcraft can find it? (i have no idea)

oh, and i fixed the fsck problem. i just let the computer boot for 15 minutes and then its working as usual again.

---

### Post by GreyFox503 on 2005-11-01
Creating and mounting cd images is really easy.  To create a cd image, run something like :

```
cp /dev/cdrom mycd.iso
``` 
with the appropriate directory for the CDROM and the whatever name you want the file to be. This should create a roughly 600MB file that is the image of the disc.

To mount an image, run :

```
mount -o loop mycd.iso /media/fakecd/
``` 
The above command might require root privileges but I don't remember. If it says something about it, use sudo to mount it. You can mount an image to any directory you want, but I usually create a new one in my /media folder.

Unmount it in the normal way:

```
umount /media/fakecd
``` 
Root privileges might apply here also.



Hope that helps. :)

---

