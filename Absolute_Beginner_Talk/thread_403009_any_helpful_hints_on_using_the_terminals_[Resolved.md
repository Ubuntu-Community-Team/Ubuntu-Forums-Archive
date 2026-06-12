---
title: "any helpful hints on using the terminals [Resolved]"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by morrissey21 on 2007-04-06
hey guys i'm newbie to ubuntu and have been taught a little by my mate who converted me to ubuntu but i still need to know more about some things ie. terminals or anything else.........
i have only seen a little of what ubuntu has to offer but it seems wikid!!!!!!!!!!!!!!!!
so can anyone help me out?????
or
does anyone no of a descent tutorial or documentation explaining how to use the terminals and other ubuntu features????????

thanx in advance
morrissey21

---

### Post by aysiu on 2007-04-06
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

The best way to get started is to just copy and paste commands. That's what I did.

---

### Post by lukew on 2007-04-06
> **morrissey21 said:**
> hey guys i'm newbie to ubuntu and have been taught a little by my mate who converted me to ubuntu but i still need to know more about some things ie. terminals or anything else.........
i have only seen a little of what ubuntu has to offer but it seems wikid!!!!!!!!!!!!!!!!
so can anyone help me out?????
or
does anyone no of a descent tutorial or documentation explaining how to use the terminals and other ubuntu features????????

thanx in advance
morrissey21

The best command by far is the tab command. auto completes file/dirs and commands. :)

---

### Post by Maestro23 on 2007-04-06
Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29%7C%28driver%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29%7C%28driver%29)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by szymon_g on 2007-04-06
hi.
you can look for bash's features in google :-/. in my opinion the mos usefull shell feature is auto-completation (or something like that ;-P). you can try it by typing eg. cd /first_latter_of_directory<tab>.

---

### Post by morrissey21 on 2007-04-06
cheers guys thats should be enough web pages to keep me going for atleast a couple of hours

---

### Post by Nolander on 2007-04-06
first ill say welcome to the ubuntu community.

if u wanna learn stuff just surf the forum and that mate of yours that got u on to ubuntu sounds like a legend.

have fun,
nolander.

---

### Post by nhandler on 2007-04-06
Here are a few commands to get you started.

cd /path/to/folder
    This changes what directory you are in. You can use an absolute path or relative path (./subfolder). If you type cd with nothing after it, it will take you to your home folder.

ls
   This lists all the files and folders in the directory. You can view hidden files by adding the -a flag. You can also add the path to a folder onto the end to list the files in a different folder.

sudo
       You can put sudo in front of a command to run it as root. It will prompt you for your password after this. When you run something as root, you get full permissions.

nano/vi
        These are 2 popular terminal based text editors

gedit
      This will launch a graphical text editor

sudo aptitude search PROGRAM
      This will search the repositories for a program named PROGRAM

sudo apt-get install PROGRAM
      This will install PROGRAM to your computer

sudo apt-get remove PROGRAM
      This will remove PROGRAM from your computer

sudo apt-get update
     This will update your package listing

sudo apt-get upgrade
     This will upgrade your computer


These should get you started.

---

### Post by jpmswiss on 2007-04-06
thanks from another new linux user!

---

