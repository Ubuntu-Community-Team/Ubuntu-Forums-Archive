---
title: "best way to modify xorg.conf file?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by pwrcul on 2006-11-27
What is the best way to modify the xorg.conf file?

I eventually succeeded by using "sudo dpkg-reconfigure xserver-xorg", but I don't have a clear idea of what I was doing.  The dialog that ensued did not seem to have a way of backing up.  Does it?
Is there a document or help file which describes how to enter checks and other modifciations  (Fortunately, I found a message that said use the SPACE key.  ESC key seemed useful in places but it was a wild guess on my part)
I found man dpkg and man dpkg-reconfigure, but they have nothing to say about the dialog that gets invoked.

At one point I tried to use my latent, old Unix knowledge and succeeded in using "cd /etc" but then found it could not find X11 in "cd /X11" from the /etc directory.  That was when gedit would not let me make a backup copy, but since then I learned that I could have tried "sudo gedit /etc/X11/xorg.conf"  Any idea why I could not descend the tree from /etc to /X11?

Given the choices of using dpkg-reconfigure, an editor in the terminal if I can reach X11, or sudo gedit, which method is best?  

Thanks.

---

### Post by IYY on 2006-11-27
```
cd /X11 
```

does not mean "go to the subdirectory X11 in the current directory", but rather "go to the directory /X11" where "/" means the root of the filesystem.

Options that would have worked:

```
cd X11
``` 

or

```
cd ./X11
``` 

or

```
cd /etc/X11
``` 

The code to back up your xorg file is:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` 

The code to edit your xorg file is:

```
gksudo gedit /etc/X11/xorg.conf
```

Remember that if something breaks, the code to restore from the backup created using the code I gave you is:

```
cp -f /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by aysiu on 2006-11-27
```
sudo dpkg-reconfigure xserver-xorg
``` automatically makes a timestamped backup of your /etc/X11/xorg.conf file.

---

### Post by bodhi.zazen on 2006-11-27
sudo dpkg-reconfigure xserver-xorg is best.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```It essentially the same thing. Default options are selected with the exception of resolution.

To manually edit, what editor do you like? vim, nano, gedit?

For the sake of example lets stay with gedit.

first make a backup, then edit:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Configuration of X is complex and there are a variety of options....

Start here:
[Arch Linux How to X11](http://wiki.archlinux.org/index.php/Xorg7)
[Gentoo how to X11](http://www.gentoo.org/doc/en/xorg-config.xml)
[XFree Local Multi-User HOWTO](http://tldp.org/HOWTO/XFree-Local-multi-user-HOWTO/)

---

### Post by pwrcul on 2006-11-29
Thanks to IYY, aysiu and bodhi.zazen for your thoughtful points, suggestions and links.

I searched in vain for a user's guide type doc to the user interface to "sudo dpkg-reconfigure xserver-xorg" and found the most usable fragment to be from [www.mepis.org/docs/en/index.php/Dpkg-reconfigure_xserver-xorg](www.mepis.org/docs/en/index.php/Dpkg-reconfigure_xserver-xorg)
where they said
"Navigate through the dialogs by using:

    * Tab key to toggle between the buttons
    * SpaceBar to toggle check boxes on or off
    * Return to accept/next/ok
    * Arrow Keys for Up/Down in lists
    * Left/Right to tab between boxes"

The same Mepis file also says "If the first attempt to configure X isn't successful/satisfactory - run it again until satisfactory result is obtained."  So I guess there is no backing up.  It did not say anything about ESC, while I found it handy.

Later, while skimming Linux in a Nutshell, 4th ed., I found out that dpkg-reconfigure is a perl script (see p. 551).  I tried to find it, thinking it would be in plain text and perhaps well commented, etc., but I did not succeed.  Anyone know where I can find it?  

(If it is not in plain text, where can I find the source?  Googling did not help.  I also came up empty handed at gnu.org and sourceforge.net.  This may seem a waste of time, but I now want to know how this ecosystem functions.)

In the process of looking around I found lots more discussion and hints.  At some point I will come back and modify my grub entries and eventually work on the printer, etc.

Once again, I am very pleased with the help I got.

---

### Post by CatKiller on 2006-11-29
> **pwrcul said:**
> The same Mepis file also says "If the first attempt to configure X isn't successful/satisfactory - run it again until satisfactory result is obtained."  So I guess there is no backing up.

Actually, that doesn't follow. I believe the backups are date-stamped, like xorg.conf.20061130042515

Glad you're enjoying your adventure.

---

### Post by pwrcul on 2006-11-30
> **CatKiller said:**
> Actually, that doesn't follow. I believe the backups are date-stamped, like xorg.conf.20061130042515

Glad you're enjoying your adventure.

Yes, there are time stamped backups as aysiu pointed out.  I have a bunch now.

I am enjoying the adventure, but it is slow--mostly because of limited time.  I will be away all next week, etc.  Poco a poco.

What I meant to say is that within the dpkg-reconfigure dialog it appears that once you make a choice you cannot revisit it within the same linear pass through it.  You have to start over if you decide you should have answered differently.  That's what I believe the Mepis doc implies.

Does anyone have information on where I can see the dpkg-reconfigure script in plain text?

---

### Post by CatKiller on 2006-11-30
> **pwrcul said:**
> Yes, there are time stamped backups as aysiu pointed out.  I have a bunch now.

I am enjoying the adventure, but it is slow--mostly because of limited time.  I will be away all next week, etc.  Poco a poco.

What I meant to say is that within the dpkg-reconfigure dialog it appears that once you make a choice you cannot revisit it within the same linear pass through it.  You have to start over if you decide you should have answered differently.  That's what I believe the Mepis doc implies.

Ah, I see. "No going back" kind of thing. Separated by a common language :)

> Does anyone have information on where I can see the dpkg-reconfigure script in plain text?

It's something to do with the deb packaging system. I don't know where you'd be able to see the post-installation configuration script, which is what that command runs, but you might potentially be able to find out more about the process from the developer section of debian.org.

You can look at **man xorg.conf** to find out information about the configuration file you're creating through the process. You'll also find information you might find interesting at x.org. Personally, I find it terribly dull :)

---

