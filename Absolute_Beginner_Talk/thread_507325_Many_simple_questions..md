---
title: "Many simple questions."
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by {A}Poly on 2007-07-22
[B]1)  Is there a way to upgrade to a newer version of Ubuntu withought restarting everything. I have Ubuntu 6.06 and want to upgrade, How do i upgrade withought a CD.

2) I want to install wine, But many parts in the instructions, don't make any sense to me. Here are the instructions : [/B]

[I]First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
 
For Ubuntu Edgy (6.10): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list

Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'.
[/I]

WALK ME THROUGH THIS, I have no idea how to do stuff like "add the repository to your system's list of APT sources:", I am compleatly new to Linux. 

please help.

and lastly, I appologize to everyone in the world for getting linux and not knowing how to do  anything properly, and wasting all of your presious time by posting here. Sorry.

:confused:

---

### Post by mevets on 2007-07-22
If terminal commands prove too hard, just let Automatix install it for you. Visit [www.getautomatix.com](www.getautomatix.com)

---

### Post by Malibu Illusion on 2007-07-22
1) Covered by Google, I'll let someone else waste their time answering this if your're not going to go there.

2) Read the instructions?  The command line code for adding the necessary repositories are staring you directly in the face.  Look for your Ubuntu version, copy and paste the line under it into a terminal.  Couldn't be simpler.  What you have there is already a walk-through.

Btw, suggest ignoring the above poster talking about Automatix.  Learn how to install things the correct way to avoid issues.

Take care.

---

### Post by p_quarles on 2007-07-22
1) Don't install Automatix. 

2) Ignore Malibu Illusion. That kind of post is not appropriate for this forum. For beginners who don't know what a repository is, much less how to add one, google isn't much help. Frankly, I'm not sure why he/she responded to your question in the first place.

Okay: First, I think it's better to reinstall the system when you upgrade. Backup your personal files to other disks, make notes about which packages you have installed, and then install the latest version. If you can't do this, I'll try to find a link that guides you through the automatic version upgrade process. Just be forewarned that it can be buggy.

Second, you can edit your repositories this way(open a terminal and type):```
gksudo gedit /etc/apt/sources.list
```
Wine is available in the main repositories, so you don't actually need to add anything. Just make sure that you remove any # symbols in front of lines beginning with "deb". Then, go back to the terminal, and type: ```
sudo apt-get install wine
```
Just so you know, though, wine is pretty difficult to use, and should be avoided if you can find an equivalent Linux program.

---

### Post by pearlie on 2007-07-22
Alrighty then, I'll give it a shot.

Firstly, don't apologize for not knowing how to do stuff in Ubuntu - everybody was new to this once.  It's like learning how to ride a bike - strange and wobbly at first, then easy and natural after a while.  It really doesn't take very long before you'll feel confident.

Okay... upgrading without a CD is pretty straightforward.  **Back up all your personal data first** - you don't want to lose stuff permanently if things go wrong.  Open up a terminal - that is, go to Applications -> Acessories ->  and click on Terminal.  This opens your Command Line Interface - or 'CLI'.  When the box appears, type in (or copy and paste) the following:

```
gksu "update-manager -c"
```

The Update Manager will open up and give you an option to upgrade to the next available version.  Click on that option, and follow along as the universe unfolds in a gentle and obvious way.  It will take a while, so make sure you have some time set aside.   Please note that you can only step up one version at a time with this method - from Dapper (6.06) you'll go to Edgy; then, if you want, you can to it again go from Edgy to Feisty.

Don't bother messing with Wine until you've done your upgrade.  Let us know how it works out for you.


Edit:  Oops!  tooke me too long to type this, I got sniped.

---

### Post by dhughes on 2007-07-22
Keep in mind folks this is the **Absolute Beginner** section of the Ubuntu Forum. No need to be snippy. "Just Google it" is no help, you may as well say nothing.

---

### Post by lisati on 2007-07-22
> **pearlie said:**
> Alrighty then, I'll give it a shot.

Firstly, don't apologize for not knowing how to do stuff in Ubuntu - everybody was new to this once.  It's like learning how to ride a bike - strange and wobbly at first, then easy and natural after a while.  It really doesn't take very long before you'll feel confident.


In some ways it's like adjusting to a new car where the layout of the controls is different to what you had before - there will be some things you'll be able to use from your previous experience, and some things that might take a little learning but will be worth the effort.

---

### Post by {A}Poly on 2007-07-22
thanks a lot everyone. I will try out all of these.

---

### Post by KyleBrandt on 2007-07-22
{A}Poly:  If you have no luck with wine, I would recommend giving virtualization a try.  There is a package in the repositories, Virtualbox, which is free and works really well.  You can run windows on top of your ubunutu installation for any windows needs, and all current windows software should work fine as long as your are not too tight on system resources.

---

### Post by Immolatus on 2007-07-22
I think I recall them saying (when feisty was released) that dapper users would be able to upgrade via the "upgrade distribution" button in the update manager when Gusty is released in September.

In a sense LTS --> LTS, skipping all the distros in between. Just a thought.

---

### Post by pyros on 2007-07-23
wine has been covered here already, but since I just had to upgrade a box from dapper to feisty, I thought I would chime in.

the official docs covering this are here:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
and I would recommend
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

essentialy, when upgrading, it's not advisable to jump a release. So, for example, its ok to go from dapper to edgy to feisty, but not from dapper to feisty directly. Although, (and I haven't tried this, mind you) you can try downloading the alternate install cd, burning it, mounting it (not booting off of it), and running the command: 
```

gksu "sh /cdrom/cdromupgrade" 

```

I did it, from dapper, by running:
```

gksu "update-manager -c" 

```
that adds a button to the update manager that lets you upgrade to edgy, after doing that, I did the same to update from edgy to feisty.

---

