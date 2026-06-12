---
title: "How do i get Oblivion to work with Wine?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-04-11
No worries, I know im an ideot and should be able to figure this out but ive read the previous threads and the walkthrough (which looks really good if only I could understand it!) and I cant get Oblivion working on my machine.  

Ive downloaded and installed wine.  I dont know which version cos I cant figure out how to tell but its there and every now and again it pops up and does something.  So, I poped my Oblivion DVD into my machine, it picked it up, installed it, added a shortcut (can you call them that on Ubuntu??? Sorry if ive offended anyone by using windows lingo....) to my desktop and I thought I was on to a winner.  I ran the shortcut and was rubbing my hands when I got the normal Oblivion menu, with sound!  Great I thought!!! then I clicked play and my system reverted back to the desktop as if to say '*dont be silly*!'  

So, I know I should really be able to figure this out but Oblivion is the only reason I still have an XP partition and if I can get that working then I can be rid of windows forever!!!!  so.....can anyone baby walk an ideot like me through this?

---

### Post by ComplexNumber on 2007-04-11
firstly, you are absolutely not an idiot. everyone has to start somewhere :).

i found [this]("http://ubuntuforums.org/showthread.php?t=349764") link. it may help. post back if it helps or not.

btw i renamed your thread to something more appropriate  ;)

---

### Post by MikeSz on 2007-04-11
Hello - yes, thanks for that, I have read through that and to be honest, it lost me after it started talking about extracting files from the DVD (pretty much went off the rails there...) so I decided to have a play and see if I could strike it lucky and get the thing working just by "winging it".  

Im sure its something fairly simple so im looking round the threads and the online guides but if you have any suggestions then that would be great, like I said, this is the only reason I have an XP partition (its the only game I play really) so if I can get this working I will be well chuffed!

---

### Post by Maestro23 on 2007-04-11
I google this, don't know if you have seen it already.

[http://mongooseichiban.blogspot.com/2007/01/oblivion-under-wine.html](http://mongooseichiban.blogspot.com/2007/01/oblivion-under-wine.html)

Just find you a guide and jump in and get your hands dirty with it.:D 

Good luck.

---

### Post by ComplexNumber on 2007-04-11
ok. i've never used wine before, so, unfortunately, i can't  go through the procedure in that link to guide you through it.

---

### Post by MikeSz on 2007-04-11
Thanks guys!  The wiki link is pretty similar to the one ive found on here in terms of walkthrough, looks like ive jumped the gun a bit by just trying to install Oblivion from the DVD :( 

Il have to have a good read through as it looks as if il have to start from scratch with it...

---

### Post by MikeSz on 2007-04-11
Ok, bit of an update....

Ive run through the walkthrough (as much as poss anyway) and have configured wine, ive made the fake registry entry sort of thing and now when I start oblivion, wine opens in the background and I get the menu, the only difference is now I dont have any sound and it still drops to a desktop when I click on play.  i have got to the bit on the walkthrough where it says :  (and I havent a clue what to do now!)

Playing!

Now you can finally play the game. Remember you must have the disc or the iso for Oblivion mounted and setup as CDROM device in Wine to play. Disabling all the debug spew improves performance. The following shell script can be used to start the game. Open up a text editor and save the text below to Oblivion.sh. Change the OBLIVION_DIR to be your install directory, and set the permissions of execute bit on the script. You can do this by right clicking on the file, click the Permissions tab, and checking the Execute box. Also the command 'chmod +x Oblivion.sh' in a terminal works as well.

#!/bin/sh
# This script disables all the text output for Wine
# debugging for improved performace.
export WINEDEBUG=fixme-all,err-all,warn-all,trace-all
OBLIVION_DIR=/opt/games/Windows/Oblivion
cd ${OBLIVION_DIR}
wine OblivionLauncher.exe

You can either run the shell script from a terminal or make a menu entry.

# Command for use in terminal
sh Oblivion.sh

---

### Post by MikeSz on 2007-04-12
bump...

---

### Post by MikeSz on 2007-04-12
another bump...

---

### Post by Mongoose on 2007-04-17
Did you follow the recommended settings, and disable features known to cause issues?

---

### Post by MikeSz on 2007-04-17
Im pretty sure I did, I followed the walkthrough as much as I could - the only thing I havent done is extract that dll file from the disc as that bit sort of lost me a bit :(   All the other settings are as per the walkthrough though

---

### Post by MikeSz on 2007-05-01
If anyone can help im still having this problem - ive now installed fiesty from scratch on a new hard disk and im only running a geforce fx 5600 now with 256 meg.  (had a psu blow-out over the weekend which has killed a couple of components!)  

Ive followed the walkthrough, installed wine 0.9.33 and all went pretty well (apart from the bit where you have to edit the registry - I didnt have a Direct3D key so I created one and put all the strings in).   Same problem as before, I have a desktop icon, it loads the menu - which I can use, but the moment I click on play it drops back to the desktop.  I have tried removing the intro values in the .ini file as well as suggested to one poster in the walktrhough thread started by Mongoose.  Can anyone tell me why this problem is happening?  

Any help much appreciated!

---

### Post by lou1998 on 2007-07-02
Which .ini file are you editing?  The one in the Oblivion directory named Oblivion_default.ini is not the correct file.  Make sure you go to the My Games/Oblivion directory and edit the Oblivion.ini file there.

I was able to get the game working well after I followed all the instructions in the wiki and updated my Nvidia driver.

However, I can't save games.  They just don't appear on the list or in the saves directory.

---

