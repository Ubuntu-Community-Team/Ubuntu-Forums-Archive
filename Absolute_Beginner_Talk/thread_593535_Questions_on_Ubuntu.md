---
title: "Questions on Ubuntu"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Simple512 on 2007-10-27
Hello, not sure if ya guys remember me from about a month ago i finally got around to installing linux ! 

Version: Linux 7.04 Desktop Edition (download .iso and burned to disc ) 

I boot from the boot menu and there is generic ubuntu 7.04, safe mode, mem test x86 and then windows xp. I just boot from generic is that ok ?

And so far, everything looks good, it installed in 10 minutes compared to MS 1 hour long installation. But there is alot of confusion that i knew would occur just like any other foreign application you use for the first time. 

Some of my questions :) 

1) Firefox works (obviously) but under tools there is no settings option that i can go into and change certain settings i use under XP. Where is it ? 

2) I need some good beginner reading material, because i know this is a long road and need some good links to things like ( using terminal, how the hell to install programs, etc.)

3) I got a little update icon that popped up for firefox and it was the flash player 9 manual installation. I downloaded the archived file and extracted it. There is a ( flashplayer.xpt, flashplayer-installer, libflashplayer.so ) What do i do ? 

4) I was reading this tutorial in hopes it would help me with installing but some of the commands he uses for navigating directories dont work in 7.04. I believe he was using 6.06 or something. Such as this snippet from the article 

> To see a list of files and directories inside the current directory, run the command ls

When i type in Is in the terminal, it tells me ( bash: Is: command not found ) 

So im guessing there is new commands ? Also in the article it tells me to use, Synaptic Package Manager. I launch it, and search for flashplayer-installer and it returns nothing. Now the article says to search for packages. To bad the author doesnt tell you what a package is ( frustrating ! :) ) 

5) Im using XF-I SoundBlaster Xtreme Music Audio Card. I went and downloaded the drivers for it and heres what is in the folder ( Disclaim.txt, installer, License.txt, Readme.txt, XfiDrv_linux_US-1.04.tar.bz2) What do i do to install these audio drivers. I have no sound at all and if i try to run a video an error pops up saying no sound or something but it will play the video ( im half way there ! ) 

6) Can someone link me to the huge information site on ubuntu. Someone linked it to me before, its like a bunch of how to do this and this and that. 

7) I made the stupid mistake of importing my XP user account ( it asks if i want to in the ubuntu installer ) and i did. I cant do anything with it because its all windows apps, and it imported the Windows folder ??? (why would it do this i dont have a need for Windows folder ) How do i delete the imported xp user account. I think its taking up alot of space and i cant use it so please help me with this.

Thanks thats about it for now, i appreciate how helpful you guys are to us beginners. Ubuntu isnt as user friendly as Windows so im not used to installing programs through a command prompt.

---

### Post by stomponthis on 2007-10-27
> **Simple512 said:**
> 1) Firefox works (obviously) but under tools there is no settings option that i can go into and change certain settings i use under XP. Where is it ?
Try looking under Edit - Preferences
Maybe it changes by what version you are using of Firefox... I am not sure 
Check out this site it has heaps of great stuff for new users
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

---

### Post by Simple512 on 2007-10-27
> **stomponthis said:**
> Try looking under Edit - Preferences
Maybe it changes by what version you are using of Firefox... I am not sure 
Check out this site it has heaps of great stuff for new users
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

THANKS ! it was under edit preferences and thats the site i was looking for ty ty ty

now can anyone answer some of my other questions very good feedback :D

---

### Post by Anzan on 2007-10-27
> **Simple512 said:**
> 
4) I was reading this tutorial in hopes it would help me with installing but some of the commands he uses for navigating directories dont work in 7.04. I believe he was using 6.06 or something. Such as this snippet from the article 



When i type in Is in the terminal, it tells me ( bash: Is: command not found ) 

You need to say what you want to "ls".

For example:

you@yourbox:~$ ls /.

returns something like

bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old

---

### Post by Daveth on 2007-10-27
this is worth looking at as well

[https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html)

it is LS in lowercase, it you type man ls in a terminal it will tell you all the flag options you can use with it. ls -l is a popular one to try.....

That X-Fi card driver is very very beta and a 64 bit one if I'm not mistaken- I know you have the card but I would be very wary of that.

flashplayer- nonfree will get you there

look around

[https://help.ubuntu.com/community/HowToGetHelp](https://help.ubuntu.com/community/HowToGetHelp)

---

### Post by Pumalite on 2007-10-27
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by mikewhatever on 2007-10-27
Adobe's flash is in the repositories. Just open Applications>Add/Remove and search for flash. The package name is flashplugin-nonfree, if you are interested.

---

### Post by mdpalow on 2007-10-27
hi,

At first, installing software not in the Synaptic Package Manager (SPM) was difficult. However, I found a link that helped me assuming the downloads were correctly made to install.

Try this:

[http://monkeyblog.org/ubuntu/installing/#package_manager](http://monkeyblog.org/ubuntu/installing/#package_manager)

This link discusses SPM, debian, RPM, and others I believe.

I don't know what you're trying to install, but if it's programs - look at this link. If you find something you want to install - use SPM to find it and install.

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

I have yet to find any program that I used on Window$ that I can't find in SPM.

Good luck,

---

### Post by Simple512 on 2007-10-27
thanks everyone !

---

