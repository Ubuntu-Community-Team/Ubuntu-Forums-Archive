---
title: "Can I have a moan please about deleting files."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-24
I think I feel a moan, gipe, complain coming on, so where best to post it ;)

Now, I fully understand there had to be protection on just wading into folders deleting icons/programs without knowing what you are doing.

And also for security reasons too.

But, (and I'm sure many, no make that ALL people who are new to Linux) find it annoying that you can't delete what you want without (it seems) a fight.

Now, perhaps this (from my point of view) would be the ideal.

Say, I browse to a folder, and find a file, I know I don't want and don't need.
Currently I'm told I don't have permission to move to trash.

Would it not be more helpful, to have a warning box pop up questioning the deletion, and offering you that can type in your password to allow deletion for this file if you are sure.

Would that not be good?

Tis just an idea?

Well, it would be helpful to me anyway!

And on this very note:

How do I delete a folder called swiftdove in /usr/local ?

From the gui file browser, there is not even the option to delete is, password or not.

Not yet being up to speed with terminal commands, I'm not sure about this.

I would love the ability to delete something like this from the graphical gui method, even if I have to enter my password to do it.

---

### Post by forestpixie on 2008-02-24
you can open nautilus with root rights

gksudo nautilus

be aware that it'll get deleted into root's trash - so it won't appear in yours, and regardless of rights if you delete a hidden file - it will appear in trash as hidden

and be careful when you're in nautilus with root rights

---

### Post by PiggiePaul on 2008-02-24
> **forestpixie said:**
> you can open nautilus with root rights

gksudo nautilus

be aware that it'll get deleted into root's trash - so it won't appear in yours, and regardless of rights if you delete a hidden file - it will appear in trash as hidden

and be careful when you're in nautilus with root rights

Excellent.

Many thanks for that. That's one of the most useful bits I've found out :)

I was being reminded about Vista's problem where it won't allow you delete things!

I know it's all about security, it's just annoying that you can see what you don't want and yet you are not allowed to delete something.

Again, many thanks.

If I make my system bomb out through using it, I'll only have myself to blame :D

I just get annoyed when I remove a program, and there are bits left when I do a search.

---

### Post by llamakc on 2008-02-24
When you start deleting files that are placed in the filesystem by the package management system you ARE ASKING for trouble, unless you truly know what you are doing.

Any files in your /home/USER directory should already be deletable by you.

Perhaps I am not understanding why you want to do this. Please provide one example.

EDIT: Just caught this in your post above: >  I just get annoyed when I remove a program, and there are bits left when I do a search..

That's the way it works. If you want to completely remove all files associated with a package that option exists in all of the package management front ends.

2nd EDIT: I see that you wanted to remove something in /usr/local. HOW did you install it?

---

### Post by glennric on 2008-02-24
swiftdove is the optimized build of thunderbird.  Try uninstalling the package swiftdove and that should get rid of it.  Also, if you could install "apt-file" and if you find a file you think you don't need try
```
apt-file search filename
```
and it will tell you which package (if any) the file belongs to.  Then if you don't need that package you can uninstall it.

---

### Post by PiggiePaul on 2008-02-24
Ok.... More details

Firstly, I do stand by my (little rant) that if I want to delete a file, I get a tad annoyed about a message that says I can't delete it and not give me any option to override this.

Much in the same way that you might start a washing machine cycle, then find you have left 1 sock out and the machine won't let you re-open the door to put the sock in, cos it know better than you, even though the water is no-where near the door level, it will just refuse to open.

Hey door, I own the dam machine now open!

he he....... (just a pet annoyance) :D

Anyway, back to this.

Ok, after much reading, I installed SwiftDove, and found it to have some very in your face bugs/faults/issues. Main parts of the program had graphical problems.

So, decided, it would be easier to just bite the bullet and go with Thunderbird.

SwiftDove was installed from their site (as could not see it thru the synaptic package manager)

So, (as I said) downloaded the suggested version from their site, which was a self installing .deb file version.

It installed and all was fine.

Just in case I wanted to remove it, I took a copy'n'paste from the output window of all the files that installed:

Here's a sample from the start of the list:
[COLOR="Blue"]
./
usr/
usr/share/
usr/share/applications/
usr/share/applications/swiftdove.desktop
usr/share/doc/
usr/share/doc/swiftdove/
usr/share/doc/swiftdove/mozilla-firefox.js.tmpl
usr/share/doc/swiftdove/changelog.Debian.gz
usr/share/doc/swiftdove/README.txt.gz
usr/share/doc/swiftdove/swiftdove-compose
usr/share/doc/swiftdove/copyright
usr/share/doc/swiftdove/README.Debian.gz
usr/share/man/
usr/share/man/man1/
usr/share/man/man1/swiftdove.1.gz
usr/local/
usr/local/bin/
usr/local/bin/swiftdove
usr/local/swiftdove/
usr/local/swiftdove/defaults/
usr/local/swiftdove/defaults/autoconfig/
usr/local/swiftdove/defaults/autoconfig/platform.js
usr/local/swiftdove/defaults/autoconfig/prefcalls.js
usr/local/swiftdove/defaults/wallet/[/COLOR]

As I said, upon trying this (and it did physically work) it had some glaring graphical problems I think mainly to do with the built in Calendar side of things.

So, thought there's no point carrying on, I'll just to what I should have done and gone with Thunderbird.

Did a read from these forums about how to remove .deb packages and read that they would be in Synaptic and to use this to remove them, which I did.

Yes, Swiftdove did show in Synaptic and I selected a full uninstall, which it did.

I checked the output window and it said there were bits it did not remove :confused:

Upon doing some searching (Thanks to Catfish) I found there were some Swiftdove Icons left in: usr/share/pixmaps

And a whole Swiftdove folder (with 3 sub folders) in /usr/local

None of which were removed by Synaptic, and they were not there before I installed Swiftdove.

So call me wreckless, but I've gone into them (checking with my original cut'n'paste copy of what was installed) and physically taken them out.

Perhaps there was a better way to have REALLY uninstalled everything, that using Synaptic to do the uninstall?

Perhaps that was my mistake?

I just didn't want Swiftdove folders still on my system (which were not there before I installed it) sitting there for eternity.

If I could have gone about this a better way I'd like to know for future .deb installs.

---

### Post by glennric on 2008-02-24
Try
```
sudo apt-get remove --purge swiftdove
```

Edit:  Didn't read your post carefully.  If you have added other files to those directories after installing swiftdove then those files will not be removed by the uninstall process.  It assumes you know what you are doing and doesn't delete something you did.  You will have to manually delete those files.  If you install with a deb, don't manually make modifications to the installation, and use the above command, everything will be removed.

---

### Post by bodhi.zazen on 2008-02-24
I think permissions are an adjustment when migrating from other OS that do not user them. After a while they start to make sense. 

Obviously they both increase security and protect you from yourself.

If you want to run a root shell, use :

```
sudo -i
```

If you want a gui, use ```
gksu nautilus
```

Take care with those ...

---

### Post by PiggiePaul on 2008-02-24
> **glennric said:**
> Try
```
sudo apt-get remove --purge swiftdove
```

Edit:  Didn't read your post carefully.  If you have added other files to those directories after installing swiftdove then those files will not be removed by the uninstall process.  It assumes you know what you are doing and doesn't delete something you did.  You will have to manually delete those files.  If you install with a deb, don't manually make modifications to the installation, and use the above command, everything will be removed.

Well, I guess what could happen is:

I installed Swiftdove.

If you look towards the bottom of the [COLOR="Blue"]**BLUE** [/COLOR] file list above, you will see it made (and put stuff in) a folder called /usr/local/swiftdove

Now, (perhaps this is how it works)

I ran Swiftdove and all I did was set up my email account, and downloaded an email.

Not sure where this data went, but if a program makes MORE files, and puts them into the same folder it made during installation.

Then you wish to do a full uninstall. the fact that there a new files in the folders (that were not there during the initial install) will that mean that the uninstall will refuse to remove those folders?

I'm sure like me, if you wanted to remove Swiftdove from your system, you would not want Swiftdove folders, icons and data that it created when it was run still hanging around.

I don't normally make a note of the files that go ON during installation, or check the terminal output after removal to see what's left behind.

It's just one of those gripes that I (and I know many) had about Windows filling up with junk over time as things get left behind, and over time you can get more and more junk in the system, and have to try some scanning software to find things that are no longer needed.

On that subject, is there anything we can use ubuntu/linux that does a kinda system scan to remove unwanted and no-longer used bits and pieces.

I suppose I'd like things to all be in 1 folder, so you remove the folder and everything goes. But perhaps that's not a practical way to do things these days?

---

### Post by glennric on 2008-02-24
Did you by chance install swiftdove first using some other method?  If installed from a deb (or via apt-get or synaptic) then when you uninstall it will remove all of those files that you are talking about.  The settings that are added when you run the program are stored in a hidden directory in your home directory, and not in the install directory.  That won't affect the unistall.

---

### Post by Black Market Baby on 2008-02-24
If you ran ubuntu as root all the time, then you could delete anything you wanted and change permissions on anything without having to open up a root terminal to do it. 

But then you'd be throwing away a lot of safety and also setting yourself up for unintentionally damaging stuff you shouldnt be messing with. 

What are you are moaning about is a feature that most linux users like. And you can avoid that feature if you choose to do so. So the choice is yours really.

---

### Post by PiggiePaul on 2008-02-24
> **Black Market Baby said:**
> If you ran ubuntu as root all the time, then you could delete anything you wanted and change permissions on anything without having to open up a root terminal to do it. 

But then you'd be throwing away a lot of safety and also setting yourself up for unintentionally damaging stuff you shouldnt be messing with. 

What are you are moaning about is a feature that most linux users like. And you can avoid that feature if you choose to do so. So the choice is yours really.

Yeah, I realize about the dangers of root.

I suppose all I'm really asking for it:

If you DO know what you want to remove, you can go into the terminal with a SUDO command and after entering your password you can delete the files.

I guess, I'd like (and I guess it could be done very easy) is the same kind of security but in the GUI file manager, so if you browse say 5 folders deep and find something you wish to remove (the icon of a file) I'd like to be able to "Whilst I'm there looking at it) Enter my password and be given the rights to delete it.

Perhaps right clicking and there could be an option.

Or, when you try and delete, you get a pop up message that says you don't have permission to delete. Within this message could be an OVERRIDE button, where you can enter your password.

I'm not really asking for any less security that you have at the moment, just an easier way to over ride it, whilst browsing, rather than, having to go back to the terminal, enter your password there, and then browse back to where you were.

Just an ease of use thing.

Hopefully it's not something I'll need to use much anyway :)

---

### Post by Black Market Baby on 2008-02-24
Maybe there could be an option where you right-click and choose "open root terminal in this directory"

---

### Post by arekkusu on 2008-02-24
PiggiePaul: I pretty sure the behavior you want will be in the next Ubuntu version with the "policy kit" and new GVFS...

Take a look at the alpha version page for Hardy: [http://www.ubuntu.com/testing/hardy/alpha5](http://www.ubuntu.com/testing/hardy/alpha5)

:)

---

### Post by wolfen69 on 2008-02-24
a couple of other things you can run to insure a clean system are:
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```
these will get rid of any unused dependencies and such.

---

### Post by PiggiePaul on 2008-02-24
> **wolfen69 said:**
> a couple of other things you can run to insure a clean system are:
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```
these will get rid of any unused dependencies and such.

Thanks for that.

The second command came up with:
[COLOR="Blue"]
The following packages were automatically installed and are no longer required:
  liblzo1 python-qt3 python-sip4
The following packages will be REMOVED
  liblzo1 python-qt3 python-sip4[/COLOR]

You sure I don't need that?
I recall reading about python in some posting about various things.

I've said NO at the moment by the way

---

### Post by PiggiePaul on 2008-02-24
> **arekkusu said:**
> PiggiePaul: I pretty sure the behavior you want will be in the next Ubuntu version with the "policy kit" and new GVFS...

Take a look at the alpha version page for Hardy: [http://www.ubuntu.com/testing/hardy/alpha5](http://www.ubuntu.com/testing/hardy/alpha5)

:)

Thanks, well, I'm sure things will get tweaked and changed as time goes on, I know I won't be able to resist the upgrade when it comes officially ;)

---

### Post by tagawa on 2008-02-26
> **PiggiePaul said:**
> Thanks for that.

The second command came up with:
[COLOR="Blue"]
The following packages were automatically installed and are no longer required:
  liblzo1 python-qt3 python-sip4
The following packages will be REMOVED
  liblzo1 python-qt3 python-sip4[/COLOR]

You sure I don't need that?
I recall reading about python in some posting about various things.

I've said NO at the moment by the way

I frequently run autoremove and it seems to work well.
It's your machine so it's your decision, but if it was me I'd give it a try and if there's a problem run:
sudo apt-get check
and
sudo apt-get -f install

Incidentally, once you've run autoremove it's worthwhile going back into Synaptic, clicking 'Status' and removing everything in the 'residual config' list to get rid of lingering configuration files from uninstalled packages.

Hope this helps.

---

### Post by 3rdalbum on 2008-02-26
Remember, clicking on buttons with the mouse was difficult when you first learnt it. But now it's second-nature.

Now it's second-nature for me to use gksudo nautilus to open a root file browser.

The other thing you could do is go into Synaptic Package Manager and install the package "nautilus-gksu". This gives you a new contextual menu item "Open as administrator". You can right-click on a folder and go to "Open as administrator", put in your password, and presto you have root privileges.

---

### Post by PiggiePaul on 2008-02-27
> **3rdalbum said:**
> Remember, clicking on buttons with the mouse was difficult when you first learnt it. But now it's second-nature.

Now it's second-nature for me to use gksudo nautilus to open a root file browser.

The other thing you could do is go into Synaptic Package Manager and install the package "nautilus-gksu". This gives you a new contextual menu item "Open as administrator". You can right-click on a folder and go to "Open as administrator", put in your password, and presto you have root privileges.

Thanks, sounds a useful addition, will try that later.

---

### Post by PiggiePaul on 2008-02-27
> **3rdalbum said:**
> Remember, clicking on buttons with the mouse was difficult when you first learnt it. But now it's second-nature.

Now it's second-nature for me to use gksudo nautilus to open a root file browser.

The other thing you could do is go into Synaptic Package Manager and install the package "nautilus-gksu". This gives you a new contextual menu item "Open as administrator". You can right-click on a folder and go to "Open as administrator", put in your password, and presto you have root privileges.

Just want to say.

SUPERB !!!! :D

That was EXACTLY the kinda thing (option) I've wanted all along and thought should be there as standard.

And to think it was there (in the background - kinda) all the time.

Excellent, and again, Many thanks for letting me know about this.

---

