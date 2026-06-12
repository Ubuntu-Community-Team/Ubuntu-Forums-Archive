---
title: "Allrighhhht ! ! ! !"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by HiSpeed15 on 2006-02-07
:D  YES I did it LOL I got Ububtu loaded here relatively painlessly...after two HD 's that were to darn small,I scooped one of my sons out of his (er my old) pc its only about 12 G but it works. Dont think he'll even notice it gone with the 2.1 Gb one I slapped in there.No worries, he only plays a bit on MSN anyhow and once I learn how to use this better His will be on Ubuntu as well. 

Yess so anyhow...First full install on an old Pentium box 366Mhz seems to be ok  a little draggy but maybe I can tweak it abit. Any suggestions? I'm not worried about burning this as its put together with a bunch of spare stuff I had laying around. These boards helped LOTS Thanks everyone for posting Q and A  
                                                                                               Best Rgds    Larry

---

### Post by byen on 2006-02-07
For that processor speed....I strongly suggest using the  XFCE desktop environment. You might also want to try Fluxbox, IceWM etc.
To install XFCE
```
sudo apt-get install xubuntu-desktop
```
To Install Fluxbox
```
sudo apt-get install fluxbox
```
To install ICewm
```
sudo apt-get install icewm menu
```

these 3 are famous for bringing old, slow computers back to life...so I suggest you try them. Goodluck and Welcome to Ubuntu!

EDIT: command corrected (what was I thinking). thanks SavageBeginner

---

### Post by HiSpeed15 on 2006-02-07
ok i used those commands to get fluxbox but cant really tell if its working

---

### Post by taurus on 2006-02-07
If you reboot your machine, wait for the system to finish at which it will present you a login screen.  If you click on the Sessions, you will see your new window managers like Xfce, fluxbox, etc. that you have installed.  Pick the one you want to try out and log in...

---

### Post by SavageBeginner on 2006-02-07
[QUOTE=byen]For that processor speed....I strongly suggest using the  XFCE desktop environment. You might also want to try Fluxbox, IceWM etc.
To install XFCE
```
sudo apt-get remove xubuntu-desktop
```
To Install Fluxbox
```
sudo apt-get install fluxbox
```
To install ICewm
```
sudo apt-get install icewm menu
```

these 3 are famous for bringing old, slow computers back to life...so I suggest you try them. Goodluck and Welcome to Ubuntu![/QUOTE]I think you mean```
sudo apt-get install xubuntu-desktop
```

---

### Post by HiSpeed15 on 2006-02-07
OK i'll give that a shot. I'm guessing that seeing as I did the 
sudo apt-get remove ubuntu  command Now I need to reverse that or leave it?
I'll be back after this old beast reboots

---

### Post by taurus on 2006-02-07
If you happened to remove it from your system, then you need to re-install it again or you can't use it.

---

### Post by AmboyGuy on 2006-02-07
It's been about 10 - 15 minutes since he left. Probably booted into a blank fluxbox WM and can't figure it out. Bet he's back to Gnome in a hurry. (wonder if he knows about Ctrl-Alt-Backspace)
I use XFCE (Xubuntu) works great on my old system.

---

### Post by byen on 2006-02-07
[QUOTE=SavageBeginner]I think you mean```
sudo apt-get install xubuntu-desktop
```[/QUOTE]
I apologize for the stupid mistake. It was from a similar post and I just pasted the codes here.. I should have checked it again. Hope no one broke anything here. Sorry guys!

---

### Post by HiSpeed15 on 2006-02-07
well yes your right LOL Back in Gnome and no I didnt know about ctrl alt backspace
I'll get the hang of this eventually.

When I click on sessions it didnt show those other ones tho

---

### Post by HiSpeed15 on 2006-02-07
Nope still doesnt show them. But the domestic chores call here, I'll check back later tonite or in the morning. Thanks for the help guys.

---

### Post by AmboyGuy on 2006-02-08
I use the Xubuntu version (Light weight, fast, maybe not the fastest, Imports menus, and fairly easy to figure out) and here's the way I did it.

In Gnome :
** System > Administration > Synaptic Package Manager **
click settings > repositories and edit / add multiverse & universe to your repo's
exit settings.
click search and enter 'xubuntu' in the search field - change the search to 'name' and click search.
right click on 'Xubuntu-desktop' and 'Mark for installation' (and all the other apps it needs also)
click Apply
Get a cup of coffee, do the laundry, wash the dishes, clean the garage etc. if you're on dial-up.

When it's finished reboot your system ( ** System > Log out > Restart ** )
I'm not sure this is needed but you do get a 'known good' starting point.

When the login screen appears click **Sessions** (just under the login area)
Select XFCE and finish your login.

You should now be in a new GUI & you can use the panel or right click on the screen and get a menu.

Good luck, any problems post back.

PS: My system is a 450Mhz P3, 128 MB Ram, 6GB HD, Diamond Viper 550 (RIVA TNT) 16MB video. XFCE gave this system a new lease on life. (and I still have Gnome (Ctrl-Alt-Backspace) to fall back on when I screw up)

---

### Post by HiSpeed15 on 2006-02-09
Hello again,I'm back with a whole new approach and a different   set of issues LOL I decided not to use that old box and installed Ubuntu onto my XP machine its working pretty good as far as I can and the grub loader comes up at boot to ask which os to boot OK Thats all fine,as far as I can tell  both XP and Ubuntu boot like they are supposed to. this guide > [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
is pretty good for configuring ntfs and ubuntu. OK anyways my "issue" is this How do I find out what my partions look like and how much is used ?

PS  
     Thanks to everyone for the responses I appreciate the help.I am going to get that other old one working at some point  so i'll keep an eye on this thread. So Thanks Lots eh.!

---

