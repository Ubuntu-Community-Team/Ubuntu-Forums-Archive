---
title: "Remove Compiz - need help."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-05-14
Hi – I need some help today!

I have installed Compiz + the theme manager, and now I really want to remove it. Even if I have not add it to the session manager the effect are always on(even when rebooting), and its buggy(turns my screen dark from time to time and makes the system hang).

I have tried to remove it, but with no luck. Could someone pl tell me what I am doing wrong?

This is what I have done to remove it(I did use aptitude to install it); runed these two in the terminal(and didn't get any error message): 

sudo aptitude remove beryl beryl-manager emerald emerald-theme-manager	

sudo aptitude remove beryl emerald-themes beryl-manager

But the effect when closing and opening programs are still there, and my screen still gets dark from time to time(and it all hangs). 

If you need more info just ask. 

Thanks for any help

---

### Post by aeiah on 2007-05-14
what version of ubnutu?

---

### Post by _sAm_ on 2007-05-14
Feisty Fawn(sorry, should have said that in the first post!).

And now the hang/dark screen are happening more and more(!), aaa, and I had the perfect setup before I tried that beta compiz - stupid me!

---

### Post by aeiah on 2007-05-14
that has compiz installed by default no? ive not installed feisty, but i put it on my girlfriends, and there's an option (perhaps someone can direct you to it), somewhere in your settings menu that lets you turn the accelerated desktop on or off (which is essentially compiz). it should save the settings for each time you reboot as i disabled it to install beryl.

---

### Post by aeiah on 2007-05-14
ohh, and you're confusing compiz with beryl. beryl is a fork of compiz, so removing beryl wont affect your compiz effects. did you install a beta version of compiz or are you talking about the pre-installed version in feisty?

you should be able to search for compiz in synaptic, and right click the green boxed compiz packages and select 'remove' (or 'remove completley including settings' or something too), but you should make sure your desktop is set to run metacity else you may have errors when it cant find compiz. did you manage to deselect it in the settings menu?

---

### Post by _sAm_ on 2007-05-14
I can try again(sorry if I wrote badly above);

I have not turned on Compiz in the menu, but I have installed Beryl. Now I really want to remove Beryl(and there is nothing to be found of Beryl in Synaptic).

---

### Post by aeiah on 2007-05-14
how did you install it? via synaptic or some other method? if you followed a howto, what method did it use to start up beryl on boot?

---

### Post by _sAm_ on 2007-05-14
I followed the guide " How to install Beryl (Nvidia)" here is the linkl; this guide; [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz_.28Nvidia.29)

After that the boarders around the programs where gone so I went back to the same guide and added the suggestion to the  xorg.conf file, witch fixed it. 

(I also did the backup command from the guide).

So I used all the commands under &#8220;How to install Beryl (Nvidia)&#8221; to the DefaultDepth 24.

---

### Post by aeiah on 2007-05-14
ok. you'll have added both beryl-manager and emerald --replace to your sessions, and this is what triggers beryl to start on startup. go back to your System -> Preferences -> Sessions and remove them

you'll have made a backup of your xorg.conf file (called xorg.conf_backup). you should probably restore this. first make a copy of your current xorg.conf file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup2

```

and restore your prior one

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

```

then go into synaptic and remove the packages for beryl and emerald that show up

---

### Post by _sAm_ on 2007-05-14
.......................................

---

### Post by _sAm_ on 2007-05-14
When I browse the folder /etc/X11 with Nautilus I can see that my first backup file of the xorg list are there, and it is called; xorg.conf_backup2001-05-05
I want to restore it, so I press Ctril +Alt +F1 to get to a terminal(when I open a terminal within X it is blank and I cant type in it). In the terminal I type;

sudo cp /etc/X11/xorg.conf_backup2007-05-05 /etc/X11/xorg.conf 

Then it asks me for the password, but answer "Login incorrect" when I type it, evne though I am 100% sure its the right one? (no caps lock are on).

Looks like I am heading for a re-installation...

---

### Post by Big_Croc7 on 2007-05-14
If you press ctrl-alt-f1 you'll usually get a prompt like:
```
login>
```
enter your username, then password, then the command (sudo etc..) then it'll ask for your password again to run sudo. :-)

---

### Post by _sAm_ on 2007-05-14
Ooo, thanks! 

I hate beeing a noob...

---

