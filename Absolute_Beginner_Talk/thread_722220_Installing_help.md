---
title: "Installing help"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by GreenSmoke777 on 2008-03-12
Ok hi everyone, right welll i recently got linux and have been learning to use the terminal. I dont have any problem navigating through my directorys but i cant seem to install anything and i was just wondering what the command is to install files.
I have read other posts and tried things like "sudo install flasplayer-installer" but it just says something along the lines of file missing or cant find file.
I know my post is pretty vague at the moment but thats due to me being at work if.If yous need some more information ill be happt to post it a bit later on say around 7 ish.
Any help aprecciated.

---

### Post by NightwishFan on 2008-03-12
If you mean install from the repositories. The main command is:
```
sudo apt-get install *packagename*
```
If you mean other sources, generally there is a readme with instructions.

---

### Post by GreenSmoke777 on 2008-03-12
Ive tried that commadn before nightwish and i got an error.
You see what im trying to do is install a flashplayer i have the unzipped file on my desktop so what i do is open my terminal and type
cd /home/andrew/Desktop/flashplayer
ls -l

then it gives me 2 files, one being flash player installer(wich has a  padlock symbol next to it when i look in the folder) and the ther other being some sort of libflash.so(or something like that)

---

### Post by NightwishFan on 2008-03-12
What type of file is the installer? If you wish to get flash plugin working in firefox, just use:
```
sudo apt-get install flashplugin-nonfree
```
If you mean another type of flash player it would help if I knew which one.

---

### Post by Bölvaður on 2008-03-12
> **GreenSmoke777 said:**
> Ive tried that commadn before nightwish and i got an error.
You see what im trying to do is install a flashplayer i have the unzipped file on my desktop so what i do is open my terminal and type
cd /home/andrew/Desktop/flashplayer
ls -l

then it gives me 2 files, one being flash player installer(wich has a  padlock symbol next to it when i look in the folder) and the ther other being some sort of libflash.so(or something like that)

you are on the right track

cd fla[push tab to finish the word]
sudo ./install fla[push tab to finish the word]

something like that. I think you forgot the period

---

### Post by GreenSmoke777 on 2008-03-12
Im pretty sure i tried that command as well and yeh its just the flash player for firefox i guess ill have to wait until i get back from work to give yous some more information.Ill post my error message later on ok.
Thanks for your time anyway nightwish.

---

### Post by GreenSmoke777 on 2008-03-12
> **Bölvaður said:**
> you are on the right track

cd fla[push tab to finish the word]
sudo ./install fla[push tab to finish the word]

something like that. I think you forgot the period

Right that looks like one i havnt tried ill give that a go when i get home and let you know how it goes.
Thanks mate:)

---

### Post by GreenSmoke777 on 2008-03-12
[PHP]andrew@AndrewsComputer:~$ cd /home/andrew/Desktop/flash_player
andrew@AndrewsComputer:~/Desktop/flash_player$ sudo ./install flashplayer-installer 
Password:
sudo: ./install: command not found
andrew@AndrewsComputer:~/Desktop/flash_player$ cdflashplayer_installer
bash: cdflashplayer_installer: command not found
andrew@AndrewsComputer:~/Desktop/flash_player$ cd flashplayer_installer
bash: cd: flashplayer_installer: No such file or directory
andrew@AndrewsComputer:~/Desktop/flash_player$ 
[/PHP]

This is what i put into the terminal.

---

### Post by jan quark on 2008-03-12
navigate to the directory where you have tried to run.```
/install flashplayer-installer
```

and run only this
```
./flashplayer-installer
```

---

### Post by GreenSmoke777 on 2008-03-12
[PHP]andrew@AndrewsComputer:~/Desktop/flash_player$ ./flashplayer-installer

ERROR: Your architecture, \'ppc64\', is not supported by the
       Adobe Flash Player installer.

andrew@AndrewsComputer:~/Desktop/flash_player$ 
[/PHP]

Well at least i got a new error message.
Any more ideas?

---

### Post by NightwishFan on 2008-03-12
You cannot install it on a PPC. Try my method.
If you are on Ubuntu Gutsy use this command.
```
sudo apt-get install flashplugin-nonfree
```
post the results

---

### Post by GreenSmoke777 on 2008-03-12
[PHP]andrew@AndrewsComputer:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
andrew@AndrewsComputer:~$ cd /home/andrew/Desktop/flash_player
andrew@AndrewsComputer:~/Desktop/flash_player$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
andrew@AndrewsComputer:~/Desktop/flash_player$ 
[/PHP]

Emm, Just getting curious is it worth noting im on my ps3?

---

### Post by Bölvaður on 2008-03-12
not sure. You should have all the same stuff, so it really should be no difference.


```
gummi@kjallari:~$** cd Desktop**
gummi@kjallari:~/Desktop$ **cd install_flash_player_9_linux/**
gummi@kjallari:~/Desktop/install_flash_player_9_linux$ **./flashplayer-installer **

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux.......... more stuff about the install
```


I just installed it successfully.
Btw I just remembered... did you allow this file to be run as a program?

You can do it with chmod or right click the file and go to properties -> permissions -> tic the 'Execute' box.

And.. well if you have it like that I guess you could just double click the file from file browser (Nautilus) and press Run in Terminal.

---

### Post by NightwishFan on 2008-03-13
I think it does matter that it is on a ps3. The thing you downloaded will not install and there seems to be no flash plugin in the repos.

---

### Post by Bölvaður on 2008-03-13
> **NightwishFan said:**
> I think it does matter that it is on a ps3. The thing you downloaded will not install and there seems to be no flash plugin in the repos.

oh yeah omg. well... he could compile it.

I think you need to compile most of the programs that havent been compiled already for you (which might be everything)

so.... if you are able to get the source you could compile it and there wouldn't be a problem. I know you cannot get the one from Adobe, but others??

---

