---
title: "how do u instal drivers ment for Windows?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by M!K3_$ on 2006-02-27
i want to instal a driver for my wireless internet PCI card, but the driver is ment for windows. is there anyway i can do this?

---

### Post by Coelocanth on 2006-02-27
You can't use the Windows drivers, no. You'll have to do a search for your card and find out what to do/where to get the proper Linux drivers for it. First thing I'd check is the manufacturer's web site. It's possible they may have Linux drivers for it.

---

### Post by wylfing on 2006-02-28
True, but ndiswrapper is meant for doing what you describe, **M!K3_$**. So if there are no native Linux drivers, you might try that. See here:

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by benplaut on 2006-02-28
[QUOTE=wylfing]True, but ndiswrapper is meant for doing what you describe, **M!K3_$**. So if there are no native Linux drivers, you might try that. See here:

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)[/QUOTE]

keep in mind that ndiswrapper is a bit of a hack (in the best sense of the word, of course). It worked for me when i needed it, but it doesn't work for all.

What's the manufacteror and model of your card?

---

### Post by az on 2006-02-28
[QUOTE=M!K3_$]i want to instal a driver for my wireless internet PCI card, but the driver is ment for windows. is there anyway i can do this?[/QUOTE]

1.   Fire up synaptic.  Search for ndiswrapper.  Click on ndiswrapper-utils and mark for installation.  Apply.
2.  Get you wireless device cd.  Open it on your screen.  Navigate to the Windows Xp driver folder.  Drag and drop the .inf files and any other files in that folder to the desktop.
3.  Open a terminal.  type this
cd /Desktop
sudo ndiswrapper -i XXXXXXXX.inf
(Where XXXXXX is the file name of the .inf file.  If you are not sure, try the one that makes the most sense with respect to your card's name)
ndiswrapper -l
(this asks ndiswrapper to show you what it sees - If you get a driver present, hardware present go on to the next step.)
sudo modprobe ndiswrapper
Then fire up the networking tool.

When you are happy, type 
sudo gedit /etc/modules
and add the work ndiswrapper at the end of the list.  This will load the module at boot time.


If none of this works, you probably will need a more recent version of the .inf file that ships with your card.  Ndiswrapper is developed with the most recent one.  If that is the case, post the model of your card.

---

### Post by Zodiac on 2006-02-28
Oh oh oh!!

Do a Linksys WPC54G Ver. 2!!! 


P.S. - Yea I'm hijacking this thread big whup wanna fight about it?

---

