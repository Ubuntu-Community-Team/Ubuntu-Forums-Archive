---
title: "Syncing an iPod Touch, iPhone, iPad, etc."
date: 2011-03-31
forum: Apple Hardware Users
---

### Post by newblueboy on 2011-03-31
I know this is a dumb question, but is there a program OTHER than using WINE and iTunes that I can use to sync my iPod Touch with my Ubuntu 10.10 machine? I still have Vista as a Dual Boot, but I just HATE using it (I'm sure you know).

Thanks!

---

### Post by snafu006 on 2011-03-31
> **newblueboy said:**
> I know this is a dumb question, but is there a program OTHER than using WINE and iTunes that I can use to sync my iPod Touch with my Ubuntu 10.10 machine? I still have Vista as a Dual Boot, but I just HATE using it (I'm sure you know).

Thanks!

Yes its called banshee media player. and you might need the PPA aswell

---

### Post by snafu006 on 2011-03-31
First you must have tethering enabled in the iPhone, either via your carrier, or via a 3rd party app such as MyWi.
 Simply add the corresponding PPA repository, either via your prefered GUI or with the command:[INDENT]sudo apt-add-repository ppa:pmcenery/ppa
[/INDENT]The update your sources with your GUI or with:[INDENT]sudo apt-get update
[/INDENT]And the install ipheth-utils via Syaptic, or with the command:[INDENT]sudo apt-get install ipheth-utils
[/INDENT]Ready, next time you connect your iPhone, Ubuntu Lucid will automatically connect.

---

### Post by Georgia boy on 2011-05-05
Hi. Won an iPad from Dummies.com. The attachment shows what I get when connecting. I use Lucid.The Dbus error isn't constant but does come up at times. Also why do I keep getting this iPod initialization screen popping up? I followed the directions in this link for setting up to include getting the latest of librimobibledrives.  [http://www.linuxuser.co.uk/tutorials/how-to-sync-your-ipad-with-linux/](http://www.linuxuser.co.uk/tutorials/how-to-sync-your-ipad-with-linux/)

The screenshots are what I get. When I go into the iPad on the pc I can see music and pictures that I put into the photos. But when I unmount and turn the iPad back on guess what's not on the iPad. So, what am I doing wrong or is there something else that should be done? For now I'm having to use Drop Box to put pictures on the iPad photo folder and listen to the music from the Drop Box favorites folder. So, how do I go about actually getting this thing to work with Lucid? From what I had read Lucid and on were supposed to be working out of the box with the iPad. I don't have the latest version on the iPad. I'm using the 4.2. 
It's not jail broken. At least not yet. ;)  Want to get used to it first. Has nice sound when playing the music. Shows good quality when looking at the pictures. Just the idea of wanting to get things from my folders on the pc over to the iPad.

Thanks

GB

---

### Post by Hatsune Miku on 2011-05-05
**_Do this im awesome :u_**

1. Just use Virtual box to make a VM of Windows 
2. Install iTunes on Windows
3. Mount the "i" device on the VM
4. sync in iTunes

Enjoy, Miku.

---

### Post by Georgia boy on 2011-05-06
> **Hatsune Miku said:**
> **_Do this im awesome :u_**

1. Just use Virtual box to make a VM of Windows 
2. Install iTunes on Windows
3. Mount the "i" device on the VM
4. sync in iTunes

Enjoy, Miku.

Only Windows I have is the 18 cd's os XP I made when I got my computer. Didn't come with a Windows CD. Don't know what the product key is since I didn't have a book come with it. I do have a product key on the side of the computer. Will I have to install all of those CD's or is there  a way to legally get a free Windows iso? 

Thanks
GB

---

### Post by Hatsune Miku on 2011-06-07
> **Georgia boy said:**
> Only Windows I have is the 18 cd's os XP I made when I got my computer. Didn't come with a Windows CD. Don't know what the product key is since I didn't have a book come with it. I do have a product key on the side of the computer. Will I have to install all of those CD's or is there  a way to legally get a free Windows iso? 

Thanks
GB

 Call the computer manufacturer about it, they should by law give you a cd key and CD of XP.

---

