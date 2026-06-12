---
title: "Broken software index HELP!!!"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Copperteeth on 2007-01-13
Messed up my software index some how. Not sure what i did wrong? Firs off before i continue i should mention im using a custom source.list that if needed i can provied. i compiled it using source-o-matic and some other reccomended souces from hardcore ubuntu friends.

It started off when I kept ketting this update error from software updates, for wpasupplicant which i figured i didnt need as i dont have a wireless card nor do i plan to get one in the future so i removed it through the synaptic pachage manager. Biggest mistake i made. The uninstallation gave/gives me the error when i applyed the uninstall for it:

> E: wpasupplicant: subprocess post-removal script returned error exit status 10

ok, not sure what that means, maby its not a problem, WRONG! The software updater keeps running trying to update wpasupplicant (which afaik its uninstalled but with errors) but now for some reaon when software manager runs i get this error

> It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

so i go to termainal (which is my favourite part of linux btw, no joke i actully find joy in typing in commands :D :cool: ) and type in sudo apt-get install -f, and it replys with this message:

> Reading package lists... Done
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

> E: /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu0_i386.deb: there is no script in the new version of the package - giving up


... this is getting annoying, now software manager is poping up again, maby somthing is working even though i got an error. Nope same old message, sotfware update is broken, still gotta run apt-get install -f which at this point wont work. need some help!


Also on a completly unrelated topic which i will fix probably later myself, kiba-dock wont start for me and it crashes a lot for some reason? This problem isnt much of concern right now but if i can get 2 birds with one stone, awesome!

---

### Post by Tomosaur on 2007-01-13
You cannot use apt-get or aptitude from the command line while synaptic is open. You must first close synaptic, and then run the apt-get command.

---

### Post by Copperteeth on 2007-01-13
ok now i closed all that junk that i stupidly left open and sudo apt bla bla bla and i got this error still:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wpasupplicant
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wpasupplicant
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 692kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 136280 files and directories currently installed.)
Removing wpasupplicant ...
dpkg: error processing wpasupplicant (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 wpasupplicant
E: Sub-process /usr/bin/dpkg returned an error code (1)


still broken...

---

### Post by Tomosaur on 2007-01-13
Try the following command:
```

sudo aptitude purge wpasupplicant

```

---

### Post by Copperteeth on 2007-01-13
for a second there i had hope, stupid wpa crap!

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  wpasupplicant{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 692kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 136280 files and directories currently installed.)
Removing wpasupplicant ...
dpkg: error processing wpasupplicant (--purge):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 wpasupplicant
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


---

### Post by in_flu_ence on 2007-01-13
i got exactly the same issue.

For me as i have posted in my post, i had vmware installed previously which I didn't know if that will complicate things on this.

---

### Post by jvc26 on 2007-01-13
```

sudo apt-get --purge remove wpasupplicant

```
Does this end up the same way as tomosaurs (it may well be just another way of writing tomosaur's method)
Il

---

### Post by Copperteeth on 2007-01-13
we gotta fix this issue, i need my updates!!! ](*,)

---

### Post by jvc26 on 2007-01-13
Have you done the 
```

sudo apt-get install -f

```
Since you closed synaptic (just in case?)
Il

---

### Post by Copperteeth on 2007-01-13
yes i have, but ill do it again
that was the first thing i tried

---

### Post by in_flu_ence on 2007-01-13
Yes i got the exact same error. Probably I didn't paste enough of mine in my last post.

and i probably have done exactly as Copperteeth and did the purge thingy.

I suppose something is broken in the package indexing (or along those line) where the repos are not binded well.

Appreciated.

---

### Post by jairo.serrano on 2007-01-14
i simple comment all the content of 
/var/lib/dpkg/info/wpasupplicant.postrm

and unnistall the package...

Dirty and ugly solution...

---

### Post by arnieboy on 2007-01-14
A couple of comments:
1) The package has a broken postrm file and it can be removed by doing:
```
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
```
followed by a regular apt-get  update.
2) > deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0 is home to many broken Ubuntu packages. Please do not use this repository. It will result in more breakages and malfunctioning software.

---

### Post by Copperteeth on 2007-01-14
> **arnieboy said:**
> 
2)> deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
is home to many broken Ubuntu packages. Please do not use this repository. It will result in more breakages and malfunctioning software.  is home to many broken Ubuntu packages. Please do not use this repository. It will result in more breakages and malfunctioning software.

ok thanks, everything is working now

one more question though, on my source.list i have the following:
> #TREVOR
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

so should i stop using things from tuxfamily then? i # everything out but what would someone reccomend to replace those repositorys that i shouldnt use?

---

