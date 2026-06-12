---
title: "command less doesn't seem to work"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Rosemere on 2007-07-21
when I type **“ less” **in Terminal this is the response I get:  Missing filename ("less --help" for help)

pete@pete-desktop:~$ file

Usage: file [-bcikLhnNrsvz0] [-f namefile] [-F separator] [-m magicfiles] file...

       file -C -m magicfiles

Try `file --help' for more information.

pete@pete-desktop:~$ 


Could you please direct what I am doing wrong. I am following the  Learning program. when I typed “ls”
that command seemed to work. Also how do I use the command for File.

---

### Post by ardchoille42 on 2007-07-21
You have to use the less command with a filename:

```
less file.txt
```

---

### Post by Rosemere on 2007-07-21
I just typed less Yellow Cotton Afghan  see my results below. This is a file I created in Open Office and I opened to double check.  I also tried with the extension. I am sorry I am  so new.

pete@pete-desktop:~**$ less Yellow Cotton Afghan.txt**
Yellow: No such file or directory
Cotton: No such file or directory
Afghan.txt: No such file or directory
pete@pete-desktop:~$ less Yellow Cotton Afghan.rtf.txt
Yellow: No such file or directory
Cotton: No such file or directory
Afghan.rtf.txt: No such file or directory
pete@pete-desktop:~$

---

### Post by Majorix on 2007-07-21
You have to quote the filename because it contains spaces.

Look at this:
```
less "Yellow Cotton Afghan.txt"
```

---

### Post by Rosemere on 2007-07-21
pete@pete-desktop:~$ less "Yellow Cotton Afghan.txt"
Yellow Cotton Afghan.txt: No such file or directory
pete@pete-desktop:~$ 

Please  see above it didn't work

---

### Post by louieb on 2007-07-21
gota be something simple please post the output of the **ls** command. File names are case sensitive

---

### Post by Rosemere on 2007-07-23
pete@pete-desktop:~$ ls
automatix2.key                            Intel-536ep-443.tgz
Automatix.rtf                             Intel-536EP-4.71.tgz
deluge-torrent_0.5.1-0zachtib1_amd64.deb  intel_536ep_feisty.tar.gz
Desktop                                   jre-1_5_0_12-linux-i586-rpm.bin
Examples                                  jre-6u1-linux-i586-rpm.bin
hplip-2.7.6                               McDonald's Toy Story 2.rtf
hplip-2.7.6.run                           Pete_sSideofBeefOrder.doc
install_flash_player_9_linux              Preferences
Intel-536                                 Screensaver
intel-536EP-2.56.76.0                     skype-1.4.0.74.deb
Intel-536ep-443
pete@pete-desktop:~$ 


[B][I]Please note since I started trying to enter info in Terminal I have managed to disable Add/Remove as well has Synaptic Manager. I get this error in synaptic.
[/I][/B]
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'deb-sr' is not known on line 5 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

If I have things conflicting please give me the steps for Terminal. Using Ubuntu 7.04

---

### Post by Majorix on 2007-07-23
Your problem with Synaptic is nothing related to the terminal or what you did in this thread.

Do this to fix it:
```
sudo gedit /etc/apt/sources.list
```

Then go to line 5. Add a "c" without the quotes after "deb-sr".

```
sudo apt-get update
```

If that still doesn't help, copy and paste that file here and we will help.




About your original question: You REALLY don't have the file you are trying to open with less, so its normal if you can't access it. I am not sure if less will read rtf files, but you can still try this:
```
less "hplip-2.7.6 McDonald's Toy Story 2.rtf"
```
Don't get frustrated if that doesn't work as I am not sure if less will read rtf files. In that case, go and find yourself a .txt file and we can try again.

---

### Post by Rosemere on 2007-07-23
Still no light bulb on.

I did the following steps. Terminal opened and typed in:

Another screen opened which says sources list. I will post the whole list at the bottom to not confuse you what I did.
2. I then copied the whole list into Terminal and I changed on line 4 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe restricted main

[COLOR="Red"]***deb-src***[/COLOR]   Hit enter

3**. then I put the following code in**  sudo apt-get update
Here are my results.

Those two files above that you commented on, one is and Open office document nd the other is the driver for an HP printer. Should they be moved?

pete@pete-desktop:~$ sudo gedit /etc/apt/sources.list
Password:
pete@pete-desktop:~$  See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
bash: See: command not found
pete@pete-desktop:~$ # newer versions of the distribution.
pete@pete-desktop:~$ 
pete@pete-desktop:~$ deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe restricted main
bash: deb: command not found
pete@pete-desktop:~$ deb-src
bash: deb-src: command not found
pete@pete-desktop:~$ c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties
bash: c: command not found
pete@pete-desktop:~$ 
pete@pete-desktop:~$ ## Major  bug fix updates produced after the final release of the
pete@pete-desktop:~$ ## distribution.
pete@pete-desktop:~$ 
pete@pete-desktop:~$ ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
pete@pete-desktop:~$ ## team, and may not be under a free licence. Please satisfy yourself as to
pete@pete-desktop:~$ ## your rights to use the software. Also, please note that software in
pete@pete-desktop:~$ ## universe WILL NOT receive any review or updates from the Ubuntu security
pete@pete-desktop:~$ ## team.gksu gedit /etc/apt/sources.list
pete@pete-desktop:~$ 
pete@pete-desktop:~$ ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
pete@pete-desktop:~$ ## team, and may not be under a free licence. Please satisfy yourself as to 
pete@pete-desktop:~$ ## your rights to use the software. Also, please note that software in 
pete@pete-desktop:~$ ## multiverse WILL NOT receive any review or updates from the Ubuntu
pete@pete-desktop:~$ ## security team.
pete@pete-desktop:~$ 
pete@pete-desktop:~$ ## Uncomment the following two lines to add software from the 'backports'
pete@pete-desktop:~$ ## repository.
pete@pete-desktop:~$ ## N.B. software from this repository may not have been tested as
pete@pete-desktop:~$ ## extensively as that contained in the main release, although it includes
pete@pete-desktop:~$ ## newer versions of some applications which may provide useful features.
pete@pete-desktop:~$ ## Also, please note that software in backports WILL NOT receive any review
pete@pete-desktop:~$ ## or updates from the Ubuntu security team.
pete@pete-desktop:~$ # deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
pete@pete-desktop:~$ # deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
pete@pete-desktop:~$ 
pete@pete-desktop:~$ deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-proposed universe restricted main
bash: deb: command not found
pete@pete-desktop:~$ deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-proposed universe restricted #Added by software-properties
bash: deb-src: command not found
pete@pete-desktop:~$ deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports universe restricted main
bash: deb: command not found
pete@pete-desktop:~$ deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports universe restricted #Added by software-properties
bash: deb-src: command not found
pete@pete-desktop:~$ 
pete@pete-desktop:~$ #AUTOMATIX REPOS START
pete@pete-desktop:~$ 
pete@pete-desktop:~$ deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports multiverse
bash: deb: command not found
pete@pete-desktop:~$ deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports multiverse #Added by software-properties
bash: deb-src: command not found
pete@pete-desktop:~$ 
pete@pete-desktop:~$ 
pete@pete-desktop:~$ 
pete@pete-desktop:~$ deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
bash: deb: command not found
pete@pete-desktop:~$ deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse #Added by software-properties
bash: deb-src: command not found
pete@pete-desktop:~$ 
pete@pete-desktop:~$ 
pete@pete-desktop:~$ 
pete@pete-desktop:~$ 
pete@pete-desktop:~$ #AUTOMATIX REPOS END
pete@pete-desktop:~$ deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
bash: deb: command not found
pete@pete-desktop:~$ deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security multiverse universe restricted main
bash: deb: command not found
pete@pete-desktop:~$ deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security multiverse universe restricted #Added by software-properties
bash: deb-src: command not found
pete@pete-desktop:~$ deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates multiverse universe restricted main
bash: deb: command not found
pete@pete-desktop:~$ deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates multiverse universe restricted #Added by software-properties
bash: deb-src: command not found
pete@pete-desktop:~$ deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
bash: deb: command not found
pete@pete-desktop:~$ deb http:// archive.ubuntu.com/ubuntu/feisty main
bash: deb: command not found
pete@pete-desktop:~$ deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
bash: deb: command not found
pete@pete-desktop:~$ sudo apt-get update

If you want the total source file this is it:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe restricted main

deb-sr

c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties



## Major  bug fix updates produced after the final release of the

## distribution.



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.gksu gedit /etc/apt/sources.list



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse



deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-proposed universe restricted main

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-proposed universe restricted #Added by software-properties

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports universe restricted main

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports universe restricted #Added by software-properties



#AUTOMATIX REPOS START



deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports multiverse

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports multiverse #Added by software-properties




deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse #Added by software-properties




#AUTOMATIX REPOS END

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security multiverse universe restricted main

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-security multiverse universe restricted #Added by software-properties

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates multiverse universe restricted main

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates multiverse universe restricted #Added by software-properties

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

deb http:// archive.ubuntu.com/ubuntu/feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by davidjmayo on 2007-07-23
with regard to the last post only:

there were/still are? problems with the canada repos yesterday.
see here #4 & #6 [http://ubuntuforums.org/showthread.php?t=506939&highlight=canada](http://ubuntuforums.org/showthread.php?t=506939&highlight=canada)

---

### Post by louieb on 2007-07-23
As you have found out by now the less command did not display anything because there is no file by that name. 

apt and Synaptic are complaining because 
```
deb-sr

c http://ubuntu.mirrors.tds.net/pub/ubuntu/ feisty universe restricted #Added by software-properties

```should read 
```
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ feisty universe restricted #Added by software-properties

```btw: to edit the sources file the command should be:
```
gksudo gedit /etc/apt/sources.list
```

---

