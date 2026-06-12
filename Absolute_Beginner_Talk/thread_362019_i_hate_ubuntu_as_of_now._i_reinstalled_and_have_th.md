---
title: "i hate ubuntu as of now. i reinstalled and have the same prob"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-15
i reinstalled the system , i formatted the windows partition and did a clean install, no dual boot.
after i installed it , i did the following:
got Easyubuntu and ran it to have all my codecs
mounted the other ntfs formatted hard disk
created a new panel on the right with trash; connection monitor and clock and added transparency to all the panels using the properties dialog
added the Deskbar triggered by ALT+F3 on the top taskbar
installed Adobe Reader and Azureus using Add/remove applications
installed WINE using Add/remove
did a restart and it got into the desktop and just after the sound stop playing it restarted to the login screen and i logged in again..and the same thing happened.
not even failsafe gnome works.
only failsafe terminal in which i am now.:mad:
help

---

### Post by frodon on 2007-02-15
Maybe an easyubuntu bug, you should try to re-install and not use easyubuntu, all for the codecs is there :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I think you have a gnome session error but without error message it's nearly impossible to know what is the problem, so try to search and provide some informations or error message. Or re-install and don't use easyubuntu.

---

### Post by panti19 on 2007-02-15
ok the error i get in failsafe gnome, wich seems to work now is:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by frodon on 2007-02-15
This should help you :
[http://ubuntuforums.org/showthread.php?t=351739](http://ubuntuforums.org/showthread.php?t=351739)
[http://ubuntuforums.org/showthread.php?t=335886](http://ubuntuforums.org/showthread.php?t=335886)

---

### Post by panti19 on 2007-02-15
thanks for the replies, but none of those solutions worked for me:(

---

### Post by panti19 on 2007-02-15
i am free today, so i can easily reinstall, but i just want to know for sure what caused the problem.
be it easyubuntu or any other app..
help me identify the problem

---

### Post by apjone on 2007-02-15
create a new users and try to login as them. see if you get the same problem

---

### Post by frodon on 2007-02-15
Yep apjone has a good suggestion try that and we will now if it's a theme, icon or user configuration problem.

---

### Post by panti19 on 2007-02-15
i've created a new   "Desktop User" (not administrator) and it seems to be working perfectly.

---

### Post by frodon on 2007-02-15
Ok so i think it's just a theme, icon problem or something like that. Maybe easyubuntu installed you some new themes or icon and it don't work really well.
So you can try to modify the setting of the other user or more easy give full rights to this user and use it as first user.

---

### Post by panti19 on 2007-02-15
thanks, so i'll just have to be careful not to change the theme? i deleted my old user and am now using the new one :)

---

### Post by apjone on 2007-02-15
make a back up of your home directory and remove the .gnome files . Then login and they should get recreated and your problem may be resolved. 

WARNING: I have tried this and it worked for me with a similar problem, It may NOT work for you. Ensure you have a GOOD BACKUP of anything you need to keep

---

### Post by panti19 on 2007-02-15
ok now i can log in normally ,but only on the second try :confused: 
i mean , when i first log in when i start the computer, it restarts once it finishes playing the start sound (not the login one, the long one) it then takes me to the login where i login again and it works.

---

### Post by tchoklat on 2007-02-22
I have the same problem and did the same solution. I now have a second user that works fine - though I have lost all my settings etc for the original user, ME. What can I do? I need to logon and use the original user's settings but I am unable to start Gnome with it

---

### Post by tchoklat on 2007-02-22
thanks Apjone.

I found that I had a .gnome and a .gnome2 folder. I deleted the .gnome and renamed the .gnome2 to .gnome and restarted.

All works great. I wonder where the .gnome2 folder came from though!


Tony

---

### Post by paydaydaddy on 2007-02-22
Maybe not related to your problem, but worth checking if you haven't aleady. Ubuntu comes with a pretty cool memory test. I loaded Ubuntu into one of my computers and things worked well for several days and then would get buggy. I reloaded several times and then after a few days things would start going south. I finally decided to run the memory test and found a bad strip of RAM. I pulled out that strip of RAM and ,Walla, no problems since. Like I said, may not be your problem, but may be worth checking out.

---

### Post by cantormath on 2007-02-22
I would have used Automatix2 instead of easyubuntu.  Just my opinion.

---

### Post by rapolas on 2007-04-21
It's a problem with gnome panels transparency, if you make your gnome panel transparent, the problem occurs, it doesn't matter if you make it transparent or put a transparent background, if you are not making gnome panel transparent, everything works fine.. I don't know how to fix this, but at least I found a reason for problem.

p.s I would appreciate if somebody could suggest any solutions to this problem;)

---

### Post by brandon079 on 2007-10-17
> **cantormath said:**
> I would have used Automatix2 instead of easyubuntu.  Just my opinion. I have heard bad things about automatix. It's pretty useless now anyways with synaptic package manager and other Ubuntu features. Everything will go well until you try to update your system and everything goes to hell. If you need any program automatix might have just google "Installing [appname] on Ubuntu" and you will find plenty of answers. 


Not related:  didn't know I could have an transparent (translucent) panel background. I thought it was either solid color with alpha blending or background and no alpha blending. And here I've been tricking people into using Ubuntu with this half *** Vista panel.

---

