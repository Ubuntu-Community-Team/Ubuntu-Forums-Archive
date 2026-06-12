---
title: "Installing real player"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-20
Hello,

How do I install real player in ubuntu ?

---

### Post by sad_iq on 2007-04-20
Try **sudo aptitude install realplay**!!!

---

### Post by Xarok on 2007-04-20
go to applications --> add+remove software and then search for real player
(at least that's how it works on my edgy machine)
If it's not there then search in the synaptic package manager.

---

### Post by Joseaa on 2007-04-20
"sudo aptitude install realplay"  gave this error :

"Couldn't find any package matching "realplay".  However, the following
packages contain "realplay" in their description:
 kmplayer-konq-plugins "

It is not listed under "Add/Remove software" and I don't know how to use synaptic packet manager. Someone please help !

---

### Post by sad_iq on 2007-04-20
Enable Universe and Multiverse repositorys from synaptic!!! 
 That should do the trick!!!
 Or go to [http://www.real.com/linux](http://www.real.com/linux) and download it manually then do :
 **sudo chmod +x RealPlayer10GOLD.bin** and 
 **sudo ./RealPlayer10GOLD.bin**

---

### Post by Xarok on 2007-04-20
> **sad_iq said:**
> Enable Universe and Multiverse repositorys from synaptic!!! 
 That should do the trick!!!
 Or go to [http://www.real.com/linux](http://www.real.com/linux) and download it manually then do :
 **sudo chmod +x RealPlayer10GOLD.bin** and 
 **sudo ./RealPlayer10GOLD.bin**

When I did that it placed that damn files on my desktop, I wouldn't suggest it.

---

### Post by sad_iq on 2007-04-20
To enable the repositories read here:
 [http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

---

### Post by sad_iq on 2007-04-20
> **Xarok said:**
> When I did that it placed that damn files on my desktop, I wouldn't suggest it.

 What files did it put in your desktop?

---

### Post by Joseaa on 2007-04-20
> **Xarok said:**
> When I did that it placed that damn files on my desktop, I wouldn't suggest it.

I guess, you must have selected desktop as installation directory. 

I tried the terminal way and it said :

"Copying RealPlayer files...configuring mozilla...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done."

Seems like the installation is complete but real player is not listed under Add/Remove programs and my browsers can't detect the plugin. Should I install the plugin separately for it to work in the browser?

---

### Post by Xarok on 2007-04-20
> **sad_iq said:**
> What files did it put in your desktop?

Basically it placed a folder with all the real player files in it.

Yes, I do remember something about it setting the directory to the desktop.

oh well, it happened and it's done.  At least it works just fine. 

Just seems like a dumb default location for an installation.

---

### Post by Joseaa on 2007-04-20
I still can't get the real player plugin to work with my browser. Any ideas ?

---

### Post by sad_iq on 2007-04-20
Real Play should be dispayed under multimedia (or whatever)...I don't use gnome...so don't remember where exactly it should be...if you can't find it restart gnome and look again...and do enable those repositories as you'll need them sooner or later!!!

---

### Post by Perfect Storm on 2007-04-20
Suggestion: Use mplayer or similar to play the realplayer files. Realplayer is not great.

---

### Post by MissG on 2007-04-20
> **Xarok said:**
> When I did that it placed that damn files on my desktop, I wouldn't suggest it.
Couldn't you just copy and paste the file into your home directory and go from there? (or navigate to Desktop? You can specify where to install once you start). To navigate:
# cd /home/yourhomedir/Destop

---

### Post by Joseaa on 2007-04-20
mplayer might be good but I was trying to get real player installed in the system. 

I was able to open the player directly from the installation location but the shortcut is not listed under add/remove programs or anywhere.  Moreover, I was trying to get the plug-ins to work in my browser but it's just not working even after installing the player.

Please help !

---

### Post by Perfect Storm on 2007-04-20
I have uploade a .deb file for it: [http://www.mediafire.com/?bm12yymjqmx](http://www.mediafire.com/?bm12yymjqmx)
You might want to uninstall the previous first.

---

### Post by MissG on 2007-04-20
> **Joseaa said:**
> I was trying to get the plug-ins to work in my browser but it's just not working even after installing the player.

Please help !
I don't know if this is your problem too, but here's how I got around an audio content problem:

click on RealPlayer audio content link (in my case a music link from Amazon)
ubuntu's download monitor appears, downloading "hurl.exe"
realplayer appears (with video box), no apparent functionality (buttons gray)
click realplayer file drop down menu, choose hurl.exe from list
realplayer video window disappears, leaving audio controls with functional buttons
content plays
sometimes clicking on more links brings up the functional player immediately

sort of annoying but it works well enough for me

---

### Post by Joseaa on 2007-04-20
Artificial Intelligence, thanks. It would be particularly useful if you could tell what to do with this file also.

Moreover, how to uninstall the program. It is not listed under add/remove programs.

---

### Post by Perfect Storm on 2007-04-20
Try with first;
```
whereis realplayer
locate realplayer
```

post the output.

The .deb I posted, just doubleclick to installed it.

---

### Post by Joseaa on 2007-04-20
Here is the output : 

joseaa@joseaa-Linux:~$ whereis realplayer
realplayer:
joseaa@joseaa-Linux:~$ locate realplayer
joseaa@joseaa-Linux:~$

---

### Post by Perfect Storm on 2007-04-20
okay, looks like it isn't installed. Then you can install the package I posted.

---

