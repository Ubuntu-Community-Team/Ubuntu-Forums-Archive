---
title: "[SOLVED] Thunderbird, can downoad it, can unpack it, but...."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by bmann11 on 2008-04-18
can't install it.  Any help for a newb such as myself?  Thanks, Bmann

I'm running 7.10 and trying to install T-bird version 2.0.0.12 for Linux i686.

---

### Post by ACMarina on 2008-04-18
How are you downloading it??  Directly from Mozilla??

---

### Post by bmann11 on 2008-04-18
Yes, direcetly from Mozilla.  tried to install it via add/remove but got an error message.

---

### Post by SunnyRabbiera on 2008-04-18
you do not download from random sites like in windows, instead you can install thunderbird in the repositories by using an app called synaptic or add/remove.
synaptic is under system>administration>synaptic
and add/remove is perfectly visible under applications.
for now you can use add/remove until you get used to things, open it up and search for thunderbird, installing it is very straightforward.
as for any error messages, what error message did you get?

---

### Post by bmann11 on 2008-04-18
The message reads:

"Mozilla Thunderbird Mail/News cannot be installed on your computer type (i368)

Either the application requires special hardware features or the vendor decided not to support your computer type."

---

### Post by ACMarina on 2008-04-18
Did you try to install via synaptic, as was suggested??

It's not like Windows, where you just download the file and double click to install.  You can install files in that fashion, but it's more complex to do it that way, simply because linux (on the whole) asks for more information to customize the system to your liking..

To just install it without having to do that, you just use synaptic..

---

### Post by forrestcupp on 2008-04-18
open a terminal and type
```
uname -r
```and post the output.  This will tell us which kernel you are using.

What kind of processor does your computer have?  

Also in the terminal, type
```
sudo apt-get update
sudo apt-get install thunderbird
```and tell us what the output is there.

---

### Post by bmann11 on 2008-04-18
it doens't show up under synaptic.

---

### Post by forrestcupp on 2008-04-18
> **bmann11 said:**
> it doens't show up under synaptic.

please do what I said in my last post.  I'm sure we can get it working.

---

### Post by bmann11 on 2008-04-18
first command output is:

2.6.22-14-generic

My processor is a pentium 1.6

Second command output reads:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate

---

### Post by stchman on 2008-04-18
> **bmann11 said:**
> can't install it.  Any help for a newb such as myself?  Thanks, Bmann

I'm running 7.10 and trying to install T-bird version 2.0.0.12 for Linux i686.

For Gutsy or later distro Thunderbird 2.0.0.12 is in the repos.  For Feisty or earlier I have a script that installs Tbird.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

It is in the Scripts section.

The Thunderbird you download from Mozilla's website is a precompiled binary.  If you wish to get the source and built it you will need to go to the developers area.

---

### Post by ACMarina on 2008-04-18
Did you do the 

sudo apt-get update

line??

Edit - missed that script post just before mine..

---

### Post by bmann11 on 2008-04-18
sudo apt-get update output

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done

---

### Post by bmann11 on 2008-04-18
How do I access thunderbird in the repos?

---

### Post by ACMarina on 2008-04-18
Well, if you ran that script and everything worked properly, you should be able to find the version of thunderbird you need in synaptic or by using "apt-get"..

---

### Post by jocko on 2008-04-18
> **bmann11 said:**
> sudo apt-get update output

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done

It looks like you don't have all the repos activated.
Go to System --> Administration --> Software Sources.
[B]
Absolutely necessary:[/B] In the first tab, make sure the top four checkboxes are checked (the lines ending with "(main)", "(universe)", "(restricted)" and "(multiverse)").

**Not absolutely necessary**, but still recommended to fix bugs and security issues: In the third tab (Updates..) activate the top two (security and updates).

Close software sources, let it reload the package information and open up synaptic again. Now you should find thunderbird (and probably a lot of updates).

---

### Post by bmann11 on 2008-04-18
That did it.  Thanks.  These forums are great.

---

