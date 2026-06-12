---
title: "How do I reverse this? To uninstall?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by SMF on 2006-02-18
This was the command to install.

sudo apt-get install j2re1.4

I installed it but now I want to un-install it.

Can any one tell me the correct code:)

Thank you.

---

### Post by codejunkie on 2006-02-18
[QUOTE=SMF]This was the command to install.

sudo apt-get install j2re1.4

I installed it but now I want to un-install it.

Can any one tell me the correct code:)

Thank you.[/QUOTE]
```
sudo apt-get remove --purge j2re1.4
```

---

### Post by SMF on 2006-02-18
Thank you. I would of never guessed that one :mrgreen:

---

### Post by prizrak on 2006-02-18
You can also use the Synaptic Package Manager, makes it a bit simpler :)

---

### Post by unbutuju on 2006-02-19
Hi all
amasing X tool this Synaptic Package Manager I have tryed it already with all the features and its a great "add remove" programs for those like me with very small experience on the commands you should explore the Synaptic Package Manager its a great tool!

I am liking it more and more day after day the ubuntu of course!

---

### Post by SMF on 2006-02-19
> 
Hi all
amasing X tool this Synaptic Package Manager I have tryed it already with all the features and its a great "add remove" programs for those like me with very small experience on the commands you should explore the Synaptic Package Manager its a great tool!

I am liking it more and more day after day the ubuntu of course!
__________________



Amazing X is some kind of tool?

?

---

### Post by mostwanted on 2006-02-19
No, synaptic.

System -> Administration -> Synaptic

Or just type
```
gksudo synaptic
```
in the terminal.

---

### Post by SMF on 2006-02-19
Ok thank you Mono :mrgreen: 
I found it. That is a very great tool and thanks to this thread I was able to learn a little more.

Very nice;)

---

### Post by SMF on 2006-02-19
BTW when I do run the synaptic i get this following error.

Should I be concernd?

W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by codejunkie on 2006-02-19
[QUOTE=SMF]BTW when I do run the synaptic i get this following error.

Should I be concernd?

W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)[/QUOTE]
this could mean that either the repo is down at the moment or the entry is wrong in your sources.list file if it worked before using apt-get id bet the repo is just down.

---

### Post by kvorion on 2006-02-19
By the way, do remember to run
```
apt-get update
```
from time to time in order to keep the list of available software up to date.

```
man apt-get
``` to read more about apt-get

---

### Post by SMF on 2006-02-19
[QUOTE=kvorion]By the way, do remember to run
```
apt-get update
```
from time to time in order to keep the list of available software up to date.

```
man apt-get
``` to read more about apt-get[/QUOTE]

ok kvorion I entered the 
```
apt-get update
```
into my Terminal and it open and closed real fast so I am assuming this is the same thing as the update manager in my System/Administration/Update Manager.
? Which by the way says that I am up to date when using the 
System/Administration/Update Manager.

And then this is why the terminal open and close and I saw nothing because these are two ways of getting to the same software updater?

:-k

---

