---
title: "Corrupt installation?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by NotGrayt on 2006-04-28
I thought I'd successfully installed the program (from CD), but I have several items that when selected (System - Administration - **Synaptic package** manager or  System - Administration - **Update Manager** or **User and Groups**) appear as if they are going to load, but nothing happens.  I think the update manager is running as there is an icon on the top of the screen, and when right clicked shows options to download and show updates amoung other things, but clicking on any of them results in the same no response result.  No error messages, and sometimes I am prompted for a password for some programs and I type it in and no errors reported and no program runs.  The system is able to get to the internet with Firefox, and I can see my file system, many games installed and OOO apps work.  I only have one account configured (not root) and am wondering if my installation might be faulty as I can find no similar accounts in the forums.  This is my first linux experience, and am struggling.  I have little experience with the konsole as well.  Any ideas or thoughts are appreciated.:-k

---

### Post by dave9191 on 2006-04-28
You should only have one account configured. In ubuntu the root account is disabled. 

And try launching these programs from a terminal and see if they generate any error messages. Try 

sudo synaptic

and type your password. 

--
Dave

---

### Post by NotGrayt on 2006-04-28
Yea I only have one account configured.  Her'e the output from the terminal after typing in my password
labprint is not in the sudoers file.  This incident will be reported.
tried to do it again and no response

---

### Post by browndog on 2006-04-28
Since you are brand new to Linux it's important that you not give up hope and have plenty of patience while you're learning...this forum is one of the best places to do it.  Ok, for a newbie I would suggest that you use only the Synaptic Package Manger to start with for installing software.  Ubuntu Linux gets it's software from online repositories, and you have to enable all of these repositories in the Synaptic Package Manager in order to have the widest available selection of programs to install.  On the top menu bar of Ubuntu click on System --> Administration --> Synaptic Package Manager. Type your password when it asks you and then you're in. Once inside click on Settings --> Repositories to get into a screen where you can enable all the online repositories. To enable a repository highlight it and click on "Add". Once you've added all the repositories go back to the main Synaptic Package Manager page and click on the Search button. Type in the name of the software you're looking for and click search. When your software title comes up, click on its box in the right hand panel and select "mark for installation", then click "apply" at the bottom. When it finishes installing close the package manager.  After that you can start the program up by clicking on it's name under the applications menu.

---

### Post by NotGrayt on 2006-04-28
I apprecaite your patience and this forum.  As I may have not made clear, I am not able to open Synaptics, along with many other features.  I click on them and nothing happens.  :confused: Thats whats so weird.

---

### Post by YuHoo on 2006-04-28
I suspect that you're using KUbuntu since you're using Konsole. I don't use KDE so I don't know everything (because I know everything there is to anything :mrgreen: ) that there is to it. I would suggest that you attempt to install certain things through the console. 

Run "sudo apt-get update" and see if it refreshes your sources, sometimes it's stupid weird things that fix other problems. After that is done try downloading and installing trough the console. This is done through sudo apt-get install name-of-program-listed. I'm interested in if this is corrupted as well, if it is, reinstall. For good programs to test try build-essentials, amarok, and vlc. 

To learn more about Ubuntu check out this page [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) I love it. Also look toward checking out Gnome, it's pretty fast and I enjoy how it just feels out of the way. But if you've got a question, type it into the search and then post it, it's usually answered in the first hour or so (but sometimes it's a real stumper). Cheers

---

### Post by NotGrayt on 2006-04-28
Thanks Yuhoo, I am using Breezy Badger - Release 5.10.  I do believe I tried this (not sure), and I believe the command is run but just get the prompt.  I will give your advice a try on Monday as this is a work computer.  I'll post results then.  Have a good weekend in Wisconsin, (I'm in Mpls) rain expected! ;)

---

### Post by dave9191 on 2006-04-28
Hey, 

It sounds like you have a problem that i have read about from time to time on these forums. I am not sure what causes it tho. 

A little background. In ubuntu you don't use the root account, you use sudo instead. Sudo is a mechansim which allows you to run root commands from your own login using your own password. 

In order for this to work, your account needs to be in the sudoers file so that the systems knows you are allowed to run root commands. But for some reason your username isnt in the file. It should be put in there during install automatically. 

Because you can't use sudo, synaptic or anything else that needs root access will not work. 

Did you try and create a new user account other then the one during the install? If thats the case, then the account you created isn't added to the sudo list. 

The simplest thing to do (assuming you haven't done much on ubuntu since you installed it) is to reinstall. That should fix the problem. An alternative is to add yourself to the sudoers file ([http://www.ubuntuforums.org/showthread.php?t=162353)](http://www.ubuntuforums.org/showthread.php?t=162353)). The last post goes into a little detail about that. But that required a little linux terminal magic, so if you are new I'm not sure if you want to get in that deep yet. 

--
Dave

---

### Post by NotGrayt on 2006-05-01
Well it appears Dave was right about the sudo file being messed up.  I booted into recovery mode, typed visudo, and added  "username All=(ALL) ALL and rebooted.  I'm able to now access my updates.  I'm glad I did't have to reinstall as I got to learn more from this then if I hadn't found out what the problem was.  I'd like to thank you all for your expediant replys and suggestions.  You all should be proud of your forum and the group of people you attract.  I'm sure I'll be back, thanks

---

### Post by dave9191 on 2006-05-01
Hey, glad I could help and you got your problem sorted :)

--
Dave

---

