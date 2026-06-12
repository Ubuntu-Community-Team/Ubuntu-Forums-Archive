---
title: "beginner's pain [Resolved]"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by ottawa on 2007-04-14
Hi there,

after getting help for commands and testing a few in the terminal of ubuntu 6.10 server (no mouse) I am not able to find the way OUT of the files I had opened. I guess I am too new to Linux :)
To be more precise, here 2 samples:

1. sample:
man man will show me the help about the help. Now: How to get out of the file ?

2. sample:
I opened source.list with
sudo editor /etc/apt/source.list
looked at the file and at the bottom I have my options. I need to close the file and want to use "Exit" which is shown as  ^X Exit (^X highlighted) Question: How to activate this ? I tried ^X by activating the keys at the same time = nothing  I can't get the curser there.

In both situations: What I am suppose to do ?  :(
By the way: I can't find any "Save" command . Are the changes made to files directly written and saved ?

Any help very appreciated.

---

### Post by BoneKracker on 2007-04-14
pressing q will exit a man page

pressing ctrl+x will exit from nano (the editor)
("ctrl" is often abbreviated as "^")

pressing ctrl+o will save a file in nano ("save out", I guess is the logic)
If you try to exit with it unsaved, it will prompt you anyway.

Be patient, it will soon be muscle memory to you, like addressing an email or typing a search into google.  Everybody goes through it.
The man pages are your best friend.  Type "man nano".  (And remember 'q' to quit.)   ; )

---

### Post by ottawa on 2007-04-14
BoneKracker

thank you for the tip. Will give it a try.

It's amazing how fast I get the answers here. WOW!

---

### Post by Maestro23 on 2007-04-14
That file is owned by a directory in[COLOR="Red"] root "/"[/COLOR].  Therefore you need to use "sudo" in front of your command to edit the file.

> sudo nano /etc/apt/sources.list

When you have made changes, Ctrl O (Saves the file) then Ctrl X (Exits the program)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Some more links to introduce you to Ubuntu:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

How to Change Default OS: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by ottawa on 2007-04-14
Is noted down and works like a charme.

There are coming old memories back as I liked the windows command line, I guess I like this even more :)  :)

---

