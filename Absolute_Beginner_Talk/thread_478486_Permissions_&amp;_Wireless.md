---
title: "Permissions &amp; Wireless"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by ljk on 2007-06-19
Hello,
I have been trying to get connected to my wireless home network which works fine with 1 Windows laptop and an aging iBook.
I installed Feisty (7.04) on the Windows laptop using "wubi"  (I know this is NOT officially supported but I think anything which encourages people to try Open Source alternatives can't be bad) but the wireless adapter card which lights up in Windows remains lifeless in Ubuntu.
After many hours of reading and searching I tried to edit the "menu.lst" file in the grub folder - some of the documentation suggested that I should add  "pci=assign-busses" to a particular line in order to have the card recognised as being there.
I was unable to do this as Ubuntu told me the owner of the file was "root" - I did not have permission to edit the file.
Further searches suggested terminal commands (I have only the vaguest understanding of these things). I copied these but found that anything starting in "sudo" did not work. Even more hours later I tried "gksudo" to only have the computer issue dire warnings combined with words such as "authorizations".
I did the edits but after restarting I found that the text I had added was no longer there.
It is understandable that Ubuntu developers should shield this wonderful OS from people like me but how can I get things working when I need to edit a file and Ubuntu won't let me? I am obviously a "point & click" type of user - I don't object to entering my password for administrative tasks but I did believe Ubuntu was seriously trying to make Linux accessible to people like myself. If we are not allowed to edit a file, even when we are the true owners/administrators, without recourse to terminal commands known only to the cognoscenti, I fear that the "human beings" Ubuntu was ostensibly designed for will just stay with the stuff they already have.

How can I edit  files which are owned by "root"?

                                                                                                                                                                
[PS - I did try "ndiswrapper" with drivers supplied by the card manufacturer & also drivers by the chipset supplier - no result. I will persevere. Please try to make this system easier for "Point & Clickers".]

---

### Post by mikewhatever on 2007-06-19
To edit a file 'owned by root' use the following command
> gksudo gedit /boot/grub/menu.lst
After you are done, don't forget to click the 'save' button. 
I do not quite see what is wrong with using the terminal commands.

If you must have a graphic way of editing files, hit Alt+F2 and type 'gksudo nautilus', enter your password, and navigate to the file you want to edit, open by double clicking, edit, save and exit.

---

### Post by jbaerbock on 2007-06-19
I has to use ndiswrapper as well. Linux Mint (based on Ubuntu) has a GUI for ndiswrapper. After you used ndiswrapper did you try typing "ndiswrapper -l" and was your driver listed without problems? I to like GUI better than the terminal but sometimes the terminal is just a better way to do things and quicker too (if you know what you are doing). Anyway if when typing the previous your driver is listed does it mention in ( ) an alternate driver being used? If it does then in order to use your driver you want to use you must blacklist the driver Linux automaticaly wants to use. Simply navigate (either in gksudo nautilus or in terminal) to /etc/modprobe.d directory and edit the file black list. If you are using terminal type "cd /etc/modprobe.d" and hit enter "obviously ommit the quotations". That will take you to the folder which contains your blacklist. The blacklist file is used to control which drivers you don't want Linux to load on startup. If in terminal and in the afore mentioned directory type "sudo gedit blacklist" the word password will then appear (this is in order to acess the file as a superuser). After typing in the password it should open a text file in the GUI. Simply add "blacklist" followed by whatever alternate driver ndiswrapper mentioned.

  For example my driver is bcml5 for my broadcom driver and for alternate it mentioned bcm4xx. So I simply edited the blacklist file and added within the text somewhere (doesn't matter where) blacklist bcm4xx, then I restarted my system and the windows wireless driver i installed via ndiswrapper was able to take over. I know this was a long explanation, if you have further questions feel free to ask.

---

### Post by ugm6hr on 2007-06-19
> **ljk said:**
> How can I edit  files which are owned by "root"?

This has already been answered by others - mikewhatever has given a point&click option above.

Just be sure that it is the correct question.  I cannot see how editing menu.lst can have any impact on your wifi card (irrespective of whether it is USB / PCI / PCMCIA / internal).

It might be a better option to merely post again with a "How do I get my wifi working" - assuming that a similar thread does not already exist for your card / chipset (which is unlikely).

In case you haven't already discovered these:
```
lspci
lsusb
ifconfig
iwconfig
```
They can all give potentially useful info regarding your wifi.

Also - ndiswrapper wiki includes a list of cards that work, together with which Windows drivers to use with it (and which version of ndiswrapper is required):
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by ljk on 2007-06-20
Many thanks to everyone who responded to my post. It's greatly appreciated.

I made the post because my wifi card seemed not to be recognised by Fiesty so I thought it might be a hardware detection problem. Some of the support documentation advised adding "pci=assign-busses" to the line in /boot/grub/menu.lst which ends in "splash". I thought that if the card was detected I could then focus on ndiswrapper & drivers to try to get wireless working.

I tried mikewhatever's suggestions a few minutes ago but nothing worked. The terminal command got menu.lst open in gedit - I did click the "save" button after editing but when I re-opened menu.lst (Display) the additional text was gone.

I tried Alt+F2 etc but not even a password prompt appeared.

I have been slavishly following "how to"s from the Ubuntu documentation on the net and consulting "The Official Ubuntu Book" so I had already tried the terminal command suggested by mikewhatever but gave it another shot.

I suspect that there may be something wrong with the downloaded wubi installation as these commands should have allowed me to edit the file so I will delete the current Ubuntu installation, download a fresh one and start again.

If that works, I sincerely aplogise to you all as the problems would have been caused by a faulty installation.

Again, many thanks & best regards.

---

