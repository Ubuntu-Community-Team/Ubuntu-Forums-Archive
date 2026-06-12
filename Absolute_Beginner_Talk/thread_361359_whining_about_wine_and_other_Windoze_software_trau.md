---
title: "whining about wine and other Windoze software traumas"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by daft bird on 2007-02-14
Right, this is really several questions all rolled up.  I'll try to keep it seperate...

1) I can't actually find Wine in order to open it and do some of the things I've been told to do in order to sort out my troubles.  So, bearing in mind I am a VERY daft bird and therefore need the utter Noddy guide here, where do I find Wine???  and how do I open it?

2) I successfully installed some software on my dd's PC that absolutely has to have the  CD-ROM in the "D" drive, won't work in a drive with any other name (and yes I know how badly written that makes it but it is her favourite game okay?).  I was told to go to wine config (see above for why I didn't do that...) and that it would all magically be solved there.   So, how to I convince her  CD drive that it's called D and not whatever Edubuntu calles it?

3) Having given up on taht game I lurched onto her 2nd favourite game.   It installed and ran fine and dandy in "Parent"  but the launcher didn't work - it's one of those that launches right after you finsh intalling it.  Uninstalling then re installing Wine seemed to make a second Laucher appear on teh desktop which worked wonderfully, the game worked find and dandy and I started to think I had cracked this one and earned millions of Brownie points.  Then I switched to me dd's log in and guess what?  U-huh, no launcher :confused:    Wine installed it to "C/program files" which of course doesn't really exist so I cn't go find it and make a launcher myself.   So how do I get it working under her log in (very restricted!!!  She's only 6) as I cna't access any add/remeve things within her log in to try the uninstall and re install trick there.

---

### Post by taurus on 2007-02-14
1.

Applications -> Accessories -> Terminal
```
wine **program**
```

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by steve.horsley on 2007-02-14
1:
Launch executables with **wine whatever.exe**. Wine is actually a command-launched program. Or you can right-click on a .exe and choose to open it in wine. You can name the executables either with their linux path like **wine /home/steve/trojan1.exe** or if it's on the C drive, you can say **wine "C:\\Program Files\\whatever\\whatever.exe"**.

2: 
it's **winecfg** not wineconfig. This launches a configuration GUI where you can add a specification that says to map D: to /media/cdrom (under the Drives tab).

3:
In normal Linux, wine hides its dummy drive C in you home directory, in **.wine/drive_c**. Each user has their own home directory, and therefore their own set of wine config files in their own .wine folder. You can see hidden folders in nautilus by pressing Ctrl-H. So installing the games into your wine won't do anything to her wine setup. You will have to run the setup under here account.

At least, that's with normal Linux. If you are running thin clients to a Edubuntu server, things may be set up differently, I don't know - I've never tinkered with Edubuntu.

---

### Post by daft bird on 2007-02-14
Thanks, think I may have it now, I rummaged through the wine folder and found all sorts of lost souls that I decided I mustn't have installed after all!

Now, how does one make a desktop launcher.... Okay!!! I'll go try for myself but expect me back shortly for idiot proof instructions!!!

---

### Post by Shay Stephens on 2007-02-14
> **daft bird said:**
> Thanks, think I may have it now, I rummaged through the wine folder and found all sorts of lost souls that I decided I mustn't have installed after all!

Now, how does one make a desktop launcher.... Okay!!! I'll go try for myself but expect me back shortly for idiot proof instructions!!!

Right click, create launcher
[LIST=1]
[*]Type in a descriptive name (e.g.Photoshop)
[*]Type in the command (e.g. wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe")
[*]Add a comment if desired (e.g. Edit photos)
[*]Click on the button that edits the icon.  choose a generic icon or navigate to one you have saved already.
[/LIST]

With Photoshop at least, using the windows path is best, using the linux path causes errors.

---

