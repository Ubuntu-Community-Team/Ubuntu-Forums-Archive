---
title: "installing software"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by ckonrad on 2006-05-23
I dont understand why i cant install anything under linux. I follow the directions in my book or from websites and people i speak with on the forums but nothing works. No matter what commands i use i always get the error "directory doesnt exist. What am i  missing. THis happens to me on any version of linux i have tried out. I have a huge book on linux that weighs like 5 lbs lol and i cant find an answer to my question in it. The directions for installing software are always so simple. Just type this and this and this + the file name and it will install, well it never does. What directory am i supposed to have files in in order to get them to install from the command like? I just dont get it. This has been going on for about 20 days now and no information i get from the forums here or from any book i have has helped at all, is there anyone that can lend me a hand here. 

Thanks

---

### Post by bluevoodoo1 on 2006-05-23
Have you by any chance seen this link?
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by aysiu on 2006-05-23
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by alphaomega on 2006-05-23
[QUOTE=bluevoodoo1]Have you by any chance seen this link?
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)[/QUOTE]

[QUOTE=peterj]ok trying to work out java.
uninstalled that rubbish blackdown 1.4 version.
installed java 1.5 through the repository.
now when I go onto my favourite site...[www.funkypool.com](www.funkypool.com)
i get 'plugin required.
firefox doesnt recognise me as having any java through the about:plugins command.
maybe I haven't installed it at all?
normally when I do it through the add/remove programs it does it all for me I think
thanks[/QUOTE]

that is the beesknees when it comes to a how to.

---

### Post by ckonrad on 2006-05-23
[QUOTE=bluevoodoo1]Have you by any chance seen this link?
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)[/QUOTE]

well lets take it step by step how do i install the program in the link below, there are several linux distros for it but everyone i try doesnt install so i must be doing something wrong. 

[http://www.jahshaka.org/](http://www.jahshaka.org/)

---

### Post by ckonrad on 2006-05-23
[QUOTE=alphaomega]that is the beesknees when it comes to a how to.[/QUOTE]

i dont know what beesk nees is i am just trying to understand how to install programs i download, i think you put this post in the wrong place or something.

Thanks

---

### Post by aysiu on 2006-05-23
I don't know what the dependencies are for this program, but this is theoretically how it should be installed.

Paste these commands into a terminal: ```
sudo apt-get update
sudo apt-get install build-essential
cd
wget -c http://easynews.dl.sourceforge.net/sourceforge/jahshakafx/jahshaka-2.0.0.tar.gz
tar -x -z -v -f jahshaka-2.0.0.tar.gz
cd jahshaka
./configure
make
sudo make install
```

---

### Post by ckonrad on 2006-05-23
ok but, one thing that i dont understand is why i cant change directories with commands like cd. If i have a directory called Documents then how am i supposed to change it to that directory in the terminal. I have tried cd documents, cd/documents, cd Documents cd/Documents etc etc but non of them work they all just say no such directory even though i  have a documents directory which i installed my programs. non of the code you ask me to display in my terminal worked to install that program. I appreciate your help though. I just get a directory doesnt exist error. what directory am i supposed to have files in in order for them to install and how do i change directories if the cd command doesnt work? i must be missing something or doing something wrong.




[QUOTE=aysiu]I don't know what the dependencies are for this program, but this is theoretically how it should be installed.

Paste these commands into a terminal: ```
sudo apt-get update
sudo apt-get install build-essential
cd
wget -c http://easynews.dl.sourceforge.net/sourceforge/jahshakafx/jahshaka-2.0.0.tar.gz
tar -x -z -v -f jahshaka-2.0.0.tar.gz
cd jahshaka
./configure
make
sudo make install
```[/QUOTE]

---

### Post by ckonrad on 2006-05-23
here is what i get from that 

sudo: apt-get: command not found

yet when i type in whereis sudo it certainly exists on my system just doesnt work.






[QUOTE=aysiu]I don't know what the dependencies are for this program, but this is theoretically how it should be installed.

Paste these commands into a terminal: ```
sudo apt-get update
sudo apt-get install build-essential
cd
wget -c http://easynews.dl.sourceforge.net/sourceforge/jahshakafx/jahshaka-2.0.0.tar.gz
tar -x -z -v -f jahshaka-2.0.0.tar.gz
cd jahshaka
./configure
make
sudo make install
```[/QUOTE]

---

### Post by aysiu on 2006-05-23
Instead of describing the errors you get, can you copy and paste exactly what you type into the terminal and exactly what errors you get?

Is this documents folder inside of your home folder or does it exist outside of the home folder?

Can you type these commands in the terminal and paste the commands *and* the output back here? ```
cd
ls
sudo updatedb
locate Documents
locate documents
```

---

### Post by ckonrad on 2006-05-23
well actually i just finished an installation of suse linux that came with a book i bought and not only did it detect all my hardware perfectly wireless works great and i was able to install jahshaksa following the simple directions on there site. i dont know maybe i have a bad ubuntu distro or something its one of those cd's i oredered from ubuntu though and it was brand new.

Thanks for your help though i think i'll stick with suse it seems to work better.


[QUOTE=aysiu]Instead of describing the errors you get, can you copy and paste exactly what you type into the terminal and exactly what errors you get?

Is this documents folder inside of your home folder or does it exist outside of the home folder?

Can you type these commands in the terminal and paste the commands *and* the output back here? ```
cd
ls
sudo updatedb
locate Documents
locate documents
```[/QUOTE]

---

### Post by aysiu on 2006-05-23
[QUOTE=ckonrad]
Thanks for your help though i think i'll stick with suse it seems to work better.[/QUOTE] Awesome! I'm glad you found something that works for you. Best of luck with everything.

---

