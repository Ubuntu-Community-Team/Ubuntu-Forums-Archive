---
title: "[SOLVED] Arch Linux"
date: 2008-09-04
forum: Arch and derivatives
---

### Post by Elephantman5 on 2008-09-04
Hello. I have the guide for installing Arch linux, and all goes well, (so far).

I just don't know what to press  when, I try to install GRUB  with the installer, and it wants me to view the file before it installs it.
Then the black screen comes up showing me the text version of GRUB, but I don't know how to get out of it. I tried every button I can think of.
What am I missing here?

---

### Post by Locutus_of_Borg on 2008-09-04
hold control and press X
then press Y
then press enter



if you dont know how to use nano, you really should not be trying to use Arch


maybe gentoo is more to your liking

;p

---

### Post by Elephantman5 on 2008-09-04
So, this wasn't in my guide but, 

[http://wiki.archlinux.org/index.php/Quick_Archlinux_Install](http://wiki.archlinux.org/index.php/Quick_Archlinux_Install)
```

"Press Strg-O, then Strg-X, and everything will be saved. "
```

What does that mean????

---

### Post by Elephantman5 on 2008-09-05
> **Locutus_of_Borg said:**
> hold control and press X
then press Y
then press enter



if you dont know how to use nano, you really should not be trying to use Arch


maybe gentoo is more to your liking

;p

Hey, paultag told me to jump in when the water's the coldest.
He mentioned LFS like it was possible for me to do it.

Thanks dude. :)

---

### Post by Locutus_of_Borg on 2008-09-05
im sure it is possible

i only mentioned gentoo because it pwns arch linux 

just be sure you are not installing either onto the only computer you can access the internet with.

---

### Post by handy on 2008-09-05
Arch has great documentation, (so does Gentoo :-)) & is very quick & simple to install, especially when compared to a 3 day Gentoo installation.

You just need to use the console & a console driven text editor such as nano or vi(m).

As previously mentioned, it certainly helps to have another machine connected to the web to access information, the same machine with a web connection makes it a bit more inconvenient, but certainly possible, even if you have to use a liveCD to do it.

Enjoy.

---

### Post by crimesaucer on 2008-09-05
> **Elephantman5 said:**
> So, this wasn't in my guide but, 

[http://wiki.archlinux.org/index.php/Quick_Archlinux_Install](http://wiki.archlinux.org/index.php/Quick_Archlinux_Install)


This is not the best guide for installing Arch. It's say's that it's outdated.


Check out this guide: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
and this guide: [http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)


and more Archlinux wiki info: [http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)


..... and one of my favorite guides (even though this is an old one also) is this 10 page "easy-to-follow" install tutorial that has pictures for most all of the important steps: [http://www.raiden.net/?cat=2&aid=276](http://www.raiden.net/?cat=2&aid=276)


I also like to use the "FTP" install if you have hardware that you know works with Linux, and a working Internet connection. 


The steps of a FTP install are basically the same, it's just faster and you don't have to upgrade anything after the install because you already install the newest packages from the FTP mirror instead of the base packages off of the disk.


Don't be scared of nano, it's really easy to use, just don't select vim. When you use nano, it's basically just moving your cursor with the up/down/left/right arrows, and when you want to save your edited file, press "control + o" and then the enter button to save the file as the name it already had when you opened it (for example: rc.conf), and then to exit from nano press "control + x".


That is about all you need to know about using nano. Read the 10 page tutorial and it will show you what files you have to edit with nano, and what to check for or add/edit.

---

### Post by Elephantman5 on 2008-09-05
> **crimesaucer said:**
> This is not the best guide for installing Arch. It's say's that it's outdated.


Check out this guide: [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
and this guide: [http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)


and more Archlinux wiki info: [http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)


..... and one of my favorite guides (even though this is an old one also) is this 10 page "easy-to-follow" install tutorial that has pictures for most all of the important steps: [http://www.raiden.net/?cat=2&aid=276](http://www.raiden.net/?cat=2&aid=276)


I also like to use the "FTP" install if you have hardware that you know works with Linux, and a working Internet connection. 


The steps of a FTP install are basically the same, it's just faster and you don't have to upgrade anything after the install because you already install the newest packages from the FTP mirror instead of the base packages off of the disk.


Don't be scared of nano, it's really easy to use, just don't select vim. When you use nano, it's basically just moving your cursor with the up/down/left/right arrows, and when you want to save your edited file, press "control + o" and then the enter button to save the file as the name it already had when you opened it (for example: rc.conf), and then to exit from nano press "control + x".


That is about all you need to know about using nano. Read the 10 page tutorial and it will show you what files you have to edit with nano, and what to check for or add/edit.

Funny, because that's what I selected the first time: vim.
That's why I didn't know what to do. I'm not scared of nano, it had all the keys to press at the bottom of the screen.
I've got all the links you showed me. Dude, thanks a lot! I'll post back with my experience. :)

--
I exited the grub file, and select the drive to boot from and I get an error. Check ttyl something.
I'm looking into it.

---

### Post by Elephantman5 on 2008-09-05
Not for me, I hated it. (gentoo)
Took forever to install, and then rebooted into a virtual console.
Funny, because I specifically install a window manager, and I don't know what to do to get out of a virtual console, or start a window manager.
Why wouldn't it start with the system. Seems pretty common sense to me.
Every time I try something else I run back to ubuntu and cry myself to sleep. Not really.
But.

Yeh, I got the error, and I CANNOT INSTALL GRUB. Or Lilo.


> **Locutus_of_Borg said:**
> im sure it is possible

i only mentioned gentoo because it pwns arch linux 

just be sure you are not installing either onto the only computer you can access the internet with.

---

### Post by handy on 2008-09-05
This great Arch installation video guide by ***[miggols99]("http://bbs.archlinux.org/viewtopic.php?id=52327")*** is worth a look, even if as a primer for an Arch virgin:

***_[http://video.google.co.uk/videoplay?docid=6213347420565640601](http://video.google.co.uk/videoplay?docid=6213347420565640601)_***

---

### Post by Elephantman5 on 2008-09-05
Well, I ended up doing it again, and I don't know why but this time I was able to install the GRUB bootloader. So yay to that.
Let's see here.

I followed through the installation, in updating, install xorg, creating a user, installing ALSA, 
Now I'm at installing nvida. I run pacman -S nvida (Geforce 8500 what I have) and it installs, asks if I should delete this other thing because it conflicts, so I say yes.
And when I make the configuration file:

X -configure 
and test it. 
I get this image: 
[[IMG]http://img401.imageshack.us/img401/2522/img3032bz9.th.jpg[/IMG]]("http://img401.imageshack.us/my.php?image=img3032bz9.jpg")

So I go into the conf file and look, and all the info is there. The error is pointing elsewhere (you can see in the image) but I don't know what to do.
I updated. Didn't do anything. I reinstalled nvidia, didn't do anything.

Any suggestions?

I'm running on a live cd right now, I'll just leave this on until someone can get to this.
All the help is appreciated. I love being a part of this community.

---

### Post by kpkeerthi on 2008-09-05
Here is what I did to get my xorg.conf setup:

1. Installed nvidia driver in Arch
2. Booted with Ubuntu** Live **CD and copied Ubuntu's xorg.conf to my flash drive.
3. Now booted into Arch and replaced the xorg.conf with Ubuntu's from the flash drive.
3. Ran nvidia-xconfig (in root's console) or you could just change "nv" to "nvidia" in the xorg.conf that you just copied over.
4. Reboot Arch
5. Nirvana!

---

### Post by Rumor on 2008-09-05
How did you generate your xorg.conf file? If you have run ```
pacman -S nvidia xorg
``` then you can run ```
nvidia-xconfig
``` to generate the file.

Or you can try hwd to generate the file: 
```
pacman -S hwd
hwd -u ##answer yes to the update questions##
hwd -xa
```

Let us know how you make out!

---

### Post by Elephantman5 on 2008-09-05
> **kpkeerthi said:**
> Here is what I did to get my xorg.conf setup:

1. Installed nvidia driver in Arch
2. Booted with Ubuntu** Live **CD and copied Ubuntu's xorg.conf to my flash drive.
3. Now booted into Arch and replaced the xorg.conf with Ubuntu's from the flash drive.
3. Ran nvidia-xconfig (in root's console) or you could just change "nv" to "nvidia" in the xorg.conf that you just copied over.
4. Reboot Arch
5. Nirvana!

Sounds awesome. I don't have a flash drive, but i have another internal hard drive.
I'll see about trying it that way.
What do you mean "change "nv" to "nvidia" in the xorg.conf that you just copied over."

---

### Post by kpkeerthi on 2008-09-05
> **Elephantman5 said:**
> 
What do you mean "change "nv" to "nvidia" in the xorg.conf that you just copied over."

See [http://gentoo-wiki.com/TIP_Switching_between_the_nv_free_driver_and_the_3D_nVidia_driver#Xorg_configuration](http://gentoo-wiki.com/TIP_Switching_between_the_nv_free_driver_and_the_3D_nVidia_driver#Xorg_configuration)

---

### Post by Elephantman5 on 2008-09-05
> **Rumor said:**
> How did you generate your xorg.conf file? If you have run ```
pacman -S nvidia xorg
``` then you can run ```
nvidia-xconfig
``` to generate the file.

Or you can try hwd to generate the file: 
```
pacman -S hwd
hwd -u ##answer yes to the update questions##
hwd -xa
```Let us know how you make out!

Ok Rumor, thanks for that little pitch. (Missed it in the tutorial) 
Worked.
I did the hwd way, and I tested the xorg and it worked.

[http://wiki.archlinux.org/index.php/Beginners_Guide#Simple_baseline_X_test](http://wiki.archlinux.org/index.php/Beginners_Guide#Simple_baseline_X_test)

I'm at this part now. And it doesn't work. 
_[[IMG]http://img508.imageshack.us/img508/9996/img3033di2.th.jpg[/IMG]]("http://img508.imageshack.us/my.php?image=img3033di2.jpg")_

Says there is no ~/.xinitrc file

---

### Post by mips on 2008-09-05
> **Elephantman5 said:**
> Ok Rumor, thanks for that little pitch. (Missed it in the tutorial) 

Says there is no ~/.xinitrc file

Please follow the wiki to the letter.

You have to create the .xinit.rc as per the wiki.

> 
**startx/xinit** will start the **X** server and clients. To determine the client to run, **startx/xinit** will first look for a .xinitrc file in the user's home directory. In the absence of file ~/.xinitrc, it defaults to the global xinitrc in the xinit library directory; /etc/X11/xinit/xinitrc, which defaults to using the TWM window manager. (Hence, if you invoke startx without a ~/.xinitrc file, a TWM session will start.) Switch to your ***normal, non-root*** user: 
 su yourusername

[LIST]
[*] /etc/skel/ contains files and directories to provide sane defaults for newly created user accounts. The name **skel** is derived from the word **skeleton**, because the files it contains form the basic structure for users' home directories.
[/LIST]
 [COLOR=Red]**Copy the sample xinitrc file from /etc/skel/ to your home directory:  **[/COLOR]
 [COLOR=Red]**cp /etc/skel/.xinitrc ~/**[/COLOR]
Edit the file:  
 nano ~/.xinitrc
and add: 
 exec xterm
So that it looks like this: 
 #!/bin/sh
#
# ~/.xinitrc
#
# Executed by startx (run your window manager from here)
#
exec xterm
# exec wmaker
# exec startkde
# exec icewm
# exec blackbox
# exec fluxbox
*Be sure to have only one uncommented **exec** line in your ~/.xinitrc*. Below, we shall edit this file again to specify the appropriate desktop environment/window manager of your choice. 
Finally, test your configurations by starting **X** as **normal, non-root** user, with: 
 startx
or 
 xinit
You should have an **xterm** session open up. You can exit the **X** Server with Ctrl+Alt+Backspace, or by typing "exit". If you have problems starting **X**, you can look for errors in the /var/log/Xorg.0.log file and on the console output of the console you started **X** from. 



---

### Post by Elephantman5 on 2008-09-05
Ok. So current situation is,
I got gnome installed. And I put the entry in the xinitrc file.
exec startgnome
didn't work
I tried exec startgnome-session

Didn't work. After restart and complete install of gnome. 
When I do startx this error:
[[IMG]http://img99.imageshack.us/img99/3147/img3037uk5.th.jpg[/IMG]]("http://img99.imageshack.us/my.php?image=img3037uk5.jpg")

It's kind of like nothing ever worked in the first place.

---

### Post by Rumor on 2008-09-05
If you're running gnome, you can start it by adding gdm to the end of your daemons array in your /etc/rc.conf file

e.g.
```
DAEMONS=(syslog-ng network blah blah blah gdm)
```

---

### Post by maniheer on 2008-09-05
the gdm in rc.conf method will work, or, its

```

exec gnome-session

```

---

### Post by sub2007 on 2008-09-05
GNOME isn't working because it appears to me that you DON'T yet have a working X server. There's absolutely no point messing around with GNOME until you get your X server working.

It appears that you haven't installed the graphics drivers for your system yet. Did you follow the beginners guide in the wiki exactly?

---

### Post by crimesaucer on 2008-09-05
> **maniheer said:**
> the gdm in rc.conf method will work, or, its

```

exec gnome-session

```

This is the correct way to start gnome in the .xinitrc


This is all covered in this tutorial on this page, 6th section down, right below the section for installing all of the gnome packages, editing your Daemons, and then editing your inittab to work with GDM, : [http://www.raiden.net/?cat=2&aid=276&pid=9](http://www.raiden.net/?cat=2&aid=276&pid=9)



(Like I said earlier, this is an older guide so some things are a bit different like the top section about the pacman.conf..... pacman uses a mirrors list now that is different than these steps.... it's still the same about uncommenting/commenting your preferred repository.... it also is different here: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7) on the 3rd section down, pacman uses 1 mirrors list now..... it's easier than having 5 different files to edit)  


As for nvidia, and nvidia-utils this is correct (plus compositing for compiz):

```
nvidia-xconfig --composite
```

[http://wiki.archlinux.org/index.php/NVIDIA](http://wiki.archlinux.org/index.php/NVIDIA)
[http://wiki.archlinux.org/index.php/Composite#NVIDIA_drivers](http://wiki.archlinux.org/index.php/Composite#NVIDIA_drivers)

---

### Post by Elephantman5 on 2008-09-05
> **sub2007 said:**
> GNOME isn't working because it appears to me that you DON'T yet have a working X server. There's absolutely no point messing around with GNOME until you get your X server working.

It appears that you haven't installed the graphics drivers for your system yet. Did you follow the beginners guide in the wiki exactly?

Yes I did. And I know I had a working X server because I tested it.
You know, the white box you move the X cursor around in?
Yes.

---

### Post by Elephantman5 on 2008-09-05
> **crimesaucer said:**
> This is the correct way to start gnome in the .xinitrc


This is all covered in this tutorial on this page, 6th section down, right below the section for installing all of the gnome packages, editing your Daemons, and then editing your inittab to work with GDM, : [http://www.raiden.net/?cat=2&aid=276&pid=9](http://www.raiden.net/?cat=2&aid=276&pid=9)



(Like I said earlier, this is an older guide so some things are a bit different like the top section about the pacman.conf..... pacman uses a mirrors list now that is different than these steps.... it's still the same about uncommenting/commenting your preferred repository.... it also is different here: [http://www.raiden.net/?cat=2&aid=276&pid=7](http://www.raiden.net/?cat=2&aid=276&pid=7) on the 3rd section down, pacman uses 1 mirrors list now..... it's easier than having 5 different files to edit)  


As for nvidia, and nvidia-utils this is correct (plus compositing for compiz):

```
nvidia-xconfig --composite
```[http://wiki.archlinux.org/index.php/NVIDIA](http://wiki.archlinux.org/index.php/NVIDIA)
[http://wiki.archlinux.org/index.php/Composite#NVIDIA_drivers](http://wiki.archlinux.org/index.php/Composite#NVIDIA_drivers)

Ok. Yeh, I'm not quite sure why I got that message, I'll return with more news. I really appreciate the links, I'm printing them right now.

---

### Post by Elephantman5 on 2008-09-06
(Edit)
Please stop posting on this, I'm sorry for bothering you people.
I'm an idiot.

---

