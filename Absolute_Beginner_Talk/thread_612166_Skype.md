---
title: "Skype"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-13
How might i go about getting this?

---

### Post by rudeboyskunk on 2007-11-13
Go to [www.skype.com](www.skype.com), downloads, and click the download for ubuntu (it says feisty fawn, but it works in gutsy gibbon as well).  Or you can enable the medibuntu repository and install it from synaptic (go to [www.medibuntu.org](www.medibuntu.org) to see how to do this).

I use skype, it is awesome.  If you use the beta version it has webcam support.

---

### Post by p_quarles on 2007-11-13
Do not run that command. (the one in the first response) It will delete your home folder. EDIT: Okay, the spam post was deleted. Carry on. 

You can get skype by adding the "partner" repository (I believe) in Synaptic, and then running a search for it.

---

### Post by shad0w_walker on 2007-11-13
**DO NOT RUN THAT COMMAND!**

It is a spammer who is trying to nuke your system.

---

### Post by jordank on 2007-11-13
I did it. what does it do? didnt read on. shitty.

---

### Post by jordank on 2007-11-13
ahha. shitty. totally got me.
Steps from here?

---

### Post by rudeboyskunk on 2007-11-13
best bet is probably to reinstall ubuntu.  BUT WAIT TO SEE WHAT OTHERS SAY before you do that.

---

### Post by p_quarles on 2007-11-13
> **jordank said:**
> ahha. shitty. totally got me.
Steps from here?
Yeah, he got you. Not a lot you can do to undo it, but you can try to look for some data recovery tools. In the meantime, if you see a post like that, please immediately click on "report" to notify the forum staff. Maybe you can help prevent it from happening to other people.

In general, never execute a command if you aren't sure what it does. You can find out what a command does, in general, by typing:
```
man *command*
```

---

### Post by jordank on 2007-11-13
my props to the spammer on that. that was sneaky. good learning thing though.

---

### Post by shad0w_walker on 2007-11-13
I'm afraid your rather out of luck. It deletes all the files on your harddrive. There maybe a way of recovering them however I am not sure of it. You should be able to keep running until you reboot, then you are out of luck. The easiest option other than recovery is reinstalling.

---

### Post by Sef on 2007-11-13
Use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover what you lost.

---

### Post by jordank on 2007-11-13
okay, so before i got nuked i was wondering how to get skype up and running.  I did a complete reinstall and have all my settings back to normal. if anything it improved my comp.  Now.. how do i get skype?

---

### Post by p_quarles on 2007-11-13
Earlier I said that you would need to enable the "partner" repository, but that was incorrect. You actually need the Medibuntu repository. Instructions for enabling it in the link:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jordank on 2007-11-13
Thank you, i'll check it out.

---

### Post by jordank on 2007-11-13
hrmm, i followed the instructions there, and it referred to me to another site, the medibuntu package pool.
[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)
is the link to the skype, but i have no idea what to do with packages like that.  my first question is:
i thought skype was free? why is it under the non-free section
What do i do with tar files? 
what is the .deb file extension? also .gz?
which file out of that list would i want if i wanted to install skype? i don't have the slightest idea what all of the files listed are. 
I just want skype!

---

### Post by p_quarles on 2007-11-13
Skype is free in that it costs no money, but isn't open source, so it's not "free" in the sense that Ubuntu means. 

Anyway, what I actually meant was to run the command under "Adding the repositories" in the link I gave you. Once you run those commands, Skype will automatically show up in Synaptic when you search for it. 

If you just want to download the package directory, you can get the ones that ends in ".deb." I believe you'll need skype-common, skype-static, and plain skype for the full installation. Just make sure you get the same version number for each package. Once you've downloaded them, they can be installed by double-clicking on the files, and entering your password. 

The first way is easier, though, I think.

---

### Post by jordank on 2007-11-13
after installing skype, where does it generally appear?
I checked all of the submenus of applications, and did not see any skype.
where is he?

---

### Post by p_quarles on 2007-11-13
I'm using KDE, which has a slightly different menu setup, but for me it appears under Internet applications. You can also run it by typing the command "skype."

(you can also manually add a menu item that runs this command, using the menu editor)

---

### Post by TadH on 2007-11-14
just out of curiosity what was the command the spammer told him to type, u can pm it to me.

---

### Post by jordank on 2007-11-14
it was like 
sudo rm -rf /
but please, do NOT type that.

---

### Post by jordank on 2007-11-14
Hrmm, i got skype working, but it doesn't seem to support video.  Does anyone know if the version stated in this thread supports webcam?

---

### Post by trash on 2007-11-14
I downloaded it from the Skype website and then double clicked on it and it installed no problem

---

### Post by jordank on 2007-11-14
from the skype website? you didnt get yours from synaptics? and does it have webcam support?

---

### Post by trash on 2007-11-14
> **jordank said:**
> from the skype website? you didnt get yours from synaptics? and does it have webcam support?

It's only the beta that offers cam... [http://skype.com/intl/en/download/skype/linux/beta](http://skype.com/intl/en/download/skype/linux/beta)

---

### Post by mikewhatever on 2007-11-14
> **jordank said:**
> Hrmm, i got skype working, but it doesn't seem to support video.  Does anyone know if the version stated in this thread supports webcam?

The current stable version of skype for linux has no video support.

---

### Post by nikolas68 on 2007-11-14
I did this to install Skype and it works no prob:

Using Skype's apt repository

```
1. As the root user, add this line to the end of your /etc/apt/sources.list file:

deb http://download.skype.com/linux/repos/debian/ stable non-free

2. Then run apt-get update to sync to the latest repository and
apt-get install skype to install the latest version of Skype on your computer.
```

---

### Post by jordank on 2007-11-14
still no webcam support. urgh.
what do people on ubuntu use for webcamming?

---

### Post by trash on 2007-11-14
you're going to have to give some more details about what you are doing because several people have already confirmed it works haha

---

### Post by p_quarles on 2007-11-14
So you downloaded the Skype 2.0 beta, and you still can't get webcam to work? Skype 2.0 *does* support video conferencing, so the software isn't likely the problem.

Does the webcam work with any other applications? I ask because some webcams just don't have support in the Linux kernel.

---

### Post by jordank on 2007-11-14
Went here
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
enabled the medibunto repository
went to synaptics, searched skype
installed both applications that came up, namely:
skype static
and
skype common

is this NOT the beta?
what i have in my applications>internet>skype does not support webcam.

---

### Post by p_quarles on 2007-11-14
The link that trash gave you will go directly to where you can download the latest version, which does support webcams. Choose the Ubuntu version, and once it's downloaded you can install it by clicking on it.

EDIT: Or, alternately, you can add Skype's repository by following nikolas68's instructions.

---

### Post by jordank on 2007-11-14
i deleted any skype related things i had on my computer, and attempted to take the approached suggested above. i went to
[http://skype.com/intl/en/download/skype/linux/beta/](http://skype.com/intl/en/download/skype/linux/beta/)
but after downloading, i double click the .deb file and the package installer window appears. However, in bold red writing it says:
Error: Wrong architecture 'i386'
what does this mean?

---

### Post by jordank on 2007-11-14
i tried nikolas' method aswell, but it failed to find the repository.

---

### Post by p_quarles on 2007-11-14
> **jordank said:**
> i tried nikolas' method aswell, but it failed to find the repository.
Here's the step by step version of what nikolas68 said:
```
gksudo gedit /etc/apt/sources.list
```
and add this line to that file:
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```
Then, run the following three commands:
```
sudo apt-get update
sudo apt-get install skype
sudo apt-get upgrade
```

---

### Post by jordank on 2007-11-14
I did exactly what you just said to do, and the last couple lines after 
sudo apt-get update are:

Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz) 404 Not Found [IP: 198.173.5.11 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

however, i ignored that and continued to proceed through your instructions.
After all the steps i'm left with the exact same version of skype i had before. it's not beta, and does not support webcams.
As i said above, it does not seem to find the repository that nikolas mentioned.

---

### Post by p_quarles on 2007-11-14
Yeah, that site appears to be down or outdated. Let's go back to the first method (downloading the installer). 

It said you have the wrong architecture. Can you post the output of this?:
```
uname -a
```

---

### Post by jordank on 2007-11-14
Linux Jorcomp 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

---

### Post by p_quarles on 2007-11-14
> **jordank said:**
> Linux Jorcomp 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
Thought so. You're using the 64 bit version of Linux, and the Skype beta hasn't been ported to that yet. 

Your options are:
1) Wait
2) Install 32 bit Linux (which runs fine on 64 bit processors)
3) Force it to install.

The first option is reasonable if you don't *need* video. The second option is the best if you do. The third option is kind of risky, and not at all guaranteed to work (though not as risky as that other command).

---

### Post by jordank on 2007-11-14
what would be the difference between 32 and 64 bit linux?
and how would i force it to install?

---

### Post by p_quarles on 2007-11-14
> **jordank said:**
> what would be the difference between 32 and 64 bit linux?
and how would i force it to install?
They're different architectures. You probably have an AMD CPU, and downloaded the Ubuntu version for that. The Intel (i386) will also work with the AMD processor, though, and you'll be able to install Skype. 

Like I said, forcing it to install is a bit dangerous, and not guaranteed to work. Don't do this unless you're prepared to reinstall the system again. Go to the directory in which you downloaded the package and:
```
sudo dpkg -i --force-architecture skype-debian_2.0.0.13-1_i386.deb
```
This could potentially damage your system, and this advice comes with no warranty. ;)

---

### Post by jordank on 2007-11-14
I've got an intel chip. core2duo centrino.
Should it be working?

---

### Post by p_quarles on 2007-11-14
Core 2 Duo is a 64-bit chip, but just like with AMD, it will also support the 32-bit operating system. My point was that you have the 64-bit version of Ubuntu installed, and that's why Skype doesn't want to install.

---

