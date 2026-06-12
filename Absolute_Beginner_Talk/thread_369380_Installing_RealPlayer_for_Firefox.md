---
title: "Installing RealPlayer for Firefox"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by halberd25 on 2007-02-24
Hi, I'm still pretty new to Linux.  I've been trying to install RealPlayer for Firefox, but I haven't had too much luck.  I downloaded the rpm file and compiled it with Alien.  I installed it, but what's the next step?  I read somewhere that I have to copy the plugin files from RealPlayer's mozilla folder to firefox's plugin and config folder.  I found what I think is a plugin folder, but I'm still not too sure how to make this work.  Any ideas?

---

### Post by MasterOfDisaster on 2007-02-24
This might help:
[http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/](http://jordilin.wordpress.com/2006/10/30/howto-firefox-and-the-realplayer-plugin-in-ubuntu-edgy-eft/)

Cheers.

---

### Post by halberd25 on 2007-02-24
No dice.  I don't think that my firefox is using totem, I don't have a plugins folder in that directory, and I'm using dapper.

---

### Post by Maestro23 on 2007-02-24
Try d/l the .bin file from the site: [http://www.real.com/linux/?src=guide&pcode=rn&pageid=cogixPoll&pageregion=footer](http://www.real.com/linux/?src=guide&pcode=rn&pageid=cogixPoll&pageregion=footer)

Easier setup and the first time you activate it, it walks you thru configuration using a GUI.

Just a thought.

---

### Post by halberd25 on 2007-02-24
I've tried that, and it just says "Couldn't display "/home/ben/Desktop/RealPlayer10GOLD.bin" when I try to run it.

---

### Post by Maestro23 on 2007-02-24
> **halberd25 said:**
> I've tried that, and it just says "Couldn't display "/home/ben/Desktop/RealPlayer10GOLD.bin" when I try to run it.

Where did you download the file to? Get to that directory and:

Then just open a terminal:

> chmod a+x RealPlayer10GOLD.bin

./RealPlayer10GOLD.bin



Instructions from the site:
> Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

I just tried it myself to see if there were any problems you might run into.  No probs here.

---

### Post by bergamot on 2007-02-24
When I downloaded that file, it was not executable by default. I'm not sure, but it sounds like that's why you couldn't run it. Right-click on the file, go to Properties, then Permissions. Check the box labelled "Allow executing file as program." You should then be able to run the installer by double clicking on the file.
In Linux, unlike Windows, files need to have the a flag set for them to be executable. Slightly less convenient on the surface, but more secure.
Hope this helps

---

### Post by halberd25 on 2007-02-24
I changed the permissions.  Now nothing happens at all when I double-click on it.

---

### Post by halberd25 on 2007-02-24
I got the installer to work, but now when I try to view a realplayer video, it says something like "Could not find an appropriate hxplay or realplay embedded in the system path."  I checked the about: plugins page and it says Helix DNA Plugin: RealPlayer G2 Plug-In Compatible, so I'm confused as to what's wrong.

---

### Post by RichPicker on 2007-02-27
I am having similar problems. Maybe I should wait until you get yours fixed before adding any text to this thread. I will say, however, that I installed RealPlayer from the Add/Remove Programs, not from the Real.com website. It seems like everything almost works, and if I could get Firefox to use RealPlayer as the default, instead of MoviePlayer, it might work.

---

