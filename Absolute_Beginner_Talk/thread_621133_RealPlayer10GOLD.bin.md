---
title: "RealPlayer10GOLD.bin"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Scott A on 2007-11-23
When I try to install RealPlayer10GOLD.bin, I get this error message:


Could not open location 'file:///./RealPlayer10GOLD.bin'

Details: The location or file could not be found.

I have tried following the installation instructions below, to no avail.
Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

---

### Post by philinux on 2007-11-23
Get the .deb file - much easier to install.

---

### Post by taurus on 2007-11-23
```
cd ~/Desktop
chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

---

### Post by candtalan on 2007-11-23
> **Scott A said:**
> When I try to install RealPlayer10GOLD.bin, I get this error message:
Could not open location 'file:///./RealPlayer10GOLD.bin'
Details: The location or file could not be found.


When you are using the Terminal to execute the binary, you will need to first be in the directory containing the binary, so you may need to change directory (command cd) to navigate there first.
For example, if the downloaded file is located as 
/home/user/downloads/RealPlayer10GOLD.bin
then (without discussions of the implications of Path) navigate so that your Terminal prompt is
user@your-pc:~/downloads$
then start executing the necessary commands for the chmod stuff and then run the binary.
If you want realplayer to be installed and used at system level, used sudo preceeding the run command:
Run the .bin file by typing "sudo ./RealPlayer10GOLD.bin"

you might choose to install into the location
/opt

and you might choose to accept a system wide level install when asked.

---

### Post by Scott A on 2007-11-23
Hi, I followed the following directions, but still get an error message.
cd ~/Desktop
chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

Here is the error message I get:
Could not find an appropriate hxplay or realplay in the system path to use as an embedded player.

When I installed realplayer10gold, is looked like it installed on the desktop. I didn't know what else to do but what it prompted me to do. Was that the problem, or something else?

Thanks again in advance, Scott A
:confused:

---

### Post by taurus on 2007-11-23
Read this, [https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods).

---

### Post by philinux on 2007-11-23
I downloaded the deb file and installed.

However even though it puts nphelix.so and xpt into /usr/lib/mozilla/plugins

Firefox fails to pick them up.

---

### Post by mali2297 on 2007-11-23
> **philinux said:**
> I downloaded the deb file and installed.

However even though it puts nphelix.so and xpt into /usr/lib/mozilla/plugins

Firefox fails to pick them up.

Is there a conflict with mplayer plugins?
If so, check this tip:
[http://ubuntuforums.org/showthread.php?t=200195](http://ubuntuforums.org/showthread.php?t=200195)

(The tip is rather old but might still be useful.)

---

### Post by philinux on 2007-11-23
Only got totem plugins installed.

However if I sudo locate nphelix.so the system fails to find it even though its there. It's like its invisible to file search. Is this cos trackerd is off?

---

### Post by mali2297 on 2007-11-23
> **philinux said:**
> Only got totem plugins installed.

However if I sudo locate nphelix.so the system fails to find it even though its there. It's like its invisible to file search. Is this cos trackerd is off?

The files are not broken links, are they?

If uncertain, check
```

ls -l /usr/lib/mozilla/plugins/nphelix.so

```
If it is a link, you will see where it is pointing.

---

### Post by philinux on 2007-11-23
It's not a broken link.

---

### Post by philinux on 2007-11-23
Solved it for me by getting feisty version of realplayer.

[http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

---

### Post by philinux on 2007-11-23
There must be a bug with gutsy realplayer, off to launchpad tomorrow with it.

---

