---
title: "how do i install things?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-09
a bowle of spagetti, and after you get to the end of a noodle wich seems to take weeks, you get a gold nugget if you can suck it up and stick with it.. i fear,, i will never see the golden nugget,,

display drivers wont install they only unpack, firefox wont update, it mearly unpacks more files, with no where else to go except the desk top. 

nothing works,

---

### Post by MenZa on 2007-08-09
Try and be more specific. What doesn't work? What have you tried? What error messages does it give you?

---

### Post by overdrank on 2007-08-09
> **jake16424 said:**
> a bowle of spagetti, and after you get to the end of a noodle wich seems to take weeks, you get a gold nugget if you can suck it up and stick with it.. i fear,, i will never see the golden nugget,,

display drivers wont install they only unpack, firefox wont update, it mearly unpacks more files, with no where else to go except the desk top. 

nothing works,

Hi you make those comments after you have been posting questions for only less than a day? Good luck to you then and hope you find a OS that you like. :guitar:

---

### Post by Rocket2DMn on 2007-08-09
Is there a question in there?  We'd be happy to help if you could be more specific.  For example, what kind of video card do you have?  What have you tried to get it to work exactly?  What was actually wrong with it to begin with?

---

### Post by jake16424 on 2007-08-09
ive downloaded 2 updates, realtek audio drivers for linux, and mozilla for linux,, and they just unpack,, wtf, that doesn't update anything, 

im frustrated,, i need help, if i can't understand how to install things, then im not going to use ubuntu, even though its beasty...:confused::confused::confused::confused:

---

### Post by livingtarget on 2007-08-09
If you want to update firefox then just use the update manager it should draw in any new firefox versions that Ubuntu provides. You don't need to install firefox manually ever. 

Try and use the restricted manager to upgrade your graphic drivers for you, with luck it'll do it all for you.

Restricted Manager: System -> Administration -> Restricted Manager
Update Manager:System -> Update Manager

---

### Post by jake16424 on 2007-08-09
> **overdrank said:**
> Hi you make those comments after you have been posting questions for only less than a day? Good luck to you then and hope you find a OS that you like. :guitar:

i have, ubuntu, windows is more friendly to the user, IE: you dont have to know script to update your internet browser, and, you dont have to use commands to install macromedia flash player

i have a Nvidia GEforce FX5500 AGP

and, i havent done anything for graphics, cause i can't even update my browser,, so im sure my graphics would make me cry..if i tried. and failed like everything else has..

---

### Post by jake16424 on 2007-08-09
> **livingtarget said:**
> If you want to update firefox then just use the update manager it should draw in any new firefox versions that Ubuntu provides. You don't need to install firefox manually ever. 

Try and use the restricted manager to upgrade your graphic drivers for you, with luck it'll do it all for you.

and where is this mirical device located? =) a thread of hope  wheheeeeee

---

### Post by dreadlord_chris on 2007-08-09
[How to install ANYTHING in Ubuntu!]("http://www.monkeyblog.org/ubuntu/installing/")

---

### Post by happysmileman on 2007-08-09
> **jake16424 said:**
> and where is this mirical device located? =) a thread of hope  wheheeeeee

There should be an icon in top-right corner, an orange one that will tell you if you have updates waiting... Don't ever try to install/update anything manually if you can avoid it, unless you really know what you're doing

---

### Post by jake16424 on 2007-08-09
> **happysmileman said:**
> There should be an icon in top-right corner, an orange one that will tell you if you have updates waiting... Don't ever try to install/update anything manually if you can avoid it, unless you really know what you're doing

yeppers, i really dont know what im doing, but the auto update doesnt work for my video card, wont install anything,, for it. nada,, not a thing,, no display driver,

and the sound drivers wont work they just unpack themselves, and thats the end of the book.

---

### Post by jake16424 on 2007-08-09
> **dreadlord_chris said:**
> [How to install ANYTHING in Ubuntu!]("http://www.monkeyblog.org/ubuntu/installing/")

thankyou. but, still, not to helpfull, pointed me in the right direction. but i cannot get what i need.

1. Nvidia Nforce drivers for a Geforce FX5500 video card.
2. audio drivers, Realtek 97.

---

### Post by livingtarget on 2007-08-09
> **jake16424 said:**
> and where is this mirical device located? =) a thread of hope  wheheeeeee

updated my post minutes after :)

---

### Post by K.Mandla on 2007-08-09
Can you give us more information about your computer? It will help to know what brand and model you're using, and if possible, the brand and model of your video and audio hardware.

---

### Post by jake16424 on 2007-08-09
> **livingtarget said:**
> updated my post minutes after :)

yeah i installed EVERY update as im a newb and figure you can always get rid of what you don't need. still no sound. and it didnt install anything that said realtek. or nvidia.:confused::(:(:(

---

### Post by K.Mandla on 2007-08-09
I've merged your threads so we can keep all the pertinent information together. That will help other community members help you.

For the nvidia card, you should be able to install the proprietary (company-written) drivers through the restricted driver manager. I believe that's part of the System menu in Gnome, if you're using straight Ubuntu.

---

### Post by Rocket2DMn on 2007-08-09
So what's wrong with your video card?  Just bad resolution?  If so, use this configuration to get back on track:
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you questions about your hardware - use TAB to move between options and SPACEBAR to select/enable.  On the video drivers page, choose "nv" and on the resolutions page, enabled your monitor's max resolution and everything less.  Then restart the X-server (GUI) with CTRL+ALT+BACKSPACE.  Log back in and you can set your resolution with System->Preferences->Screen Resolution

If you really want to install the restricted drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

to update from the command line:
```
sudo apt-get update
sudo apt-get upgrade
```
The latest version of firefox is in the repositories, so you should get it if you don't yet have it.

---

### Post by jake16424 on 2007-08-09
> **K.Mandla said:**
> I've merged your threads so we can keep all the pertinent information together. That will help other community members help you.

For the nvidia card, you should be able to install the proprietary (company-written) drivers through the restricted driver manager. I believe that's part of the System menu in Gnome, if you're using straight Ubuntu.

thank you =) ok, for what pc im using

i built my own, mobo is a Epox mobo 8KDA+ pro AGP slot. with realtek audio chipset.
Nvidia Nforce3 250gibyte north bridge, and south bridge i forgot what it is.

AGP card is a Nvidia Geforce FX5500 gpu.

3 hard drives 2 sata for windows, 1X 160gig and 1X 200gig

and 1 IDE for ubuntu.

2 cd roms.

---

### Post by Jimmyfj on 2007-08-09
In System>Administration you'll find two things that you need: Restricted Drivers Manager and Update manager. In Software sources you can choose which reps you want added. Just click the Updates tab and mark the backports too if you like. It's as easy as that.

---

### Post by jake16424 on 2007-08-09
> **Jimmyfj said:**
> In System>Administration you'll find two things that you need: Restricted Drivers Manager and Update manager. In Software sources you can choose which reps you want added. Just click the Updates tab and mark the backports too if you like. It's as easy as that.

yeah i dont have that restricted driver thingy,

---

### Post by kavon89 on 2007-08-09
He has a 5 series Nvidia card. From what I've seen on Nvidia's website, the oldest card supported by their drivers would be a 6100.

System -> Administration -> Restricted Drivers Manager.  Does it say Nvidia display driver enabled? If not, I would recommend that you enable it, then restart for it to take effect.

Realtec AC97 is probably the most common audio device in PCs. I wonder why yours isn't working, it should be fully supported right out of the box.

---

### Post by jake16424 on 2007-08-09
> **Rocket2DMn said:**
> So what's wrong with your video card?  Just bad resolution?  If so, use this configuration to get back on track:
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you questions about your hardware - use TAB to move between options and SPACEBAR to select/enable.  On the video drivers page, choose "nv" and on the resolutions page, enabled your monitor's max resolution and everything less.  Then restart the X-server (GUI) with CTRL+ALT+BACKSPACE.  Log back in and you can set your resolution with System->Preferences->Screen Resolution

If you really want to install the restricted drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

to update from the command line:
```
sudo apt-get update
sudo apt-get upgrade
```
The latest version of firefox is in the repositories, so you should get it if you don't yet have it.



how do i get it,, ive downloaded the update about 4 times over the last hour, and every time that damned archive manager extracts them, and thats it,, nothing else,, dead end,, idk what todo with the files after there sitting on my desk top..

---

### Post by jake16424 on 2007-08-09
> **kavon89 said:**
> He has a 5 series Nvidia card. From what I've seen on Nvidia's website, the oldest card supported by their drivers would be a 6100.

System -> Administration -> Restricted Drivers Manager.  Does it say Nvidia display driver enabled? If not, I would recommend that you enable it, then restart for it to take effect.

Realtec AC97 is probably the most common audio device in PCs. I wonder why yours isn't working, it should be fully supported right out of the box.

well its not, i played a music file last night and got diddly squat,, and, my 5 series card will kick your cards butthole,, jk.. but i have drivers on my windows hard drive i just downloaded not 4 days ago.and they fully support the entire 5 series.

---

### Post by jake16424 on 2007-08-09
EVERYTHING i install un packs and thats it,, no updates, no installation. nothing, just do you want to extract these files? i click, sure why not.
and thats the end.. no exicutable, nothing that says "click me, i install what you just downloaded"

---

### Post by Rocket2DMn on 2007-08-09
> **kavon89 said:**
> He has a 5 series Nvidia card. From what I've seen on Nvidia's website, the oldest card supported by their drivers would be a 6100.

I'm no pro on nvidia cards as I was cursed with an ATI, but according to this, their drivers won't work.  You should use either the "nv" drivers which are open source, or even the "vesa" drivers.  You can set that in the configuration I gave you above, or manually by editing xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```
Replace
```
Driver	"nvidia"
``` under Section "Device" (if it exists) with
```
Driver "nv"
     or
Driver "vesa"
```

I suggest using "nv" if you can, but vesa if you have to.  Again, that configuration script will get your resolution to be OK, so post back specifics of your problem, otherwise we'll assume you have your video card working the way you want.

---

### Post by jake16424 on 2007-08-09
> **Rocket2DMn said:**
> So what's wrong with your video card?  Just bad resolution?  If so, use this configuration to get back on track:
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you questions about your hardware - use TAB to move between options and SPACEBAR to select/enable.  On the video drivers page, choose "nv" and on the resolutions page, enabled your monitor's max resolution and everything less.  Then restart the X-server (GUI) with CTRL+ALT+BACKSPACE.  Log back in and you can set your resolution with System->Preferences->Screen Resolution

If you really want to install the restricted drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

to update from the command line:
```
sudo apt-get update
sudo apt-get upgrade
```
The latest version of firefox is in the repositories, so you should get it if you don't yet have it.


just ran all of that,, then what do i do?

---

### Post by jake16424 on 2007-08-09
> **jake16424 said:**
> just ran all of that,, then what do i do?



just so everyone knows,, my audio drivers are still bum, they dont work.. 

Realtek 97 chipset..

---

### Post by jake16424 on 2007-08-09
i still cant get firefox to update to 2.5,,, im running 1.5, i download the files and nothing happens,, it just extracts, with no explination of what todo next,, i would appreciate it if someone could help me, out =) please? :popcorn:

---

### Post by AlexenderReez on 2007-08-09
> **jake16424 said:**
> i still cant get firefox to update to 2.5,,, im running 1.5, i download the files and nothing happens,, it just extracts, with no explination of what todo next,, i would appreciate it if someone could help me, out =) please? :popcorn:

google is your friend :)
> [www.justfuckinggoogleit.com](www.justfuckinggoogleit.com)

just a** joke**:lolflag:

firefox deb package ---->

> [http://gnomefreak.youmortals.com/mozilla-testing/](http://gnomefreak.youmortals.com/mozilla-testing/)

double click to install....give a try swiftfox and swiftweasel :)

---

### Post by GarlicFish on 2007-08-09
If you have firefox 1.5 and don't have the restricted drivers manager, then it sounds like you have an older version of Ubuntu than 7.04.

open a terminal and type in 

```
cat /etc/lsb-release
```

Post back what it says.

---

### Post by jake16424 on 2007-08-09
> **AlexenderReez said:**
> google is your friend :)


just a** joke**:lolflag:

firefox deb package ---->



double click to install....give a try swiftfox and swiftweasel :)

that goolge thing made me laugh, ima have to pull it on someone, =D thanks i needed that, whheee.. haha,,

---

### Post by klytu on 2007-08-09
> **jake16424 said:**
> i still cant get firefox to update to 2.5,,, im running 1.5, i download the files and nothing happens,, it just extracts, with no explination of what todo next,, i would appreciate it if someone could help me, out =) please? :popcorn:

Are you running Ubuntu Feisty or Ubuntu Dapper? Folks were giving you instructions for Feisty, but that has Firefox 2.0.0.6 after all updates ... Firefox 1.5 would be installed with Dapper.  Go to Applications>Accessories>Terminal copy and paste the following command and post the output:```
cat /etc/issue
```

**EDIT: ** Nevermind, I read a cross-post of yours lookiing for help with your Realtek drivers -  you are running Dapper, not Feisty as your user info shows. In Dapper, there is no Restricted Drivers Manager and Firefox won't update past 1.5 with Synaptic or any package managers, you would have to do it a different way.  You could try upgrading first to Edgy and then Feisty; or if you want to stick with Dapper - you can update Firefox by following [[COLOR="Red"]**_these instructions_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=330386").

---

### Post by jake16424 on 2007-08-09
jacob@jacob-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
jacob@jacob-desktop:~$

---

### Post by klytu on 2007-08-09
> **jake16424 said:**
> jacob@jacob-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
jacob@jacob-desktop:~$

See the response which I edited into my first post above.

---

### Post by GarlicFish on 2007-08-09
Yep! you are running an older version.

If you want all the new whizzy stuff, download the latest Stable release.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

This version makes life a lot easier in terms of drivers and ease of use.

Let us know if you need to back up anything from your existing Ubuntu install before you wipe it and load the new version.

---

### Post by jake16424 on 2007-08-09
jacob@jacob-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
jacob@jacob-desktop:~$

---

