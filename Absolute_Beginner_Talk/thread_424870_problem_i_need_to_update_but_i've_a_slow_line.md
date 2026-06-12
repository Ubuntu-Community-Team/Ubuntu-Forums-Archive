---
title: "problem: i need to update but i've a slow line"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2007-04-27
hi,
i'd like to update my edgy to feisty, but i have e slow line, an isdn.
Last time to update from dapper to edgy i donwloaded the alternate cd, but with the result that after installing
edgy all packages were yet obsolete and i had to update all again. Eventually i had to donwload  all twice.:( 
Now i'd like to update it online and only one time. I tried to use the update manager, but at a point is says that more than 900 MB must be downloaded, and the precess cannot be stopped. I've a 24h flat but i cannot let the pc switched on for the entire day, so i need to update in more days, so i need a way to start-stop-restart and in safety. Is there a way to do that?
thanks

---

### Post by HereInOz on 2007-04-27
Maybe you can upgrade from the CD, and then select your updates a few at a time so that you are able to gradually download the updates that you need after upgrading from the CD.

That is the only way that I can think of.  Anyone got any other ideas?

---

### Post by johnny4north on 2007-04-27
you could check the magazine rack for linux world[etc] for cd/dvd of ubuntu 7.04  also your local linux club might might be able to give you a cd/dvd.

---

### Post by airtonix on 2007-04-27
there is a bug in the software that creates this download script but in theory it all works.

[LIST=1]
[*] open up "synaptic package manager".
[*]click "mark all upgrades" or click to install all the software you need/want.
[*]then from the file menu select "generate package download script".
[*]name it and save it on your desktop.
[*]open it in gedit,vim,leafpad,mousepad....or whatever to clean up the bugs in the file :[LIST]
[*] the file will contain a line for each file required, each line is a wget command. but the synaptics program doesnt put spaces where they should be.
[*]so at the start of each line you will find this :> wget [COLOR=Red]-chttp://[/COLOR]some.ubunut.mirror.domain.name.com/pub/
[*]when it should be this : > wget [COLOR=Blue]-c http://[/COLOR]some.ubunut.mirror.domain.name.com/pub/
[*]you can use the find and replace feature that notepad might have to repeat this task, sorry starting to forget all the funny little things about windows.
[*]since the # mark is a comment in windows batch files. we wont need to remove it.[/LIST]
[*]then take this file to a computer with a decent connection windows or linux, remember to take blank cd/dvd or a usb drive with you.
[*]Run the download script :[B]
on windows[/B][LIST=1]
[*]copy the file to the desktop and rename the download script so that ".bat" is on the end of the filename
[*]double click the filename to run it.[/LIST]
**on linux**
[LIST=1]
[*]  i think all thats needed here is > chmod +x name-of-your-download-script[/LIST]
[*]this should begin calling wget to download one file after the other.
[*]Once it has finished burn the files onto a cd or move them onto a flash drive of somekind (to get them back to your home computer)
[*]open up "synaptic package manager".
[*]goto file -> add downloaded packages
[*]navigate to the cd or device with which you brought all your new packages home with.
[*]synaptic should start processing each deb file and installing it.[/LIST] 
hope this helps.....i was in your position but i went further and copied the netire twelve gigs of the ubuntu repo on my home drive....so i could apt-get offline and stay upto date offline as well by using a method similar to the above(debmirror actually).

---

### Post by ubunlilluz on 2007-04-27
i've got a subscription to Linux Magazine, and surely next month annexed there'll be the cd of ubuntu.
Ok, but i don't want to reinstall ubuntu, i want only to update it to 7,04, without loosing all data and profile i had. Is it possible to do  it using the cd annexed to magazines or i only have to use the alternate cd?
thanks

---

### Post by zvacet on 2007-04-27
Only way to upgrade from Cd is to use alternate CD.If Cd is without errors and if it is burn properly,you should not have problem with upgrade.Command is 

```
gksu "sh /cdrom/cdromupgrade" 
```

You can find information on this page 

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

---

