---
title: "Sporatic Frozen mouse"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by EasternBlocCouture on 2007-06-07
I am very new to this so.....   I have Ubuntu with xfce installed on an IBM Thinkpad with an old joystick mouse.   Often when I turn on the laptop the cursor will move to one of the four corners of the desktop and stay there.  I am unable to utilize the mouse although the cursor does move quickly from one corner to the next only to stick there.  I am able to manipulate around using key strokes but tabbing through 30 items to get where I need gets very old very quick.  I have been told that I may need a tweak in my X configuration, but honestly this is all greek to me.   help please

---

### Post by dannyboy79 on 2007-06-07
can you paste the output of this command please
cat /etc/X11/xorg.conf
we probably just need to make sure your mouse settings within your xorg.conf file are correct for the joystick mouse. also, is the mouse a serial, ps/2, or usb, or what? If you know the model number of the mouse I will need that also.

---

### Post by dannyboy79 on 2007-06-07
i have to go now but I have found this, do your best: [http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations)
if you can't figure out what to do, I may return to the forums later. It has to do with editing the file called xorg.conf and it's located within /etc/X11/
be sure to make a backup of that file before making any changes, this way, if you screw up, you can always overwrite the bad screwed up file, with the one that you backed up. the backup command is this from the command line
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original
```
the "cp" stands for copy and as you notice we gave it a new name, so all it did was copy the original file to the new name, they are both the same file but with different names. 

after the backup, you can change the /etc/X11/xorg.conf file all you want with whatever the guide at the link I provided, then to make the changes take affect to see if your mouse works, you would have to restart your xserver, that's done by hitting ctrl-alt-backspace all at once, then you'll be presented to login again.

then if all else fails and you made so many changes to it after you backed it up and you want to return it to it's original state, you would use this command

```
sudo mv /etc/X11/xorg.conf-original /etc/X11/xorg.conf
```
the "mv" is the move command, be careful with this because it will overwrite any other file with that same name, which in this case, we want that to happen.
then after that, you need to restart your xserver by hitting ctrl-alt-backspace all at once and you gui will restarrt which will use the new xorg.conf file. good luck!

---

### Post by EasternBlocCouture on 2007-06-25
I have discovered that my mouse is of the ps/2 variety.  Having located the file and copied the original, I do not know how to change the x axis mapping.  Do i need root privileges or do I use a sudo command of some sort.  any ideas?

---

### Post by dannyboy79 on 2007-06-26
if you're talking about editing the /etc/X11/xorg.conf, then yes, you need to use sudo. which will give you root privlages temporarily. as I said, first copy the xorg.conf so that if something goes wrong, you can just use your backup config file in place of the one that you accidentally messed up but I doubt you'll mess it up, just follow the guide and you should be fine.

---

