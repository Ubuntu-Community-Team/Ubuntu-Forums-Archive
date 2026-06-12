---
title: "Screen resolution issue, editing xorg.conf"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-04-16
Hi all, 

For a few days now I've been trying to amend the screen resolution of my monitor, a 19" LG Flatron, running in conjunction with a ATI Raedon 7500 graphics card.

I attempted editing the Xorg.conf following instructions [here]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21") to no avail! Its been a great learning curve for a newbie, as I've managed to break my X 3 times and get it back up and running (with a little help from the forum :D ) however this problem is now starting to irritate :confused: 

My moniter can handle 1280 x 1024, however the highest which is offered automatically is 1024 x 768!

Within Xorg.conf the default depth under the "screen" section is 24, there I've attempted adding 1280 x 1024 as an extra resolution under 24, but upon restarting X the resolution simply isnt there, on one occasion after adding 1280 x 1024, the screen resolution gui offered 640 x 480 as a res :confused:  strange.

I've a feeling this is something to do with the Horizontal and vertical rates, which I also amended in xorg.conf to the ranges specified by the manufacturer, but not a sausage!

Perhaps a problem with my graphics card?

I also attempted installing xorg.edit in order to edit the screen res here, a few problems occured as posted over on the developers thread...

here are my experiences, has anyone any experience with this program? 

I downloaded the recent version xorg-edit_07.01.28-0ubuntu1_i386.deb and it installed without any complaints, I ran, entered my root password and amended my screen res (by entering a new mode) and attempted to save.

Upon save I receive the following:


```
can't create file '/etc/X11/xorg.conf_04/13/2007_10:16:54 PM' (error 2: No such file or directory)
```

Followed by

```
Error in file "/etc/X11/xorg.conf_04/13/2007_10:16:54 PM". Could not create backup file.
Function Stack:
GuiFrame::OnSave ->
GuiFrame::CreateBackup
```


running xorg-edit from my terminal works fine...however I receive the following:


```
(xorg-edit-bin:23006): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
```

any help, either with xorg.edit, or advice ref manually editing the xorg.conf would be appreciated!

Thanks a million..

Dale

---

### Post by justleen on 2007-04-16
im not sure how you are trying to achive the new resolution by reading the above..(never used xorg edit)
 
What you can do is the following.
Open a terminal, create backup of xorg.conf ```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```
open the config file ```
 sudo gedit /etc/X11/xorg.conf 
```  and scroll down to the bottom. It will have several lines of resolutions there which are available. (for each color depth a line)
find the depth you use, (probably 24) and add "1280x1024"  (including the "") in front of the highest res that is there already.
save the file, and restart X (CTRL-ALT-BKSPC)

---

### Post by TURNER on 2007-04-16
> It will have several lines of resolutions there which are available. (for each color depth a line)
find the depth you use, (probably 24) and add "1280x1024" (including the "") in front of the highest res that is there already.
save the file, and restart X (CTRL-ALT-BKSPC)[/B]

Hi...thanks for taking the time to reply, I've already tried this.....unfortunatly it didnt help, X restarted ok but the screen res wasn't available under sys-pref-screen res.

Strange but true :D

---

### Post by Ti_Uhl on 2007-04-16
Did you try using ctr+alt+keypad plus / keypad minus Because sometimes the gnome app doesn't display all available resolutions. 

Also, it could be that you need to look into your refresh rates, because that can also be a reason....

---

### Post by TURNER on 2007-04-16
> Did you try using ctr+alt+keypad plus / keypad minus Because sometimes the gnome app doesn't display all available resolutions. 

thats a new one on me, I'll certainly give it a try, should this key combo be pressed once the screen res GUI is open?


> Also, it could be that you need to look into your refresh rates, because that can also be a reason....

Yep, thats what I thought, I attempted creating and adding a modeline, via an online tool and also by the terminal, upon adiing this under the monitor section, something went wrong and X refused to start, backed up and now I am back to square one!

---

### Post by Ti_Uhl on 2007-04-16
> **TURNER said:**
> thats a new one on me, I'll certainly give it a try, should this key combo be pressed once the screen res GUI is open?

You can enter the key combo at any time once your X server is started. So just press it when X is running ;)
 
> **TURNER said:**
> 
Yep, thats what I thought, I attempted creating and adding a modeline, via an online tool and also by the terminal, upon adiing this under the monitor section, something went wrong and X refused to start, backed up and now I am back to square one!
 
Just make sure the modline is correct for your screen, as modline can possibly harm your screen, at least they used to be, don't know if it's still the case.
 
Then something else, when you added the resolution too the config, did you add it to all color depth's ? because in my expierience that can sometimes give errors aswell.

---

### Post by freebird54 on 2007-04-16
You might want to try running a new autodetect on your monitor - which should give you the resolutions you need.  I never got the changes to show up by just editing the xorg.conf directly either!  The command for doing so is 

```
sudo dpkg-reconfigure xserver-xorg
```

you already have backups, so I won't go into that here :)

This link gives an example walk-through running this, and could well handle things for you from there.  [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

The 'best' resolution for your monitor appears to be 1280x1024 @ 75Hz - from what I can find on the net - so enter that at the appropriate place!

Good luck!

---

### Post by TURNER on 2007-04-16
> just make sure the modline is correct for your screen, as modline can possibly harm your screen, at least they used to be, don't know if it's still the case

I did try with a new modeline, all seemed to go fine, however X didn't like it upon restart.


> You might want to try running a new autodetect on your monitor - which should give you the resolutions you need. I never got the changes to show up by just editing the xorg.conf directly either! The command for doing so is

I think I am going to give this another try, the first time I tried this I tried to get above myself and fiddle with the  advanced options, X didnt like that either, lucky I backed up first :D 

I'll let you know what the outcome is...

Thanks a lot!

---

