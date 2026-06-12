---
title: "Installing Packages"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by prospero96 on 2008-02-02
I'm a complete novice new to Ubuntu 7.10.
I've downloaded a tar.gz package to the desktop.
Adept Manager tells me I do not have administrator privileges.
In Archive Manager the package is greyed out.
I don't understand how to use the terminal.
All help would be appreciated.

---

### Post by Rocket2DMn on 2008-02-02
For installing programs, most of the stuff you will want can be found in Ubuntu's repositories.  That means you can install in any number of ways, but the two most popular:
1) go to System->Administration->Synaptic Package Manager and search for the program you want to install
or 2) open a terminal and run
```
sudo apt-get install *programname*
```
The use of "sudo" gives you administrator/root privileges for that command

Also, check this out: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by erfahren on 2008-02-02
a tar.gz package (unless it is a theme or something) would most likely be the program source code and would need to be compiled.

what exactly is it?

it's odd that you wouldn't be able to decompress it - how was it downloaded, just with Firefox from the internet?

you can check the ownership permissions of the archive by right-clicking on it "Properties" > "Permissions" tab - if it says it is owned by root you can change that by:

open a terminal (Applications > Accessories > Terminal) and first change directory to the Desktop

(the Desktop is a subdirectory of your /home/<username>  (the terminal session opens to your /home/<username> directory - also just written as "~/" ) - so
```

cd Desktop

```
then list the contents (you'll see why)
```

ls

```
now - to change ownership of the package do this (just copy and paste the name of the package where it goes) - and use your correct username of course (the colon is important)
```

sudo chown prospero96:prospero96 *name-of-archive*

```
then you should be able to right-click on it to extract it.

more info on the terminal
[Terminal for Beginners](http://ubuntuforums.org/showthread.php?t=73885)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[Know Your Terminal Commands, Terminal references](http://ubuntuforums.org/showthread.php?t=171507)

---

### Post by mcduck on 2008-02-02
This guide is actually made for Gnome desktop, but as the main things are the same you should probably read through it even if you are using KDE yourself: [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by prospero96 on 2008-02-02
Thanks all, you've given me a start. :)
I'll let you know how I get on.
The package was OpenOffice 2.3.1.

---

### Post by erfahren on 2008-02-02
> **prospero96 said:**
> Thanks all, you've given me a start. :)
I'll let you know how I get on.
The package was OpenOffice 2.3.1.
ok, yep - OpenOffice you'd really be better off just installing from the repositories (through Synaptic Package Manager - just search it)

OpenOffice is a large complex program - compiling it would be a little advanced (i'd sure avoid doing it - even if it was a newer version. It's gets updated pretty well in Ubuntu though).

good luck:)

---

### Post by prospero96 on 2008-02-03
The original download was:

OOo_2.3.1_071207_LinuxIntel_install.tar.gz downloaded to the desktop.

I've managed to extract it to the desktop as a folder: en-US

I can't get it into Synaptic Package Manager and Add/Remove programmes tells me I don't have rights even though I've set up permissions in system > admin > users.

Sorry to be a jessie, but I'm still stuck.

---

### Post by erfahren on 2008-02-03
> **prospero96 said:**
> 
I can't get it into Synaptic Package Manager and Add/Remove programmes tells me I don't have rights even though I've set up permissions in system > admin > users.

when you open Synaptic what happens exactly? It should just ask for your password.

if you get an error message could you post the wording (or just Alt+PrtScrn and post the screenshot - just attach it to your post).

---

### Post by prospero96 on 2008-02-03
I didn't explain myself very well, I can get into Synaptic, I can't get the Package into Synaptic (it's sitting on the desktop at the moment)

---

### Post by jan quark on 2008-02-03
installing packages via synaptic
what to do:

open synaptic

open the search field

type in the name of the package you want to install

here type open office

click on the box next to the open office package

mark to install 

click on apply

you don not drag and drop packages into synaptic, either they are there or you you to install it differently but try as depicted above

---

### Post by erfahren on 2008-02-03
> **prospero96 said:**
> I didn't explain myself very well, I can get into Synaptic, I can't get the Package into Synaptic (it's sitting on the desktop at the moment)
oh -- what I meant by installing through Synaptic is that you search Synaptic for the program - then check it to install. Synaptic then downloads it and automatically installs the program. [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

You can't really do anything with that package you downloaded from OpenOffice.org - it's a tar.gz package and just contains the source code of the program - it would need compiled. That's done manually.

exactly what version of Ubuntu are you using?

---

### Post by prospero96 on 2008-02-03
Thanks Jan,

Synaptic is showing OO version 2.3.0.
I have downloaded v.2.3.1 to the desktop and wish to install it from there.
This is my problem.

---

### Post by erfahren on 2008-02-03
> **prospero96 said:**
> Thanks Jan,

Synaptic is showing OO version 2.3.0.
I have downloaded v.2.3.1 to the desktop and wish to install it from there.
This is my problem.
**compile it then!** 

It will most likely be updated in Ubuntu soon, I've already said that.

---

### Post by prospero96 on 2008-02-03
> **erfahren said:**
> You can't really do anything with that package you downloaded from OpenOffice.org - it's a tar.gz package and just contains the source code of the program - it would need compiled. That's done manually.

This is starting to make sense.
I'm using Ubuntu Gutsy Gibbon 7.10.

---

### Post by jan quark on 2008-02-03
do you really need the newest OO now?:)

compiling such a big package like open office from scratch is connected with many issues and takes a long time, it might be very complicated

the changes are not so big from 2.3.0 to 2.3.1

I would just use the package which is listed in synaptic

because the installation is very easy and painless compared to the compiling process

---

### Post by prospero96 on 2008-02-03
A big thank-you to all who tried to help.
I'll wait until the "upgrade" appears.
I think we can close this thread now.

---

### Post by erfahren on 2008-02-03
ok --

I guess I should mention this, Linux isn't like Windows where you need to go out and fetch the updated version of a program on your own and install it, especially with the included software like Openoffice. 

That's one of the advantages of Ubuntu and other Linux distros that use a package manager. The updates for programs installed through it are updated by Ubuntu along with the system updates.

In short - always check the Ubuntu repos (through Synaptic) first. If the version of the program is unacceptable (or it's not in there at all) then try get it another way. There are occasions where you may definitely want or need to go out and get a newer version of a program from elsewhere. You'd first try to get a .deb package of it and only compile it if there was no other way.

---

### Post by jan quark on 2008-02-03
please mark this thread as solved if it is solved for you
use thread tools at the top of the page 
thank you

---

