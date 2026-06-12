---
title: "MacBook Pro (Santa Rosa) Triple Boot Refit Issue"
date: 2007-12-09
forum: Apple Intel Users
---

### Post by SMccan on 2007-12-09
Hey everyone. I recently was able to finally get my MacBook Pro to triple boot Leopard/Xp/Ubuntu 7.10 with refit, but I just have a little issue I was hoping could be easily fixed. I've looked all over the net for answers and I've either missed the helpful posts, or there isn't one setup yet. When booting up in refit I see my OSX, XP, and Ubuntu choices, but there is an extra option to load up Apple's Hardware Test from my OSX partition. I will not be using this feature and would like to remove this option from the boot menu. The only information that I have come across is that I would need to change an option in the refit.config file in osx but I did not have a clear answer on what exactly to do. If anyone has a pretty basic guide on how to do this for someone who isn't totally savvy on this sort of thing I would really appreciate it. Also would appreciate any links to a guide that I haven't found online yet. Thanks so much for the help and glad to be a new member of Ubuntu forums!

---

### Post by cyberdork33 on 2007-12-09
> **SMccan said:**
> Hey everyone. I recently was able to finally get my MacBook Pro to triple boot Leopard/Xp/Ubuntu 7.10 with refit, but I just have a little issue I was hoping could be easily fixed. I've looked all over the net for answers and I've either missed the helpful posts, or there isn't one setup yet. When booting up in refit I see my OSX, XP, and Ubuntu choices, but there is an extra option to load up Apple's Hardware Test from my OSX partition. I will not be using this feature and would like to remove this option from the boot menu. The only information that I have come across is that I would need to change an option in the refit.config file in osx but I did not have a clear answer on what exactly to do. If anyone has a pretty basic guide on how to do this for someone who isn't totally savvy on this sort of thing I would really appreciate it. Also would appreciate any links to a guide that I haven't found online yet. Thanks so much for the help and glad to be a new member of Ubuntu forums!

You would be the first to indicate such a problem here. There is no way to exclude certain bootable devices in rEFIt.

---

### Post by alabwab on 2007-12-15
> **SMccan said:**
> Hey everyone. I recently was able to finally get my MacBook Pro to triple boot Leopard/Xp/Ubuntu 7.10 with refit, but I just have a little issue I was hoping could be easily fixed. I've looked all over the net for answers and I've either missed the helpful posts, or there isn't one setup yet. When booting up in refit I see my OSX, XP, and Ubuntu choices, but there is an extra option to load up Apple's Hardware Test from my OSX partition. I will not be using this feature and would like to remove this option from the boot menu. The only information that I have come across is that I would need to change an option in the refit.config file in osx but I did not have a clear answer on what exactly to do. If anyone has a pretty basic guide on how to do this for someone who isn't totally savvy on this sort of thing I would really appreciate it. Also would appreciate any links to a guide that I haven't found online yet. Thanks so much for the help and glad to be a new member of Ubuntu forums!



in refit.conf you can disable the shell or the complete second row:
see quote from refit.conf
so the corresponding line should read:
hideui tools funcs


# Hide various user interface elements. Here you can list the names of
# interface elements to hide. Currently supported:
#  banner    - the rEFIt title banner
#  shell     - the EFI shell icon
#  tools     - all EFI tools (currently just the shell)
#  funcs     - built-in functions (about, restart)

#    ('tools' and 'funcs' together hide the complete second row of icons.)

#  label     - text label in the menu
#  hdbadges  - volume badges for internal disk volumes (same as
#               'hidebadges internal')
#  badges    - all volume badges (same as 'hidebadges all'); this setting
#               is not recommended because it won't let you distinguish
#               installed OSes and bootable CDs/DVDs.
#  all       - all of the above, except for 'badges'
#
#hideui tools funcs hdbadges
#hideui all

---

### Post by jackmaddox on 2008-01-04
I am having the same problem.  I have tried changing all the options that are commented in the config file and nothing gets rid of the circuit board looking icon for the hardware test.  I have the exact same setup, a MacBook Pro - SantaRosa, with Leopard/XP/Ubuntu7.10.  I have also noticed that if the OSX Install CD is in the drive bay then there will be 6 icons in at the boot prompt instead of the 4 that should be there.  From left to right, they are 1.)Apple icon with internal disk badge, 2.) Circuit Board icon with internal disk badge, 3.) Apple icon with CD badge, 4.) Circuit Board with CD Badge, 5.) Penguin with internal disk badge, 6.) XP Logo with internal disk badge. 

Maybe apple is including a new boot option in Leopard or with the new MacBooks. 

To the first poster.  Did you upgrade to Leopard from Tiger, or did your laptop come with Leopard already installed.  Mine came with Leopard already installed, so I don't know if this would have occurred with Tiger.  

I hope that someone has a fix or that there will be more options for customization in a future release.  

Also, one last thing for SMccan.  When you say you aren't very savvy about this sort of thing I don't know to what degree you are talking about so forgive me if this is too elementary.

1.) Boot into Mac OSX
2.) Open Terminal.app
3.) type ```
sudo nano /efi/refit
```
4.) type your administrator password
5.) use ```
CTRL+V
``` to page down
6.) Read the file.  Anything with ```
#
``` in front of it will not be used by refit
7.) delete the ```
#
``` from the lines you want to turn on
8.) type ```
CTRL+x
```
9.) type ```
Y
```
10) hit ```
ENTER
```

This will save the changes you made to the file.

Reboot and your changes will have taken effect.  Note: you could also install TextWrangler with its command line tools and then relpace the ```
sudo nano 
``` command with ```
sudo edit
``` and it will open into a text editor that is a little more intuitive than nano.

---

### Post by alephsmith on 2008-01-04
> ```
sudo nano /efi/refit
```

should be:

```
sudo nano /efi/refit/refit.conf
```

And be thankful you are using nano and not vi.

I am having a related problem, I restored my data from a backup stored on my iPod. Now the refit icon for me internal drive has been replaced with an iPod icon.

Where is refit getting this icon from? it is not in /efi/refit/icons as far as I can see.

Searching google for[FONT="Courier New"] refit [/FONT]and [FONT="Courier New"]ipod[/FONT] just brings up a bunch of results from text adds for cheap ipod deals.

---

### Post by cyberdork33 on 2008-01-04
> **alephsmith said:**
> should be:

```
sudo nano /efi/refit/refit.conf
```And be thankful you are using nano and not vi.
You can also just use TextEdit, or Smultron, or any other number of editors.

> I am having a related problem, I restored my data from a backup stored on my iPod. Now the refit icon for me internal drive has been replaced with an iPod icon.rEFIt thinks the volume is an iPod, probably because you copied some obscure settings file from the iPod when you restored. If it is the main large icon, then I am not sure how to change it, but you can change the smaller icon by changing the icon for your OSX mount on the desktop... If you look in the root of the OSX system, there are usually some .files liek .DS_Store, .VolumeIcon.icns, etc. This is usually where that kind of thing is configured. (the .VolumeIcon.icns file is the partition icon you see on the desktop, deleting it will revert to the default.)

---

### Post by murphybailey79 on 2008-01-04
I am having the same problem and you guys seem to know more than me. What i did is that i took my computer to Geek Squad and they got it done in one day and paid $50... It's worth it

---

### Post by Reg777 on 2008-02-11
> **SMccan said:**
> Hey everyone. I recently was able to finally get my MacBook Pro to triple boot Leopard/Xp/Ubuntu 7.10 with refit, but I just have a little issue I was hoping could be easily fixed. I've looked all over the net for answers and I've either missed the helpful posts, or there isn't one setup yet. When booting up in refit I see my OSX, XP, and Ubuntu choices, but there is an extra option to load up Apple's Hardware Test from my OSX partition. I will not be using this feature and would like to remove this option from the boot menu. The only information that I have come across is that I would need to change an option in the refit.config file in osx but I did not have a clear answer on what exactly to do. If anyone has a pretty basic guide on how to do this for someone who isn't totally savvy on this sort of thing I would really appreciate it. Also would appreciate any links to a guide that I haven't found online yet. Thanks so much for the help and glad to be a new member of Ubuntu forums!


thought this might help

from [http://refit.sourceforge.net/:](http://refit.sourceforge.net/:)
News

2008-02-10: Apple is pre-installing its “Apple Hardware Test” diagnostic software on the hard disk in current Mac models. On these Macs, an extra icon shows up in the list of operating systems on every boot. There currently is no way to hide that icon. I'm working on a new version of rEFIt that will hide the Hardware Test icon and make it an option in the submenu of the Mac OS X icon instead.

---

### Post by SMccan on 2008-02-22
Anyone interested about this issue,

I HAVE GOOD NEWS!

If you haven't already heard, rEFIt has come out with version .11 which fixes the issue with the Apple Hardware test showing as a bootable device. THANKS REFIT!

Now my bootloader looks nice and neat!

Thanks for the earlier post letting me know that the devs were looking into the problem.

---

### Post by fakt00r on 2008-03-10
Maybe someone here can help me too:
I have installed Mac OS X, Windows XP and Ubuntu 7.10. reFit Shows all three OS at startup. But maybe during installation of Ubuntu I made a mistake. I have the following situation:

```

reFIT
-----
Mac OS X    ------------------> Mac OS X
Windows XP  --+           + --> Windows XP
              +--> Grub --+
Ubuntu 7.10 --+           + --> Ubuntu 7.10

```

:confused: How can I configurate reFit that Windows and Ubuntu are starting directly without going indirect way via Grub? :confused:

---

### Post by cyberdork33 on 2008-03-10
> **fakt00r said:**
> How can I configurate reFit that Windows and Ubuntu are starting directly without going indirect way via Grub? See multi-boot guide in my signature.

---

### Post by fakt00r on 2008-03-10
> **cyberdork33 said:**
> See multi-boot guide in my signature.

Worked fine. Thanks a lot! :popcorn:

Now I just have to solve my keyboard problems. [-o<

---

