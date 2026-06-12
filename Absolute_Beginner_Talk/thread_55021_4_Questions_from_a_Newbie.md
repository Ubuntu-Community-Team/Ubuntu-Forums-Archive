---
title: "4 Questions from a Newbie"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by spnoe on 2005-08-07
Ubuntu is great, I tried SuSe and was impressed but Ubuntu is in my view is on an equal level and considering the money behind SuSe you would think it would be way ahead. So now I stick with Ubuntu. 
Firstly, I decided I wanted to use Korganizer and used packet manager to load and configure. All went well but it does not show up on the application list, any ideas? 

Secondly, I want to change the boot sequence, as I have a dual boot system. How do I do this? Thirdly, downloaded Skype and it downloded to the Archive Manager. What do I do with it now? Will the packet Manager configure automaticly? 

While I am on the subject of programmes, I read Linux format and would like to load programmes from the DVD. Can Ubuntu help me to do this? If so how?
I am sorry that there are many questions but I am sure these will be of interest to other newbies. Thank you in advance for any help that may be given.

Steve ](*,)

---

### Post by Ampersand on 2005-08-07
1)I'm not sure whether KDE programs (like Korganiser) are always listed in the gnome menus. If there's a 'Debian' menu under applications, it might be in there, otherwise you can run it from Applications - run Application'. It should be in the list of known applications.

2)Not sure about that, I'll leave it for someone else...

3)The easiest way to install skype in ubuntu is to go into Synaptic, go to 'Setting - repositories', and click add. In the URI box, put [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) , the distribution is 'stable' and the section is 'non-free' after reloading the package list, skype should be available.

4)I think this will be covered in one of the wiki pages. I'll post it if no-one else has by the time I've found it.
Hope this helps (:
Richard

Edit:

Software on cover disks tends to be the source code in a compressed file. There's a guide on compiling software here: [http://www.aboutdebian.com/compile.htm](http://www.aboutdebian.com/compile.htm) , but basically, you need to start by installing the 'build-essential' package from synaptic or apt-get. 

The files should end in 'tar.gz' or something similar Open the file you want to install with an archive manager (file-roller or ark, I think are the defaults), and extract it to somewhere on your hard drive (in the home directory is usually easiest). Open a terminal, change directory to the folder just created when you extracted the program and type './configure' followed by 'make' and finally 'sudo make install'. If you get errors from running ./configure, check whether you've got all the dependancies installed.

It's usually easier to use apt-get if the software is available in there, since it checks all the dependancies for you and allows you to easily uninstall it later. It's quite useful to be able to install programs from source, though. Good luck (:

Another edit:
The answer to part 2 can be found here: [http://www.ubuntuforums.org/showthread.php?t=53405](http://www.ubuntuforums.org/showthread.php?t=53405)

---

### Post by aysiu on 2005-08-07
[QUOTE=spnoe]Firstly, I decided I wanted to use Korganizer and used packet manager to load and configure. All went well but it does not show up on the application list, any ideas?[/quote] Can you run it, even though it's not in the menu? If so, you can manually add it to the menu using SMEG (also downloadable through Synaptic). Also, have you tried [refreshing the Gnome panel?](http://ubuntuguide.org/#refreshgnomepanel) 

> Secondly, I want to change the book sequence, as I have a dual boot system. How do I do this? I'm not sure what the book sequence is... did you mean boot sequence? Just *sudo gedit /boot/grub/menu.lst*. In that file, there should be a line that says default 0. Change default to 1.

> While I am onb the subject of programmes, I read Linux format and would like to load programmes from the DVD. Can Ubuntu help me to do this? If so how? Are you sure these programs aren't already in the repositories? Even if you [add in extra repositories](http://ubuntuguide.org/#extrarepositories)? Are you on dial-up? Is that DVD made specifically for Ubuntu? What form do the programs take (.deb, .rpm)?

---

### Post by spnoe on 2005-08-11
Just a note to say thanks to you both for your helpful replies. I am sure I'll be back with more questions. I appreciate your time.
Steve :smile:

---

