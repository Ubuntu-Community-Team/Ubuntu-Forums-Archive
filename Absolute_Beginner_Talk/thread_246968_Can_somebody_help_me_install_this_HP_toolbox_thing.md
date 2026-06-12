---
title: "Can somebody help me install this HP toolbox thing..?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-08-30
I found it here....[http://hplip.sourceforge.net/screenshots.html]("http://hplip.sourceforge.net/screenshots.html")

I really want that thing,  Whats the best way to install it..???

[http://sourceforge.net/project/showfiles.php?group_id=149981]("http://sourceforge.net/project/showfiles.php?group_id=149981")

---

### Post by Jagot on 2006-08-30
It has installation instructions with specific pointers for Ubuntu:

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

---

### Post by jason.b.c on 2006-08-30
> **Jagot said:**
> It has installation instructions with specific pointers for Ubuntu:

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


[Thats not quite it.!]("http://hplip.sourceforge.net/install/step4/index.html") , I'm not trying to install or set-up a printer , I want to install this extra thing ( like what's found in [COLOR="Blue"]Kubuntu[/COLOR] ) [( HERE )]("http://hplip.sourceforge.net/screenshots.html") to have more control over what i already have....
HP PSC 1315 All-In-One printer..( currently working )

---

### Post by jason.b.c on 2006-08-30
*BUMP*

Any takers...???

---

### Post by jason.b.c on 2006-08-30
Bump Again..

---

### Post by toasted on 2006-08-30
Did you try the installation [instructions]("http://hplip.sourceforge.net/install/index.html") like suggested?

---

### Post by editrix on 2006-08-30
> **jason.b.c said:**
> [Thats not quite it.!]("http://hplip.sourceforge.net/install/step4/index.html") , I'm not trying to install or set-up a printer , I want to install this extra thing ( like what's found in [COLOR="Blue"]Kubuntu[/COLOR] ) [( HERE )]("http://hplip.sourceforge.net/screenshots.html") to have more control over what i already have....
HP PSC 1315 All-In-One printer..( currently working )

You may already have it on your system. I use Kubuntu, but installed my printer in Gnome because the instructions were easier to follow (I have both on my box). I have HPLIP and I never downloaded anything. I can't get into Gnome without cutting off my internet connection so I can't check for you, but poke around. 

Type

locate hplip 

in the command line and a whole bunch of stuff should show up. But, oddly, if you type

which hplip

nothing shows up, so it's not an executable.

---

### Post by goatflyer on 2006-08-30
Hunting around my own gnome install, I find the following included in my ubuntu system:

file:///usr/share/doc/hplip/hplip_readme.html


I don't have any hp printer, but it appears that hplip already is installed in gnome.  Section 7.2 seems to address situations similar to yours.

Hope this helps.

---

### Post by jason.b.c on 2006-08-30
So do you think this configuration window is in my system then..??
[IMG]http://hplip.sourceforge.net/images/HP_Device_Manager.png[/IMG]

[IMG]http://hplip.sourceforge.net/images/HP_Device_Manager-3.png[/IMG]

Thats what i really want...

---

### Post by jason.b.c on 2006-08-30
OK , How can i get **just that user interface** then...???

I've got the hplip stuff on my computer because i've got an HP printer and it works so..??   All i want is that interface...Because i don't have that in here...

---

### Post by jason.b.c on 2006-08-30
> **jason.b.c said:**
> OK , How can i get **just that user interface** then...???

I've got the hplip stuff on my computer because i've got an HP printer and it works so..??   All i want is that interface...Because i don't have that in here...


Bump Up.....:???:

---

### Post by goatflyer on 2006-08-30
In a terminal window try typing

hp-toolbox

This is the command to start the hp device manager.

I get a "PyQt not installed" error, but I don't have an hp printer.

---

### Post by jason.b.c on 2006-08-30
> **goatflyer said:**
> In a terminal window try typing

hp-toolbox

This is the command to start the hp device manager.

I get a "PyQt not installed" error, but I don't have an hp printer.

See..? , Thats what i mean , I don't think i have it at all...:confused: 

> jason@Hp-Vectra-VL:~$ hp-toolbox
bash: hp-toolbox: command not found
jason@Hp-Vectra-VL:~$ sudo hp-toolbox
Password:
sudo: hp-toolbox: command not found
jason@Hp-Vectra-VL:~$



So how do i get it..?

---

### Post by jason.b.c on 2006-08-31
bump--:D

---

### Post by jason.b.c on 2006-08-31
OK , So then could somebody at least tell me if it's even in the repo's or not..??

```
sudo apt-get install hp-toolbox
```

Dosen't do much even if thats the right command or not , I dunno..:confused: 

How do i search the repo's..?  I mean , What's the URL...??

Man i wish i could just get this thing installed...](*,)

---

### Post by grte on 2006-08-31
It's already installed.  You need to install python-qt3 in order to make it run.

```
sudo apt-get install python-qt3
```

Then open Applications > Accessories > Alacarte Menu Editor

Select preferences, and make sure HPLip Toolbox is checked.  You should then be able to load it from the System > Administration menu.

---

### Post by jason.b.c on 2006-08-31
UUMM..?:confused: 

> jason@Hp-Vectra-VL:~$ sudo apt-get install python-qt3
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-qt3: Depends: python2.4-qt3 but it is not installable
E: Broken packages
jason@Hp-Vectra-VL:~$


What should i try now..??

Oh and i don't have alacarte menu editor...The other one will still do it right..?

---

### Post by Titus A Duxass on 2006-08-31
Quote "What should i try now..??

Oh and i don't have alacarte menu editor...The other one will still do it right..?"

You can try searching the forum, there are quite a few threads on HP PSC printer along with a good how to.

Try this (which took me less than 30 seconds to find using the search facility with the letters HP PSC, try it some time!):
[https://help.ubuntu.com/community/HPPrinterInstallation](https://help.ubuntu.com/community/HPPrinterInstallation)

---

### Post by goatflyer on 2006-08-31
Jason, I see you are still using Breezy, while my setup is Dapper.  hplip comes installed with Dapper, is there a reason why you need to stay using Breezy?  If not, then the simplest way might be just to upgrade....

---

### Post by toasted on 2006-08-31
Well, I have Dapper (updates are current)  and this is what happens when I type in hp-toolbox:

```
 [ERROR]: PyQt not installed. GUI not available. Exiting.
/usr/lib/hplip/base/utils.py:1027: GtkWarning: Theme directory  of theme CfG-Crystal-SVG-1.2.0 has no size field

  dialog.run()
```

I also get a warning pop up that says 

```
Warning!
You must install python-qt3 for this program to work
```

I have seen...
GtkWarning: Theme directory  of theme CfG-Crystal-SVG-1.2.0 has no size field
other times so its not relevent to this I dont think

---

### Post by jason.b.c on 2006-08-31
> **Titus A Duxass said:**
> 
Try this **(which took me less than 30 seconds to find using the search** facility with the letters HP PSC, **try it some time!):**
[https://help.ubuntu.com/community/HPPrinterInstallation](https://help.ubuntu.com/community/HPPrinterInstallation)


Well that sure was freakin rude...!!!!!!! [-X   How the h*ll am i supposed to find what i want when there is probably a few hundred threads on the subject...?

[QUOTE=goatflyer]Jason, I see you are still using Breezy, while my setup is Dapper. hplip comes installed with Dapper, is there a reason why you need to stay using Breezy? If not, then the simplest way might be just to upgrade....[/QUOTE]


I can't do that , I had dapper installed in here and i couldn't stand it..!
I couldn't , I really thought it stunk..[See.? , Here's all the problems i had..]("http://www.ubuntuforums.org/showthread.php?t=207014"):mad:

---

### Post by steve.horsley on 2006-08-31
I can confirm that installing python-qt3 on Dapper allows the hp-toolbox GUI to run OK. I don't get that error message about not being able to install python-2.4-qt3. But I'm sure I had hplip working on Breezy too.

---

### Post by toasted on 2006-08-31
Well, I installed python-qt3 and hp-toolbox came up. I have an hp installed over the network though... the printer is shared from my server so hp-toolbox just says that it found no installed printers. Sounds normal eh? 
But what if I were to get a print server for the hp would I be able to use hp-toolbox to config it then?

---

### Post by jason.b.c on 2006-08-31
> **toasted said:**
> Well, I installed python-qt3 and hp-toolbox came up. I have an hp installed over the network though... the printer is shared from my server so hp-toolbox just says that it found no installed printers. Sounds normal eh? 
But what if I were to get a print server for the hp would I be able to use hp-toolbox to config it then?

How/Where did you get that python-qt3 thing...?

---

### Post by toasted on 2006-08-31
Synaptic - but im using dapper

---

### Post by jason.b.c on 2006-08-31
> **toasted said:**
> Synaptic - but im using dapper

Would you know then how to help me install the toolbox in breezy..? , I've downloaded all the stuff for it ( i think )....:confused:

---

### Post by toasted on 2006-08-31
I would if I could, but ive only been using linux for a few weeks. I never used Breezy before. What type of file is it that you need to install? Im sure there is info here somewhere that will tell how to install any type of file and then there is always this - 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I will help if I can though

---

### Post by jason.b.c on 2006-08-31
> **toasted said:**
>  What type of file is it that you need to install? 

I will help if I can though


This===> [hplip 1.6.7]("http://sourceforge.net/project/showfiles.php?group_id=149981") , All of it i guess..For the toolbox...

---

### Post by Titus A Duxass on 2006-08-31
I wasn't being that rude, there were no expletives in the text.

---

### Post by jason.b.c on 2006-08-31
> **Titus A Duxass said:**
> I wasn't being that rude, there were no expletives in the text.

**Try it sometime..!!**   You don't call that rude...??  I do..!

---

### Post by ounas on 2006-08-31
Hei This works, thanks..
:o

---

### Post by toasted on 2006-08-31
> **jason.b.c said:**
> This===> [hplip 1.6.7]("http://sourceforge.net/project/showfiles.php?group_id=149981") , All of it i guess..For the toolbox...

What I did - 
Downloaded the file
Extracted the program folder (double clicked the file)
Found the install directions in the doc folder (html file)
posted the install section below.......

**[COLOR="DarkRed"]warning - [/COLOR]**if you experience trouble I probably cant help unless its stupidly simple  LOL  Somebody probably can though :D 

----------------------------------------------------------

Installation - Step 3 - Download and install HPLIP software

If you already have the latest HP printing software installed, then proceed to Step 4: Add the Printer.

If the HP printing software is not included with your Linux distribution, or you want to ensure that you have the latest version of the software, follow these steps to download and install the HP printing software.

Warning: If you are upgrading HPLIP and HPLIP is already preinstalled with your distribution, or you if you installed HPLIP using an RPM, DEB, or other package, please uninstall the previous version using the method specific for your distribution. If you do not do this, you may have package conflict issues or functionality problems.

   1. Download the HPLIP tar file that contains the current HP printing software from the HPLIP sourceforge download page.
   2. Make note the folder in which you save the HPLIP tar.gz file.
   3. Open a console/terminal window.
   4. Enter this command to navigate to the folder that contains the HPLIP tar file that you downloaded in step 1:

```
cd [file path]
```

(for example: cd /home/user/documents)

   5. Enter this command to extract the driver files from the HPLIP tar file:

```
tar xvfz [HPLIP filename.tar.gz]
```

(for example: $ tar xvfz hplip-0.9.tar.gz)

The files are extracted to a directory named for the HPLIP version (for example, "hplip-0.9").

   6. Enter this command to navigate to the directory containing the HPLIP files:

```
cd [folder name]
```

(Example: # cd hplip-0.8)

   7. Enter this command (for 32-bit only - for 64-bit, skip this step and do step 8):

```
./configure --prefix=/usr
```

Important

Special step required for 64-bit systems.

   8. For 64-bit Systems enter this command:

```
./configure --prefix=/usr --libdir=/usr/lib64
```

   9. Enter this command:

```
make
```

  10. Follow these steps to log in as the super user:

If you are using Ubuntu go to Step 14.

Enter this command:

```
su
```

  11. Press Enter.
  12. Enter the root password.

> Warning

The root password gives you administrative privileges on the system.

  13. Press Enter.
  14. Enter this command:
```

make install
```

For Ubuntu, Enter this command:

```
sudo make install
```

  15. Enter this command:
```

/etc/init.d/hplip restart
```

For Ubuntu, enter this command:
```

sudo /etc/init.d/hplip restart
```

  16. Enter this command:
```

/etc/init.d/cups restart
```

For Ubuntu, enter this command:
```

sudo /etc/init.d/cupsys restart
```

---

### Post by lightubun on 2006-09-02
go to Applications > Accessories > Alacarte Menu Editor
or
right click on Applications > Edit Menus
on left scroll down to Administration and hightlit it
on right side tick the HPLIP ToolBox.
close

the file is /usr/bin/hp-toolbox

you will find it on.. System > Administration > HPLIP Toolbox
good luck

---

### Post by jason.b.c on 2006-09-05
> **lightubun said:**
> go to Applications > Accessories > Alacarte Menu Editor
or
right click on Applications > Edit Menus
on left scroll down to Administration and hightlit it
on right side tick the HPLIP ToolBox.
close

the file is /usr/bin/hp-toolbox

you will find it on.. System > Administration > HPLIP Toolbox
good luck

Umm Yea , well i realize you were trying to help but, None of that stuff even exists, Where did you find that....?????

Oh and could somebody help me more with this hp toolbox install...? , I tried what was posted above but it simply refuses to install...!!!   What am i missing..??

Could i ask someone to please download that package and just tear it apart if you have to , Study it if you will so you can see what i mean..?? , Please tell me exactly what i need to install it and where to download those things....Thanks...:-D

---

### Post by lightubun on 2006-09-05
you can find the answer here [https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

important: otherwise HPLIP ToolBox wont work
befor you add printer

type
> $ lpinfo -v
network socket
network beh
network bluetooth
direct usb://HP/DeskJet%203820?serial=CN2A61N13N18
direct [COLOR="Purple"]**hp:/usb/DESKJET_3820**[/COLOR]?serial=CN2A61N13N18
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
direct canon:/dev/usblp0
direct epson:/dev/usblp0
network smb

in autodetect choose the right printer which is in this case
HP DESKJET_3820
not
HP Deskjet 3820

in model choose
Deskjet 3820

hope that help

---

### Post by useResa on 2006-09-05
I only came across your thread right now.
Didn't read the full thread, but if you are looking for instructions on how to install the latest hplip version, please look at page 3 of a thread I started

[http://www.ubuntuforums.org/showthread.php?t=245877&page=3](http://www.ubuntuforums.org/showthread.php?t=245877&page=3)

In reply #22 you will find step by step how I installed it.
After installation I had the tool you indicated on the first page available.

Good luck and regards

---

### Post by jason.b.c on 2006-09-07
Does anybody know what is missing from breezy that would stop this toolbox thing from installing...???

I'm tired of screwing with it now....**[SIZE="3"]I just want it to work...![/SIZE]**

---

### Post by mahiyar on 2006-12-25
I know it is too late to reply, but recently I went through same travails of Jason n ended up spending better part of two hours for the solution. Here it is.
1. There is a difference between 6.06 and 6.10 as far as printer/HPLIP install is concerned, HPLIP does talk about Ubuntu 6.10 but there are a lot of broken dependencies in Ubuntu 6.10 for HPLIP to install.
2. Some older version of HPLIP already comes installed with 6.10.
3.The moment you plug in USB of printer, the installation is a breeze, but then u do not get the HP tool box facility.
4.To get the HP tool box facility u need Python-qt, use only and only synaptic to search and install any package, doing so will ensure dependent packages will be installed too. (System>Admin>Syna~). I'am very wary of using the sudo apt-get, not that it does not work, but that I'am not aware of any linked packages.
5)After Python-qt is installed you can run hp-toolbox from command line. You get a nice box without any printer, even if CUPS browser shows u one, the System printer shows u one.
6)So you use >sudo hp-setup, and follow the trails to add a new printer, and voila your HP toolbox has a printer and all the related goodies.
7)However please do not make this the default printer and removing the other one, as there will be difficulties printing through this printer. The best way is to keep both the icons the one discovered by Gnome being the default,  and the other for your HP-Toolbox maintenance part.
8)It would be a lot better if we could install HPLIP without running into dependencies hell.

---

### Post by Sef on 2006-12-25
> 1. There is a difference between 6.06 and 6.10 as far as printer/HPLIP install is concerned, HPLIP does talk about Ubuntu 6.10 but there are a lot of broken dependencies in Ubuntu 6.10 for HPLIP to install.

I use Edgy Eft (6.10) and got HPLIP Toolbox this way.   System > Preferences > Menu Layout > System Preferences > checked HPLIP Toolbox > close.

---

### Post by mahiyar on 2006-12-26
Well I was not that lucky, HP toolbox needed python qt to start. Ofcourse at the end of all the steps I did the same as u.

---

### Post by steve.horsley on 2006-12-26
I just managed to install it on Edgy. In two steps:

1)
As Sef says: System > Preferences > Menu Layout > System Preferences > checked HPLIP Toolbox > close.
After this System->Preferences->HPLIP toolbox gives an error about missing python-qt3

2)
System->Administration->Synaptic, find and install python-qt3

That's it. Job done.

---

