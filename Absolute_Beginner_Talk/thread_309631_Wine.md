---
title: "Wine"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2006-11-29
I installed wine using ubuntuguide.org. The only problem is that i can't locate where its installed. I even tried doing:
 $ /usr/local/bin/winecfgbash: $: command not found
as suggested by the Guide provided at winehq. and then a need a comprehensive and short guide on installing softwares on wine.

---

### Post by Darrious on 2006-11-29
Why exactly do you need to find out where you installed it.:confused:

I would try this

```
cd /home/USERNAME/.wine
```

---

### Post by shoaibi on 2006-11-29
/home/shoaibi/.wine
bash: cd: /home/shoaibi/.wine: No such file or directory

---

### Post by Darrious on 2006-11-29
Okay. 

Try typing this command first.

```
sudo apt-get remove wine
```

then this

```
sudo apt-get install wine
```

---

### Post by LLRNR on 2006-11-29
Wine is installed in your home dir... it's in ~/.wine

~ = /home/YourUserName
.wine is hidden and if you are in ~ (i.e. /home/YourUserName) and issue **ls -a**, then you'll see the hidden files/folders too.

There's much to say about Wine but, to get started, to understand how it runs and what it does and what you have to configure, look [at this HowTo](http://doc.gwos.org/index.php/HowToWine).

For specific installation instructions... well that depends on what you want to install. The best way to do this is to go to [http://appdb.winehq.org](http://appdb.winehq.org), it's their AppDB (Application Database), where you'll see in the left side a "Search" field - type in the name of the app you want to install and see what the search returns for you - it's best to do so because their AppDB contains installation instructions for various applications you might want to use, so it's better to follow the way that others did to get their app going.

LLRNR

---

### Post by shoaibi on 2006-11-30
don't have much time to read 6-10 opages documents as a whole, just need some short methods for the time being, that is if anyone can provide me.

---

### Post by Foudre on 2006-11-30
the easiest way to install it fully and newest version is either thru the add/remove or using automatix, it sets it up for you there is no real need to manually install it like other distros, but the .wine directory won't work untill you have run the wine command first after its installed type wine or winecfg in the terminal and it creates the directory

---

### Post by shoaibi on 2006-11-30
More confused :0, can anyone please tell me a short an easy to read guide for Wine, not big then 1 page, or can anyone guide me on how to install wine, and then configure it and run it, and then how to install Matlab and SQL Server 2000 on Wine?

---

### Post by robinl on 2006-11-30
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Official guide, completely graphical (no command line needed). You just need the part under "[SIZE=3]**Installing from the WineHQ APT Repository with Synaptic**"

EDIT: why are you trying to sun MS SQL server on Linux? Why not MYSQL of ProsgreSQL? 
[/SIZE]

---

### Post by shoaibi on 2006-11-30
Thanks Robini, well i know, i even thought of making LAMP, but the requirement of our course in this semester is MS SQL 2000 and if i don't use it, i will lose points....

---

### Post by shoaibi on 2006-11-30
This is something your probably would like to see:
root@LocalSystem:/home/ubuntu# sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  glade-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9168kB of archives.
After unpacking 42.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Selecting previously deselected package wine.
(Reading database ... 95009 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.26~winehq0~ubuntu~6.06-1_i386.deb) ...
Setting up wine (0.9.26~winehq0~ubuntu~6.06-1) ...

root@LocalSystem:/home/ubuntu# cd /home/ubuntu/.wine
bash: cd: /home/ubuntu/.wine: No such file or directory
root@LocalSystem:/home/ubuntu# cd /.wine
bash: cd: /.wine: No such file or directory
root@LocalSystem:/home/ubuntu# cd ./.wine
bash: cd: ./.wine: No such file or directory


And when i try to search for wine using the "Search", i can't locate it....

---

### Post by JNowka on 2006-11-30
Ok, I am assuming you have never run wine before, just installed it.

The first thing you are going to want to do is log into the terminal, and be under your own user name, not root.

The next thing you are going to want to do is go to the command line and enter.
> winenothing more nothing less.
This will set up your .wine directory.

At this point you are going to want to install MS SQL 2000.

Still in the terminal, you will enter 
> 
cd /cdrom
ls
This will probably show you the install file.

From this point all you need to do is enter
> wine InstallFile.exewith InstallFile being the name of the installer.

Hope this helps. :)

---

### Post by JNowka on 2006-11-30
Apperently MS SQL Server 2000 does not work under WINE.
[http://appdb.winehq.org/appview.php?iVersionId=5335](http://appdb.winehq.org/appview.php?iVersionId=5335)

Sorry :/

---

### Post by shoaibi on 2006-12-01
So what should i do, i gotta do in MS SQL Sever, or tell me some software which have the same functionalities as of SQL Server

---

### Post by shoaibi on 2006-12-02
> **Darrious said:**
> Why exactly do you need to find out where you installed it.:confused:

I would try this

```
cd /home/USERNAME/.wine
```
Hmm now this command is working.
I wanna install Matlab + MS SQL Server 2000 [or anyother SQL with atleast as much functionalities as SQL server].
I have the setups of these sofwtare in another directoy, its /dev/hdb7. Tell me what to do....

---

