---
title: "can't play mp3"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by rgp-02 on 2007-01-09
1st ubuntu for me. like it so far, but i'm totally ignorant so bear with me as i may have many ?'s in the near future.
i downloaded an mp3 file to desktop.
how can i play it?

---

### Post by taurus on 2007-01-09
You first need to install codecs before the multimedia would work.  Here's a guide.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by oizhztl on 2007-01-09
Sound & Video >> Rhythmbox Music Player

---

### Post by rgp-02 on 2007-01-09
i went to: 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 

and half of the damn links don't connect, such as: 

"Installing Software"    so i tried Application>Accessories>Terminal and pasted:

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

and got:

p@rgp-02:~$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
rp@rgp-02:~$

---

### Post by 3rdalbum on 2007-01-09
Oooo... looks like someone has edited the RestrictedFormats page to miss out a step.

You must enable the Universe and Multiverse repositories first. Under System > Administration > Software Sources (or Software Properties if you're on Dapper), turn on all the checkboxes for all the repositories listed there. When you quit the program, it should ask you if you want to reload the package information. Yes; do it.

Now your command will work. Note that you can't get paid support from Canonical for packages that are in Universe and Multiverse.

---

### Post by deepbluegene on 2007-01-10
i have same problem that mp3s are not working.i followed the above guide but got the same error
"Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll"

what to do?i have already enabled the repositries.

now when i tried to install gstreamer i got folowing message
"This application is provided by the Ubuntu community.
........... cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

i am getting this message for almost every other package i am trying to install. what could be the problem. i think i will never be able to play mp3 this way
please help
Thanx

---

### Post by paker on 2007-01-10
I got the exactly same message. I checked universe and multiverse repositories. I copied and pasted the command line.

Is there any other program that will work in Ubuntu 6.10 amd64?

Thanks.

---

### Post by ComplexNumber on 2007-01-10
> **paker said:**
> I got the exactly same message. I checked universe and multiverse repositories. I copied and pasted the command line.

Is there any other program that will work in Ubuntu 6.10 amd64?

Thanks.
did you type 'sudo apt-get update' afterwards you'd enabled the extra repos?

---

### Post by migla on 2007-01-10
There's the automatix thingy for installation of some things that are and some things that are not in the repositories: [http://www.getautomatix.com/](http://www.getautomatix.com/)

(edit: not that that is needed for the codecs, but the codecs are there. I just got it for easy installation of dc++ for linux...)

---

### Post by deepbluegene on 2007-01-11
i am using i386 and most of the packages are not supposed to be for i386.
what are the alternatives to play  diff media format(restricted ones)

please help
thanx

---

### Post by paker on 2007-01-11
> **ComplexNumber said:**
> did you type 'sudo apt-get update' afterwards you'd enabled the extra repos?

After enabling Multiverse and Universe repositories, I copied and pasted the command line from [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats). 

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

And this is the message:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll

Do you suggest that I still "sudo apt-get update"?
Thanks.

---

### Post by migla on 2007-01-11
> **paker said:**
> Do you suggest that I still "sudo apt-get update"?
Thanks.

Yes.

The "sudo apt-get update" command will download and read the lists of available packages from the repositories in the /etc/apt/sources.list so you should run the update command in order for your computer to realize that there are new repositories and their packages available, as I understand it.

edit: "sudo apt-get upgrade" in turn, will upgrade packages that have updates available (which the computer will be aware of if you have done "sudo apt-get update" and there are packages with higher versions available).

---

### Post by Pixilarion on 2007-01-11
> **migla said:**
> There's the automatix thingy for installation of some things that are and some things that are not in the repositories: [http://www.getautomatix.com/](http://www.getautomatix.com/)


When this is your first time with Ubuntu/Linux, Automatix is the way to go! Anyone who can handle a mouse and can (carefully) read, should be able to get things working. :)

---

