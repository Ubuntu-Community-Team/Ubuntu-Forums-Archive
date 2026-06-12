---
title: "Linux Commands."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by zeehat on 2007-08-14
I am new to Ubuntu as of today, and I need to know useful commands for the terminal.  Also how do I install aMsn?  I did 'sudo aptitude install amsn' in the terminal, and it said it installed, but where is the file?  I want to access the file and open the program.  Thanks.

---

### Post by skymera on 2007-08-14
i think you should have done some homework before installing.
like basic commands.

sudo apt-get update   this updates your sources.list
sudo apt-get upgrade   this upgrades packages to new versions

Automatix is good to install software, but is known to be dodgy.

[www.ubuntuguide.org](www.ubuntuguide.org)

has EVERYTHING you need to know.

good luck

---

### Post by p_quarles on 2007-08-14
Here's a fairly good online guide:

[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

I also highly recommend Scott Granneman's _Linux Phrasebook_

Most programs can be run simply by typing the name of the package. Some use slightly different commands, but with this one, I'm pretty sure you can simply type "amsn."

---

### Post by jingo811 on 2007-08-14
> I want to access the file and open the program. 
Try to find it in adress location **/usr/bin/**.

> Also how do I install aMsn
I think I saw that program name in
**Applications> Add/Remove**
when I did a search for Internet programs once.  That will give you icons and all without fuss.

> I need to know useful commands for the terminal
[LIST]
[*]ls
[*]ls -l
[*]ls -la
[*]cd ..
[*]cd (some_directory_name)
[*]cp (some.important.file) (some.important.file_backup)
[*]sudo cp (some.important.file) (some.important.file_backup)
[*]gksudo gedit (some.important.file)
[/LIST]

Good overview for commands never read it though too much for my brain to handle :lolflag: I kinda got into it gradually when asking for help fixing my many problems back in my newbie era.
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by Ek0nomik on 2007-08-14
> **skymera said:**
> i think you should have done some homework before installing.
like basic commands.

sudo apt-get update   this updates your sources.list
sudo apt-get upgrade   this upgrades packages to new versions

Automatix is good to install software, but is known to be dodgy.

[www.ubuntuguide.org](www.ubuntuguide.org)

has EVERYTHING you need to know.

good luck

Automatix isn't a good option for anyone.  You don't learn how to use your system, and it causes problems down the road.

---

### Post by p_quarles on 2007-08-14
> **skymera said:**
> i think you should have done some homework before installing.
like basic commands.

sudo apt-get update   this updates your sources.list
sudo apt-get upgrade   this upgrades packages to new versions

Automatix is good to install software, but is known to be dodgy.

[www.ubuntuguide.org](www.ubuntuguide.org)

has EVERYTHING you need to know.

good luck
Beg to differ. This is the correct place to find information about basic Ubuntu-related things.

As for automatix, I really don't think anyone should suggest that for new users. Even if it doesn't crash your system, there are major problems with its design, according to one of the lead Ubuntu developers:
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by zvacet on 2007-08-14
If it is installed look in** applications>internet**

[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

---

### Post by zeehat on 2007-08-14
Wow, that's really awesome.  I like how you run programs in Linux [yes sorry I am a Linux newbie].  Thanks for all your help.

---

