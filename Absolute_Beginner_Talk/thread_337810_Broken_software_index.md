---
title: "Broken software index"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2007-01-13
This is a repost of my problem that never got solved,

Messed up my software index some how. Not sure what i did wrong? Firs off before i continue i should mention im using a custom source.list that if needed i can provied. i compiled it using source-o-matic and some other reccomended souces from hardcore ubuntu friends.

It started off when I kept ketting this update error from software updates, for wpasupplicant which i figured i didnt need as i dont have a wireless card nor do i plan to get one in the future so i removed it through the synaptic pachage manager. Biggest mistake i made. The uninstallation gave/gives me the error when i applyed the uninstall for it:

> E: wpasupplicant: subprocess post-removal script returned error exit status 10
ok, not sure what that means, maby its not a problem, WRONG! The software updater keeps running trying to update wpasupplicant (which afaik its uninstalled but with errors) but now for some reaon when software manager runs i get this error

> It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
so i go to termainal (which is my favourite part of linux btw, no joke i actully find joy in typing in commands ) and type in sudo apt-get install -f, and it replys with this message:


R> eading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
wpasupplicant
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
wpasupplicant
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
seems to me something is broken lol? Uh the next thing i tried was to reinstall wpasupplicant because i figured maby somthings left behind and if i re-remove it all will go well, so i did. Got this message

> 
E: /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu0_i386.deb: there is no script in the new version of the package - giving up
... this is getting annoying, now software manager is poping up again, maby somthing is working even though i got an error. Nope same old message, sotfware update is broken, still gotta run apt-get install -f which at this point wont work. need some help!

Things that have been suggested that i tried:

Synaptic Package manager is NOT running when i am in terminal
sudo aptitude purge wpasupplicant does not work

---

### Post by useResa on 2007-01-13
The error you are indicating "/var/cache/apt/archives/lock - open" is also being reported in a thread called [Update Manager Problems](http://www.ubuntuforums.org/showthread.php?t=304550).

Maybe the solution that is indicated in this thread may also help you solve your problems.
Good luck and hope it helps.

---

