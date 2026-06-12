---
title: "firefox upgrades in breezy badger"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by gymsmoke on 2006-04-20
I upgraded my version of Firefox from 1.07 to 1.5, and this morning got an update notice for firefox 1.08, and firefox-gnome-support 1.08.

I also got an upgrade notice for python-vte 1.0.11, and update manager (which i'm sure are unrelated)...

Is it 'safe' to update the default firefox,firefox-gnome, to 1.08 even though i'm actually running 1.5 since the upgrade to 1.5 needed to have the current installed version kept on the system?

---

### Post by OffHand on 2006-04-20
[QUOTE=gymsmoke]I upgraded my version of Firefox from 1.07 to 1.5, and this morning got an update notice for firefox 1.08, and firefox-gnome-support 1.08.

I also got an upgrade notice for python-vte 1.0.11, and update manager (which i'm sure are unrelated)...

Is it 'safe' to update the default firefox,firefox-gnome, to 1.08 even though i'm actually running 1.5 since the upgrade to 1.5 needed to have the current installed version kept on the system?[/QUOTE]
Yes, it is. It might set your icon back to default but that can easily be changed back. Make a backup of bookmarks etc, just in case.

---

### Post by Nordoelum on 2006-04-20
I have installed Firefox 1.5.0.1 manually. Then I ask, how to make version I have to update its self with the Tool -> Check for updates? It is grey and unclickable.

---

### Post by Oceola on 2006-04-20
Not my intention to insult anyone but is there some reason why 1.08 was placed in the Hoary repository instead of 1.5.02. I run an i686 machine and dumped the i386 kernals a while ago. I upgraded packages which are now just showing up in Dapper and am wondering why these upgrades aren't being passed along to the other repository. 1.5.02 upgraded automatically with the patch as did 1.5.01 and this from a manual install of 1.5 when I couldn't find an update in the repository. Seems strange to go backwards.

I also would like the newer Linux kernals and most of the other packages without having to completely re-install my entire system. I'm on dialup and it's unbelievably tiring to have to download massive amounts of software in order to keep up with the total system changes. I didn't upgrade to Breezy as it wanted to remove packages which weren't on the disk and to spend several days on dialup doing downloads just ins't the way it's supposed to work, that and I wasn't sure it was going to support some of the packages I had installed.

I wanted to grouse about this before but since I'm new to Linux I know there's a lot I don't know but wasting time is wasting time and old versions or proprietary modified files don't seem to be in keeping with the Debian concepts as I've read them.

-Dave

---

### Post by AndyC_772 on 2006-04-20
I had the same update notification yesterday, and I'm running 1.5 too, on Breezy. I've not installed the update to 1.08 and was wondering what to do about it, especially given that Firefox security flaws have hit the headlines in the last few days.

Is there a good reason why I'm not being offered an update to 1.5.whatever?

---

### Post by gymsmoke on 2006-04-20
I just ran the update to Firefox 1.0.8, and the gnome update as well.  It didn't effect Firefox 1.5.0.1 at all, and kept the bookmarks intact.

I also agree that, since 1.5.0.1 is stable on Ubuntu 5.10, it should definitely get added to the repo's, but I'm sure at this point that the developers have their hands full with the quirks in Dapper, and then there's Edgy ...

---

### Post by LanDroid on 2006-04-20
[QUOTE=Nordoelum]I have installed Firefox 1.5.0.1 manually. Then I ask, how to make version I have to update its self with the Tool -> Check for updates? It is grey and unclickable.[/QUOTE]
Terminal command:
> gksudo firefox
Help=>Check for update is now clickable...
____________________________________
WuHu! Total NuuuB helping out... :-\"

---

### Post by Mustard on 2006-04-20
Oceola (aka Dave),

These issues have been discussed in detail in other areas of the forum and I don't think its worth replicating the same discussions in this thread. :)

I would use the search functions to find the threads concerned and I would imagine the 'reasons' you are looking for will be found in them.

To address the OP,

I have upgraded to 1.0.8 and my 1.5.0.2 version is still running fine.

---

### Post by ronmarley1 on 2006-04-20
[QUOTE=Nordoelum]I have installed Firefox 1.5.0.1 manually. Then I ask, how to make version I have to update its self with the Tool -> Check for updates? It is grey and unclickable.[/QUOTE]
In a terminal, ```
sudo firefox
```
Then you can use the Help --> Check for Updates...

EDIT: Doh, shoulda read the whole thread first...  sorry.

---

### Post by EKa on 2006-04-21
> Yes, it is. It might set your icon back to default but that can easily be changed back. Make a backup of bookmarks etc, just in case.

How does it exactly happen? I need to change the icon for Thunderbird too.

---

### Post by EKa on 2006-04-21
Found this one...

> Go to /home/mindtrik/.icons and find the folder for your theme. Then replace /home/mindtrik/.icons/themename/size/filesystems/gnome-fs-home.png with the icon you want.

> Hint: .icons is a hidden folder. If you open up Nautilus, press Control-H to see hidden directories.

thanks

---

### Post by Oceola on 2006-04-22
[QUOTE=Mustard]Oceola (aka Dave),

These issues have been discussed in detail in other areas of the forum and I don't think its worth replicating the same discussions in this thread. :)

I would use the search functions to find the threads concerned and I would imagine the 'reasons' you are looking for will be found in them.

To address the OP,

I have upgraded to 1.0.8 and my 1.5.0.2 version is still running fine.[/QUOTE]

Thank You](*,)

---

### Post by Nordoelum on 2006-06-04
[QUOTE=LanDroid]Terminal command:

Help=>Check for update is now clickable...
____________________________________
WuHu! Total NuuuB helping out... :-\"[/QUOTE]
Doesn't work in dapper :(

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=Nordoelum]Doesn't work in dapper :([/QUOTE]
In my case it takes me to the default homepage :
file:///usr/share/ubuntu-artwork/home/index.html

Which is a great solution because we don't want firefox upgrade mechanisms to interfere with those of ubuntu (apt).

---

### Post by Nordoelum on 2006-06-04
Yeah, but I want the 1.5.0.4 update installed.

---

### Post by nanotube on 2006-06-04
[QUOTE=Nordoelum]Yeah, but I want the 1.5.0.4 update installed.[/QUOTE]
for installing ff1.5, as well as for getting updates to it, see first link in my sig, and go to "install firefox" section for installing 1.5.x, and to "update firefox" section, for running updates on it. that ought to fix you up.

---

### Post by Nordoelum on 2006-06-04
[QUOTE=nanotube]for installing ff1.5, as well as for getting updates to it, see first link in my sig, and go to "install firefox" section for installing 1.5.x, and to "update firefox" section, for running updates on it. that ought to fix you up.[/QUOTE]
Thank you :D But I am using Xubuntu on my server.

---

### Post by nanotube on 2006-06-04
[QUOTE=Nordoelum]Thank you :D But I am using Xubuntu on my server.[/QUOTE]
firefox is DE-independent, so whatever that says about installing the official firefox and updating it applies under any DE, gnome, kde, xfce, or anything else.

so, how is xubuntu? :)

---

### Post by Nordoelum on 2006-06-04
That I know :P But that Application manager you have used in your linkis for the Gnome based solution.

XFCE 4.4 Beta is alot better then 4.2.

---

### Post by nanotube on 2006-06-04
[QUOTE=Nordoelum]That I know :P But that Application manager you have used in your linkis for the Gnome based solution.

XFCE 4.4 Beta is alot better then 4.2.[/QUOTE]
xubuntu doesn't come with apt-get? that's the only package manager i used in the firefox install script (to make sure libstdc5 is installed). 

i'm running on gnome, but thinking of checking out xfce once i upgrade to dapper. ;)

---

### Post by aysiu on 2006-06-04
Xubuntu has apt-get. It also has Synaptic Package Manager.

[http://packages.ubuntu.com/dapper/misc/xubuntu-desktop](http://packages.ubuntu.com/dapper/misc/xubuntu-desktop)

---

### Post by Nordoelum on 2006-06-04
****

> **Update Firefox 1.5 to 1.5.0.1 (or later)**

 Since we installed the "non-ubuntu" version of firefox, above, in order to update it, we have to use the native firefox updater, rather than the apt-get method. In order for firefox to update itself, though, it will have to be run as root. So quit all firefox windows, and in a terminal, type: 
 ```
gksudo firefox &
```
This will start firefox as root. Select Help>Check for Updates from the menu, and it will find an update, and download it. You will then get a message that says that Firefox needs to be restarted to apply the update, and you can choose "Later" or "Restart Firefox Now". DO NOT choose "Restart Firefox Now", instead DO choose "Later". (If you choose restart now, then firefox will close, and restart itself - but when it restarts it will no longer be running as root, and the update will fail.) Then close firefox yourself, and in a terminal again issue: 
 ```
gksudo firefox &
```
This will restart firefox as root, and successfully complete the update. Now, you can close firefox again, and then start it as normal from the menu, not as root. And you should be all good to go!

It wont do the trick :/ I still get a grey "Check for Updates...".

---

### Post by nanotube on 2006-06-04
[QUOTE=Nordoelum]****


It wont do the trick :/ I still get a grey "Check for Updates...".[/QUOTE]
oh heh i see
well instead of gksudo, just use plain "sudo firefox". maybe that will do it. because yes, gksudo is gnome-only.

but... gksudo is not a package manager, that's why i was confused. it's just a graphical sudo :)

edit: just thought of something. if you are trying to get the "check for updates" thing to work on the ubuntu-packaged firefox, it may not work anyway. i think it will only work on an official mozilla-packaged firefox. so first step is to install the official firefox.

---

### Post by aysiu on 2006-06-04
nanotube, doesn't launching *sudo firefox* risk corrupting the permissions on the user's profile? I think ```
gksudo firefox
``` or ```
kdesu firefox
``` might be preferable. That's how I updated mine to 1.5.0.4

---

### Post by nanotube on 2006-06-05
[QUOTE=aysiu]nanotube, doesn't launching *sudo firefox* risk corrupting the permissions on the user's profile? I think ```
gksudo firefox
``` or ```
kdesu firefox
``` might be preferable. That's how I updated mine to 1.5.0.4[/QUOTE]
i never had any problems.  according to the "official" rootsudo page, 

> NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

so, if you are not planning on making another login while running the app, there is no risk. (note that just starting a terminal does not count as a login.) in fact, i would venture to say (though i am not sure), that only another graphical login would mess with iceauthority, because i think that has to do with X stuff, not other system stuff. 

but anyway, that's why my howto uses gksudo, so as not to raise these issues.  but if gksudo doesn't work for him, he should try sudo - just not run around logging in while doing it :). i actually upgrade my firefox with plain sudo...

---

### Post by aysiu on 2006-06-05
Thanks for the clarification. I do know that certain graphical applications do mess up the .ICEAuthority, and some just plain don't work (*sudo kate*, for example).

---

### Post by nanotube on 2006-06-05
[QUOTE=aysiu]Thanks for the clarification. I do know that certain graphical applications do mess up the .ICEAuthority, and some just plain don't work (*sudo kate*, for example).[/QUOTE]

hmm... i'd really like to know the details behind the differences between sudo and gksudo/kdesu. haven't found any nuts-and-bolts documentation for it so far, though. if you find something like that, make sure to send me a link :)

---

### Post by aysiu on 2006-06-05
[QUOTE=nanotube]hmm... i'd really like to know the details behind the differences between sudo and gksudo/kdesu. haven't found any nuts-and-bolts documentation for it so far, though. if you find something like that, make sure to send me a link :)[/QUOTE] Yeah, the closest I could find is this:
[http://www.nongnu.org/gksu/](http://www.nongnu.org/gksu/)

Unfortunately, it's not very detailed.

---

### Post by nanotube on 2006-06-05
[QUOTE=aysiu]Yeah, the closest I could find is this:
[http://www.nongnu.org/gksu/](http://www.nongnu.org/gksu/)

Unfortunately, it's not very detailed.[/QUOTE]
hmm, well, it's a start. ;)

---

