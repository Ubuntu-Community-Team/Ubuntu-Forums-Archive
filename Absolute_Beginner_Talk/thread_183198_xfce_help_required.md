---
title: "xfce help required"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-27
i've been using gnome and i now updated to xfce.
 i have following problems with xfce
1- i don't know where is cdrom menue
    in gnome when i insert cd it appears on desktop.however i used terminal to go to          
    cdrom.when i entered there i ls returned empty .then i ejected the disk and insert       
    another ,still ls returned empty

 2-in gnome when i enter home directory right click>properties it gives free space in  my partition and items in directory
    how to do this with xfce?????????????????

     the following  is my general problem with ubuntu

   1-how to write a cd?
   2-how to erase rewritable medium
   3-how to burn a cd

     do i need a burner or ubuntu can do it without burner       
     if i need burner tell me how can i install this by sudo apt-get 
  
    4- both gnome and xfce some times fail to pick up my sound card.they say no               
      sound card is installed

    plz tell me how to fix all of above mentioned problems
](*,)

---

### Post by aysiu on 2006-05-27
XFCE is a lighter-weight desktop and has fewer features than Gnome--this is why XFCE is also *faster* than Gnome.

You can use some of those features (automounting of CD-ROM and easy burning of CDs) in XFCE if you press Alt-F2 and type ```
nautilus
``` and then press Alt-F2 and type ```
gnome-volume-manager
``` Make sure you have in your XFCE settings to save your sessions on logout.

By the way, some of this stuff is fixed in XFCE for Dapper (the new release of Ubuntu that comes out on June 1, 2006).

---

### Post by adamkane on 2006-05-27
Using Nautilus will slow your XFCE system down. Don't use Nautilus with XFCE, if you are trying to speed up a slow system.

If your system becomes slow due to Nautilus, you will need to un-install Nautilus.

---

### Post by aysiu on 2006-05-27
[QUOTE=adamkane]Using Nautilus will slow your XFCE system down. Don't use Nautilus with XFCE, if you are trying to speed up a slow system.[/quote] Partially true... it depends how low-spec your system is. Nautilus will, in fact, slow down XFCE, but it won't make XFCE monstrously slow unless you're on 128 MB of RAM or less.

> 
If your system becomes slow due to Nautilus, you will need to un-install Nautilus. You don't need to uninstall Nautilus, you can just turn it off: ```
killall nautilus
```

---

### Post by Sutekh on 2006-05-27
If Nautilus *does* prove to be too much (should be ok) you could also try Thunar
```
sudo apt-get install thunar
``` 
If you need a burning app, you can use xfburn.  
```
sudo apt-get install xfburn
```This is only available in Dapper.  So you might want to seriously consider Dapper when it is released.

---

### Post by adamkane on 2006-05-27
Once you use Nautilus, your XFCE desktop will become a defacto Nautilus desktop, and Nautilus will be loaded each time you boot up. You will have XFCE and Gnome libraries loaded each time you boot, and this will slow your system.

If you use XFCE for speed, you need to make sure you only use apps which don't bog down your system (don't use Gnome or KDE apps). 

You have to modify your tastes/preferences to use XFCE to increase speed.

---

### Post by u04f061 on 2006-05-27
[QUOTE=Sutekh]If Nautilus *does* prove to be too much (should be ok) you could also try Thunar
```
sudo apt-get install thunar
``` 
If you need a burning app, you can use xfburn.  
```
sudo apt-get install xfburn
```This is only available in Dapper.  So you might want to seriously consider Dapper when it is released.[/QUOTE]

this is the output of u'r commands

E: Couldn't find package thunrar
ejaz@ejaz:~$  sudo apt-cache  search xfburn
ejaz@ejaz:~$  sudo apt-get install thunrar
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package thunrar
ejaz@ejaz:~$  sudo apt-get install xfburn
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xfburn
ejaz@ejaz:~$

---

### Post by adamkane on 2006-05-27
typo: thunar.

---

### Post by Sutekh on 2006-05-27
Bleh, sorry Thunar is not in any Ubuntu Breezy repos, only Dapper. Same story with xfburn.  If you are using Breezy, then you can't get them, sorry.

Nautilus can also be started so that it doesn't take over your desktop
```
nautilus --no-desktop
```

---

