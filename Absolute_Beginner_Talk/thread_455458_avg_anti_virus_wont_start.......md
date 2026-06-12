---
title: "avg anti virus wont start......"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-26
hello, ive just installed avg anti virus, i know that technically you dont need an anti virus, but ive netwirked with 2 pc's with xp on.
the problem is that ive downloaded - avg75fld-r47-a1022.i386.deb and then once downloaded i ran it and installed it ok, then ive gone to -- applications -- system tools and clicked on the avg icon and nothing is happening.
it all installed ok, and it installed fine the last time i tried it, so im not sure whats gone wrong this time, it does look like its trying to load it but nothing actually comes up.
any help will be appreciated
cheers.
i didnt use a how to install avg because as its a .deb file you should just be able to run it and it'll install

---

### Post by Ek0nomik on 2007-05-26
Where did you get the .deb file?

I guess the only thing I would suggest is uninstalling and try reinstalling it.  Sometimes weird things will happen and work.  Maybe try downloading it from a different source?

---

### Post by nickpaton on 2007-05-26
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=136064") post which describes where to get AVG and how to install etc.

---

### Post by oilchangeguy on 2007-05-26
why not just remove avg. if you've sent files to your windows computer simply scan the files before you open them, with whatever anti-virus software you use with the windows computer.

---

### Post by techno-mole on 2007-05-26
i got the .deb file from grisofts website, and all you need to do is click on the .deb file once you have downloaded it and it'll install itself.
the how to thats bee mentioned is for a slightly different .deb file, the version im trying to install is a newer version, least i think it is.
cheers.

---

### Post by paparucino on 2007-05-26
> **techno-mole said:**
> i got the .deb file from grisofts website, and all you need to do is click on the .deb file once you have downloaded it and it'll install itself.
the how to thats bee mentioned is for a slightly different .deb file, the version im trying to install is a newer version, least i think it is.
cheers.
Run synaptic, look for avg and in the "installed files" you will' see where .deb is installed. Look inside /usr/bin or /usr/local/bin to see the filename which runs avg. 
Run it from a terminal a check the errors it will output

---

### Post by techno-mole on 2007-05-27
fixed it, it took some time.
i used part of the method in the how to guide that was posted, but it turned out to be something to do with the .deb file i was trying to use, i found a link to another .deb file and that one installed and worked perfectly, i just had to set it up to let me update.
cheers for the help
:D

---

### Post by Greasyfingers on 2007-05-28
> **techno-mole said:**
>  i found a link to another .deb file and that one installed and worked perfectly

Don't keep it to yourself, I've been struggling to get it to work too. Where's this other file kept?

Using the .deb package from the [_Grisoft_]("http://free.grisoft.com/doc/5390/lng/us/tpl/v5") site, the main menu launcher doesn't seem to do anything, and nor does the launcher created in [_the guide_]("http://ubuntuforums.org/showthread.php?t=136064") referred to previously, but if I enter the launcher commands in a terminal, I get:
```

$ avggui
/opt/grisoft/avggui/prog/config.py:12: DeprecationWarning: The sre module is deprecated, please import re.
  import sre
avggui: can't find file /opt/grisoft/avggui/config/userinfo.cfg
```
or
```
$ gksudo avggui &
  import sre
avggui: can't find file /opt/grisoft/avggui/config/userinfo.cfg
```

Can anybody give me any clues how to make this work?

---

### Post by nickpaton on 2007-05-28
Just tried the HOWTO on another of my Ubu boxes and got the following error when running this first command:

```
sudo dpkg -i avg75fld-r45-a0973.i386.deb
```

```
dpkg: error processing avg75fld-r45-a0973.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 avg75fld-r45-a0973.i386.deb
```

The reason is that the downloaded file from the grisoft site is now 

> avg75fld-r47-a1022.i386.deb

So modify the first command to read:

```
sudo dpkg -i avg75fld-r47-a1022.i386.deb
```

Yup, that now works as does the launcher.
When you copy the launcher code into the window, remember to ctrl and x keys together, then y to save and enter to confirm and exit.

HTH  Nick

EDIT:  Just tried clicking on the App icon under Applications > System Tools and it comes up with the password box but doesn't actually launch.

I'll look into this further.

---

### Post by techno-mole on 2007-05-28
sorry, my bad.
ok first id make sure some of the files avg needs are up to date, this may solve you problem.
first run --> 
sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2

(i copied and pasted it, so it should be right) let that lot download and install, you may already have it all.
i couldnt get the avg how to that was posted in this thread to work for the latest version by the way. it did however create a launcher under --> applications --> accessories, which for me did a grand total of nothing.
right once you've downloaded and installed that lot you need to go to - [http://free.grisoft.com/softw/70free/setup/avg75fld-r45-a0973.i386.deb](http://free.grisoft.com/softw/70free/setup/avg75fld-r45-a0973.i386.deb) this should start a download (you may need to copy and paste the link), just download it to your desktop, if the link doesnt work go to page 25 of the HOWTO : Install AVG free anti-virus (theres a link to it in this thread) 2 or 3 posts down is a link to a file, its for kubuntu but works just as well on ubuntu, and like i said let it download.
it should be a deb file so you can just double click it and run it, this should install avg, but again the link under apps --> accessories --> avg for linux work station may well work (as in load avg) but you probably wont be able to update it, so you will need to go back to avg how to to create the other launcher.
so to re-cap - click link above and download file (i say to the desktop because thats where the guide tells you to install it from, but i dont think it matters as long as you know the paths)
once downloaded, double click and install it.
then go back to the how to as it tells you how to create the second launcher you will need if you want to up date.
its long winded i know, but its how i did it.
cheers and i hope this helps, theres also a link for another av program in the avg how to, that one may be easier.

---

### Post by nickpaton on 2007-05-28
Techno-mole

Many thanks for that, and once again the old link you supplied works.  Yes I needed to do the dependency update (but this was not needed on my other box which had a clean install of Feisty.
This box was an update from Edgy and possibly the dependencies are not installed as a result??!

There's definitely something up with the update file and I've posted into the HOWTO post to ask AI (or someone more knowledgable than me!) to look into it.

Thanks once again  Nick

---

### Post by nickpaton on 2007-05-28
FWIW

I decided to try uninstalling the older .deb (the one in the HOWTO) and install using the latest one.

I've detailed it all[ here]("http://ubuntuforums.org/showthread.php?t=136064&page=27"), but basically I'm now unable to install either the old or new one!!!

I know there's probably a simple fix, but I don't know what it is.  Moral of the story - if it aint broke don't fix it!!

---

### Post by techno-mole on 2007-05-28
i managed to get it un-installed using synaptic, if you search for avg in synaptic it should come up, it did for me, un-install it from there (if you can) then you may have to go looking for the left over files, ive found that using purge doesnt really get rid of anything, so look in the file system, it may be in usr --> local --> share ? maybe some one will put me right on that, and you may have to be root to delete any files --> sudo nautilus in terminal.
did you try the sudo apt-get --purge remove avggui ?

cheers

---

### Post by nickpaton on 2007-05-28
Before trying to uninstall it via Synaptic, I decided to simply delete every instance of AVG and found everything was in /opt/grisoft/, so simply got rid of that.

That has since prevented me from deleting  avg75fld that is found in Synaptic.

I'm going to try later this week to copy the contents of the /opt/grisoft file from my other box back into this one and see if that sorts it.

tried purging avg75fld and avggui but it always comes back to the same error message:

>  Removing avg75fld ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg75fld (--purge):
 **subprocess pre-removal script returned error exit status 100**
Errors were encountered while processing:
 avg75fld
E: Sub-process /usr/bin/dpkg returned an error code (1)

The line in bold has been a common one throughout.

I also tried:

```
sudo dpkg --remove --force-remove-reinstreq avg75fld
```

(from another post and a suggestion from one of the forum staff - thanks!)

I'm not actually that interested in having antivirus but it's become a challenge!!

---

### Post by Greasyfingers on 2007-05-28
Thanks guys.

I've done the update that techno-mole suggests. I had already installed the later version of the .deb package, but I redownloaded it and reinstalled it. No change.

I used Synaptic to uninstall the package avg75fld without a problem. I reinstalled the package as per the How To (didn't use Package Installer). No change. 

Uninstalled again, downloaded and installed the *older* version. This starts up and runs OK, but it currently fails when I try to update it. Not sure why this is, but at least it's running now.

Appreciate your help.

---

### Post by techno-mole on 2007-05-29
thats what i ended up with, i couldnt get the .deb file from grisofts website to work properly, so i went through the how to and used the older one.
and when it installed it wouldnt update, i got an error about permissions, so what you need to do is  create a second launcher, and after you have done that you will end up with a launcher under applications --> accessories and another launcher under applications --> system tools.
it does tell you how to get round this in the how to though.
try this - open terminal and type - sudo gedit /usr/share/applications/avg.desktop

then in the file that opens up type (or copy and paste) -

[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;

this should create the second launcher i mentioned, when you click on it you may get a box pop up that says something about the license this is normal, its just letting you know its a free version, and if you want you can add the launcher to a panel (its what i did with alot of stuff)
it should now let you update it by clicking the update button.
cheers

ps - you may also want to update some stuff (apparently this helps with running the gui in avg) - sudo apt-get install alien libstdc++2.10-glibc2.2 python2.4-glade2 python2.4-gtk2
hope this helps.

---

### Post by Greasyfingers on 2007-05-29
Yep, did all that (the launcher that comes with the application just points to avggui, and needs gksudo preceding it to give the user permission to open it).

It does seem that the older .deb package is the one that works. I can now open the GUI OK, can run a test, and it even *appears* to fully download an update file, but as it's finishing off the download I get

"Online update failed.
Reason: Error occurred while processing the update files."

I've downloaded the files manually from [_here_]("http://free.grisoft.com/doc/24/lng/us/tpl/v5"), pointed AVG to them, but it tells me that there is nothing to update, and then crashes.

I might see if there are any clues on the [_AVG forum_]("http://forum.grisoft.cz/freeforum/index.php?0")

---

### Post by techno-mole on 2007-05-29
the update error may be something to do with grisofts update servers, i know that the windows version that we run on the other 2 pc's has had update problems for a couple of weeks.
i upadated my avg this morning and it went fine.
maybe you could try and remove avg and try from scratch, to be honest im not sure, i do know that once avg is its a bugger to get it off again (least it was for me) i had a simialr proble with cedega, installed fine, but had trouble actually installing a game, so though id take it off until id read more about it, could i get it off ? nope, in the end it didnt matter because i re-formatted, due to my policy of " if it aint broke, fix it until it is " 
cheers

---

### Post by Greasyfingers on 2007-05-30
Well, I'm thinking I should knock AVG on the head for now. This is my experience with AVG for Linux on Feisty so far.

Installed the package avg75fld-r47-a1022.i386.deb. Couldn't start the app from a launcher, from the menu, or from the command line.

Uninstalled the package without any problems using Synaptic

Installed earlier version avg75fld-r45-a0973.i386.deb. This opened OK from a launcher (menu icon wasn't quite right), ran a test OK, but ran into problems when updating the scanner file - it would appear to download three files, but then failed with the message "Online update failed.
Reason: Error occurred while processing the update files."

Tried to update manually by dowloading the [_update files_](http://free.grisoft.com/doc/24/lng/us/tpl/v5) from the AVG site and pointing the GUI at them (Service/Program Settings/Update/Source), but this only returns "Nothing to update".

Downloaded the latest version avg75fld-r47-a1025.i386.deb, but could not uninstall the existing version, and nor could I install the new one over the existing one - "avg75fld: subprocess pre-removal script returned error exit status 150."

Can I uninstall it by simply deleting all the files it added, or is this a big no-no?

---

### Post by techno-mole on 2007-05-30
i dont see the harm in removing the files manually, ive done it on a number of occasions in linux and under windows and never had any problems, apart from things being a little messy, for example if you remove all the avg/grisoft files this will remove the application, but you will probably be left with the launchers in the applications -- accessories and applications -- system tools
so i guess it up to you, like i said ive never had any problem doing things this way, and i dont think any other applications on the system will be dependant on the avg/grisoft files, but wait and see if anyone else posts as what im saying may not be right and i wouldnt want you to stuff up your system on my say so :D
cheers

---

### Post by matchstich on 2007-05-30
i installed avg a long time ago, never did get anything in apps>acces to run it.  followed some advice and got the updater in system tools, it does update. i updated today.
how do i get a icon in apps>accs to run it
thanks

---

### Post by daimaru on 2007-05-30
well im using antivir which works fine. but maybe its just permissions crap thats bothering you . 
in terminal type: 
```
sudo alacarte 
```

select system tool or where ever ur avg thingi is installed, right click on it choose properties and make sure it says  gksu avg  ... or gksu /usr/bin/avg or something in it .. the important part is the gksu part so just add it b4 ur command and see if it runs that way.

---

### Post by Greasyfingers on 2007-05-30
> **matchstich said:**
> 
how do i get a icon in apps>accs to run it

Go System -> Preferences -> Main Menu

Select Accessories in the left pane

Right click AVG in the right pane, select Properties

Change the Command to gksudo avggui

---

### Post by matchstich on 2007-05-30
> **Greasyfingers said:**
> Go System -> Preferences -> Main Menu

Select Accessories in the left pane

Right click AVG in the right pane, select Properties

Change the Command to gksudo avggui

i went to system>preferences> but there is no main menu.

thanks

---

### Post by matchstich on 2007-05-30
> **daimaru said:**
> well im using antivir which works fine. but maybe its just permissions crap thats bothering you . 
in terminal type: 
```
sudo alacarte 
```

select system tool or where ever ur avg thingi is installed, right click on it choose properties and make sure it says  gksu avg  ... or gksu /usr/bin/avg or something in it .. the important part is the gksu part so just add it b4 ur command and see if it runs that way.

went and did what posted here, that gksu is already there but when i closed it i got this

 GnomeUI-WARNING **: gnome_icon_entry_gtk_entry deprecated, use changed signal!

what is that?
thanks

---

### Post by Greasyfingers on 2007-05-30
> **matchstich said:**
> i went to system>preferences> but there is no main menu.

In that case, right click on System and choose Edit Menus. This will bring up the Main Menu window.

---

### Post by matchstich on 2007-05-31
gksudo avggui &

is what it say in properties for avg, it is in menu editor.  i have it checked 
but it isn't showing  up in system tools, 
only the updater does.

---

