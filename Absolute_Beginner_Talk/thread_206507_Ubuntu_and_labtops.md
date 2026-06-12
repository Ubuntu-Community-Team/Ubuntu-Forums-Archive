---
title: "Ubuntu and labtops"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by csk on 2006-06-30
hi all
i just installed ubuntu on my labtop and found that i have 3 main problems. 

everytime i go into synaptic update manager i get 

"Warning"
"The following problems were found on your system"

"W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)"

everytime i log on i have to go to network settings and manually active my wireless connection by going into properties and highlighting "network name (ESSID)" to WLAN (its always blank by default) then cliicking active.

also i cant seem to get my numlock key to be off by default. 

can anyone please help 

thanks heaps 
csk

---

### Post by cowley on 2006-06-30
hi, try downloading automatix - there is a program there which will allow u to turn off/on num lock and some wifi managers too.  or try using network manager

simon

---

### Post by Jagot on 2006-06-30
The stuff to do with Synaptic is that it's trying to search for your install cd rather than just downloading from the repos.  In your sources.list you should have a couple of lines that go something like this:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20060531)]/ dapper main restricted
```

You can comment those out by putting a hash before them - #.

Or you could do it the graphical way as described here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Someone may be able to help you with the other stuff but to be honest you may want to try upgrading to the latest version of Ubuntu, Dapper Drake 6.06 as it may sort out some of those problems.

---

### Post by JoshHendo on 2006-06-30
It is weird that it is trying to connect to the CD rom. You must have added it by putting the Cd in and telling it to add.

Upgrading should also help as Jagot said.

Also, im assuming you mean laptop not labtop?

---

### Post by csk on 2006-06-30
[QUOTE=JoshHendo]

Also, im assuming you mean laptop not labtop?[/QUOTE]

lol #-o  my bad:P

u guys were right installed the new 6.06 and everything works fine 
thanks heaps

csk

---

