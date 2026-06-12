---
title: "Mixed ! Gnome and Kde"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by Dutch on 2005-08-10
Hi,

I'm using Ububtu 5.04
said:  apt-get install kubuntu-desktop

said no when installing
later said again apt-get install kubuntu-desktop
did install the Kubuntu program
Started de PC again and now I have Ubuntu with Kde mixed !

How do I get rid of KDE and how do I install KDE so that I can choose from these ?

---

### Post by KingBahamut on 2005-08-10
apt-get remove kubuntu-desktop.

---

### Post by Dutch on 2005-08-10
[QUOTE=KingBahamut]apt-get remove kubuntu-desktop.[/QUOTE]

said :  apt-get remove kubuntu-desktop
start PC up again.

Nothing changed !
Tryed it again got message that Kubuntu was not installed !
Nice !(not)

Now what ?

The aptget file is still in var/cache/apt/archives  but with a LOCK file in it.

---

### Post by varunus on 2005-08-10
I'm confused as to what you want to do.  Could you clarify?

If you want to be able to pick from GNOME and KDE, just open a terminal, do "apt-get install kubuntu-desktop", say YES, and then at your login screen, there will be a "sessions" button.  You can pick GNOME or KDE.

---

### Post by Dutch on 2005-08-10
[QUOTE=varunus]I'm confused as to what you want to do.  Could you clarify?

If you want to be able to pick from GNOME and KDE, just open a terminal, do "apt-get install kubuntu-desktop", say YES, and then at your login screen, there will be a "sessions" button.  You can pick GNOME or KDE.[/QUOTE]

Oke, but when I select Ubuntu you see both the programs from and KDE and GNOME !
Is that normal ?

When you're in KDE  you must look to pik the KDA Utilities and when you choose Gnome you must see that you find the Ubuntu things.
Is that handy ? is it ment this way ?

---

### Post by varunus on 2005-08-10
Yes, this is normal.  Because KDE and GNOME are interoperable, you can run KDE programs inside GNOME and GNOME programs inside KDE.  The menu systems will show *all* programs, not just each for each desktop envrionment.

So yes, you do have to make sure you click the right utilities...This is why most people just pick one desktop environment and use it, and only get programs they need from the other if they need them.

Unfortunately, its harder to uninstall KDE or GNOME than you think; just installing kubuntu-desktop or ubuntu-desktop won't do anything.  You'll need to hunt down all of the packages in Synaptic and uninstall them...or reinstall.

---

### Post by Dutch on 2005-08-10
[QUOTE=varunus]Yes, this is normal.  Because KDE and GNOME are interoperable, you can run KDE programs inside GNOME and GNOME programs inside KDE.  The menu systems will show *all* programs, not just each for each desktop envrionment.

So yes, you do have to make sure you click the right utilities...This is why most people just pick one desktop environment and use it, and only get programs they need from the other if they need them.

Unfortunately, its harder to uninstall KDE or GNOME than you think; just installing kubuntu-desktop or ubuntu-desktop won't do anything.  You'll need to hunt down all of the packages in Synaptic and uninstall them...or reinstall.[/QUOTE]

Oke get it.
Oke then and if I uninstall KDE with synaptic, is the downloaded file (oke apt-get) stil there ?
Then can I make u new user for KDE ?I meant make a user where only KDE runs ?
User 1 Gnome
User 2 Kde 

How about that ?

---

### Post by varunus on 2005-08-10
Unfortunately, no; if you uninstall KDE, KDE is gone.  Your users that you make must make use of the installed desktop environments, and all users will have the problem of multiple GNOME and KDE utilities in the menus.

If you can, just pick one environment, or just remember which is for which in your menus...

---

### Post by Dutch on 2005-08-10
[QUOTE=varunus]Unfortunately, no; if you uninstall KDE, KDE is gone.  Your users that you make must make use of the installed desktop environments, and all users will have the problem of multiple GNOME and KDE utilities in the menus.

If you can, just pick one environment, or just remember which is for which in your menus...[/QUOTE]

Come on, you can't be serieusly  [-X 
This is LINUX  :-P 

Stop making jokes, and tel me how  \\:D/

---

### Post by bored2k on 2005-08-10
[QUOTE=Dutch]Come on, you can't be serieusly  [-X 
This is LINUX  :-P 

Stop making jokes, and tel me how  \\:D/[/QUOTE]
 Remove KDE? Just get rid of kdelibs through Synaptic. That'll hurt KDE in the stomach. For better cleansing you could use deborphan. [http://www.ubuntuforums.org/showthread.php?t=53176&highlight=deborphan+synaptic](http://www.ubuntuforums.org/showthread.php?t=53176&highlight=deborphan+synaptic)

---

### Post by manicka on 2005-08-10
[QUOTE=Dutch]Oke get it.
Oke then and if I uninstall KDE with synaptic, is the downloaded file (oke apt-get) stil there ?
Then can I make u new user for KDE ?I meant make a user where only KDE runs ?
User 1 Gnome
User 2 Kde 

How about that ?[/QUOTE]
 What you could do is install both kde and gnome and then have user1 login for his/her session in gnome as default and user2 login to kde as his/herdefault.

Once in the environment you could use smeg in gnome or the menu editor in kde, to remove the gnome or kde apps that you don't want from the menus.

---

### Post by poofyhairguy on 2005-08-10
[QUOTE=manicka]
Once in the environment you could use smeg in gnome or the menu editor in kde, to remove the gnome or kde apps that you don't want from the menus.[/QUOTE]

Thats the best solution, its what I use.

---

### Post by Dutch on 2005-08-11
[QUOTE=bored2k]Remove KDE? Just get rid of kdelibs through Synaptic. That'll hurt KDE in the stomach. For better cleansing you could use deborphan. [http://www.ubuntuforums.org/showthread.php?t=53176&highlight=deborphan+synaptic](http://www.ubuntuforums.org/showthread.php?t=53176&highlight=deborphan+synaptic)[/QUOTE]


Nop, I meant let Ubuntu and Kubuntu.
But ! I don't want them mixed.
So user1 Ubuntu and user2 Kubuntu.

How ?

---

### Post by bored2k on 2005-08-11
[QUOTE=Dutch]Nop, I meant let Ubuntu and Kubuntu.
But ! I don't want them mixed.
So user1 Ubuntu and user2 Kubuntu.

How ?[/QUOTE]
 The thing is that they _don't_ get mixed. You simply get KDE applications on the Gnome menu and viceversa. You can select wich Desktop Environment you want on your Login Manager (GDM, KDM or whatever).

---

### Post by Dutch on 2005-08-11
[QUOTE=bored2k]The thing is that they _don't_ get mixed. You simply get KDE applications on the Gnome menu and viceversa. You can select wich Desktop Environment you want on your Login Manager (GDM, KDM or whatever).[/QUOTE]

Oke , right !

2nd.
I've updated to Ubuntu 686.
Can I remove savely al the 363 things ? with Synaptic ?(to save room on the HD)

---

### Post by Knome_fan on 2005-08-11
So all you want is to get of the KDE apps in the Gnome menu if I understand you correctly?

Open up a terminal.
Then go to /usr/share/applications/kde. (That is cd /usr/share/applications/kde)
Now run the following command.
sudo  for i in *; do echo "OnlyShowIn=KDE;" >> $i; done

That should be it.
What it does is add to the .desktop files of the KDE programs the line OnlyShowIn=KDE, which, you guessed it, causes these programs only to be shown in KDE.

Hope this helps.

---

### Post by Dutch on 2005-08-11
Uhmm that looks good.And the other way a round ?

---

### Post by Knome_fan on 2005-08-11
[QUOTE=Dutch]Uhmm that looks good.And the other way a round ?[/QUOTE]
In KDE it's probably the easiest solution to use the build in menu editor. If I remember correctly, it only removes the entries in KDE, but they will still be there in Gnome.

The problem with Smeg (the menu editor for Gnome) on the other hand is that it is totally removing the entries, even in KDE.

---

### Post by bored2k on 2005-08-11
[QUOTE=Dutch]Oke , right !

2nd.
I've updated to Ubuntu 686.
Can I remove savely al the 363 things ? with Synaptic ?(to save room on the HD)[/QUOTE]
 Yes you can remove 386 (after you booted with 686 that is ;)).

---

### Post by manicka on 2005-08-11
[QUOTE=Knome_fan]
The problem with Smeg (the menu editor for Gnome) on the other hand is that it is totally removing the entries, even in KDE.[/QUOTE]

That wouldn't effect user 1 who's just logging in with gnome and user 2 who's just logging in to kde. Changes are made on a user basis, not system wide.

---

### Post by Dutch on 2005-08-11
[QUOTE=bored2k]Yes you can remove 386 (after you booted with 686 that is ;)).[/QUOTE]

Oke.
like this ?
sudo apt-get uninstall linux-368       ?

---

### Post by bored2k on 2005-08-11
[QUOTE=Dutch]Oke.
like this ?
sudo apt-get uninstall linux-368       ?[/QUOTE]
 a) sudo apt-get remove linux-386
or
b) System - Administration - Synaptic, then use the good old "Seek and Destroy" method ;) (it's safe to remove config files).

---

### Post by Dutch on 2005-08-11
[QUOTE=bored2k]a) sudo apt-get remove linux-386
or
b) System - Administration - Synaptic, then use the good old "Seek and Destroy" method ;) (it's safe to remove config files).[/QUOTE]

Uhmm with a) they said I saved 49Kb 
Why bother.
Thanks anyhow.

---

### Post by bored2k on 2005-08-11
[QUOTE=Dutch]Uhmm with a) they said I saved 49Kb 
Why bother.
Thanks anyhow.[/QUOTE]
 Actually, search for 386 and remove all the "linux-image" and "linux-kernel" 386 stuff, they'll save you about 80megs.

---

### Post by Dutch on 2005-08-11
[QUOTE=bored2k]Actually, search for 386 and remove all the "linux-image" and "linux-kernel" 386 stuff, they'll save you about 80megs.[/QUOTE]

When I'm looking in Synaptic on version I get 1 file
Host AP driver for Intersil Prism2/2.5/3 (kernel 2.4.26-1-386)

That's all.  ](*,)

---

