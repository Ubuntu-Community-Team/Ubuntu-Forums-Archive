---
title: "Is this really hard and am I just really thick!"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by scottsaunders on 2008-03-11
Hi,

I have just installed Ubuntu for the 1st time after being a dedicated Windows user,

I have just installed the software successful which was great however there are some driver issues with the wireless parts of the laptop (not unexpected)

I have just been looking at the program ndiswrapper but if I really dont know where to start as the commands in the instructions are making no sence to me at all.

I have got the file what looks like a ZIP file anyway,  its been expanded onto the desktop and there is now a directory on my desktop called Ndiswrapper 1.52, what do I need to do now? I was thinking that I maybe need to use terminal but I dont know the commands or indeed how to change directory ? obviously in DOS its with the CD command but that does not work in Ubuntu.

I have got the windows xp driver for the wireless lan USB that is in my laptop so I know I need to do something with that but I am not sure what..

sorry to sound like a total spanner..

Thanks

---

### Post by Arthur Archnix on 2008-03-11
Post a link with the instructions you're following. Also, post the output of this command, but be sure to wrap it in code marks (highlight the text, then click the # sign). The command to run is:
```
lspci
```
Then, let us know how far along you got with the instructions before you ran into problems.

---

### Post by scottsaunders on 2008-03-11
> **Arthur Archnix said:**
> Post a link with the instructions you're following. Also, post the output of this command, but be sure to wrap it in code marks (highlight the text, then click the # sign). The command to run is:
```
lspci
```
Then, let us know how far along you got with the instructions before you ran into problems.

Thanks for the message,

Right,

"Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install"

this is what I am trying to do...

when I go to terminal and type sudo su I can enter the password to enter superuser mode but when I try and cd desktop I get this...

"root@scottsaunders-laptop:/home/scottsaunders# cd desktop
bash: cd: desktop: No such file or directory
root@scottsaunders-laptop:/home/scottsaunders# "

what do you think?

Thanks

---

### Post by Nevon on 2008-03-11
You need to spell Desktop with a capital D. It's case-sensitive.

---

### Post by scottsaunders on 2008-03-11
no way!!!!

how much of a prat am I ...

thanks

:)

---

### Post by dstew on 2008-03-11
Here is where a new open-source software user can get confused. With open-source software, you can get a program in two forms. One is the "source code", which is the original text file (or files, usually) that is what the programmer wrote. You rarely see source code for Windows programs, since that is kept secret for business reasons. The source code has to be converted to the machine-code that the computer understands. The program that does the conversion is called a compiler. So, with open-source software, this is called "compiling from source". It is not that hard to do, but for a new user you should try to avoid it. You have actually downloaded the ndiswrapper source code. If you want to compile from source, that is what you need. However, it is better to install Ubuntu software the other way, using pre-compiled binary files.

The pre-compiled binary files are stuffed in "packages" that are then installed on your system using the Debian package management software. You get these packages from archives, also called repositories, that are maintained by the Ubuntu development team. The best way to get and install Ubuntu Debian packages is to use the Synaptic package manager program, in the System --> Administration menu. You will find the ndiswrapper packages there. Use the Search menu button. The package you need is called ndiswrapper-common. You check the box as "Mark for Installation". The package manager will then automatically select other packages that are needed by the first, and will install these also. These are called "dependencies". Finally, click the Apply menu button and the programs will be installed automatically.

After ndiswrapper is installed, you will need to configure it. That is a whole 'nuther issue.

---

### Post by bodhi.zazen on 2008-03-11
LOL 

Welcome to the Ubuntu forums scottsaunders 

Yes, a new OS is challenging at first. We are here to help, so feel free to ask questions and as you can see I am sure you will find assistance.

This link can help : [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by scottsaunders on 2008-03-11
> **bodhi.zazen said:**
> LOL 

Welcome to the Ubuntu forums scottsaunders 

Yes, a new OS is challenging at first. We are here to help, so feel free to ask questions and as you can see I am sure you will find assistance.

This link can help : [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)


I am struggling here,

nothing is working for me...

basically I am trying to install a driver for my wireless usb which is a Sis163U Wlan.  I have tried following the instructions included in the Ndiswrapper download and nothing seems to work as well as it does not seem clear enough (sudo mode or not?)

I have followed what I can until i got the prompted where I need to type ndiswrapper -i driver.inf only to be told the following message...

root@scottsaunders-laptop:~/Desktop# ndiswrapper -i sis163u.inf
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
root@scottsaunders-laptop:~/Desktop# 

I cant understand what is going on and its getting to me now.

what do you think?

Thanks

P.S I followed the post before where the person told me to install Ndisrapper through the options under system, administration etc but that does nothing..

---

### Post by scottsaunders on 2008-03-11
I have uploaded the sys and inf files, if there is anyone who can turn these into a driver for ubuntu pls?

[http://clickapic.com/file/829/sis163u-inf.html](http://clickapic.com/file/829/sis163u-inf.html)  
[http://clickapic.com/file/828/SiS163u-sys.html](http://clickapic.com/file/828/SiS163u-sys.html)

thanks

---

### Post by Arkenzor on 2008-03-11
Do you have a way of getting - even temporarily - a working internet connection for your Ubuntu, or are you stuck with wireless?

---

### Post by scottsaunders on 2008-03-11
i am hooked up via lan at the moment but it means i am sat in my hallway as the ethernet is not long enough

---

### Post by Arkenzor on 2008-03-11
Then you should indeed be able to use that System -> Administration -> Synaptic to install ndiswrapper:

- Start it. It will ask for your password.

- In the menubar, find a menu with a "Software Sources" option (don't really remeber where it is). Select it.

- You'll get a new window. In one of the tabs, there'll be an option saying to use the Ubuntu installation CD as a software source. Uncheck it, close the window.

- Synaptic will then tell you to click the Reload button in the toolbar, which you should do.

- You can now use the Search function to find ndiswrapper, and install it by right-clicking the box next to it, then selecting Apply in the main toolbar.


This should take care of your current problem.



P.S.: By the way, it really is pretty hard. Wireless is the last big potential Linux Hardware Pain In The *** (even though lots of adapters work just fine. Guess you were unlucky).

---

### Post by dstew on 2008-03-11
scottsaunders: You are going to the configuration step when you do not even have ndiswrapper installed yet. See my post above. After you get ndiswrapper installed, then work on configuration.

You can install ndiswrapper using Synaptic, or use the apt-get command as the error message said.

EDIT: Ah, sorry, I see you did not even have wired internet. Synaptic needs the internet to be fully active.

---

### Post by scottsaunders on 2008-03-11
right,

I have checked on the synaptic software and both Ndiswrapper and the utilities are installed fine - I have put a screen dump below :

[http://img187.imageshack.us/img187/4195/screenshot1qb4.png](http://img187.imageshack.us/img187/4195/screenshot1qb4.png)

yet the terminal is saying its not installed..

[http://img504.imageshack.us/img504/7537/screenshot2bu8.png](http://img504.imageshack.us/img504/7537/screenshot2bu8.png)

is there something wrong/

---

### Post by Arkenzor on 2008-03-11
That's a nice mess...

Try reinstalling it (using Synaptic again) and see if it works.


If it still doesn't work, then maybe there's something wrong with the path where the shell looks for the commands you type. Try providing its complete location:
```
/usr/sbin/ndiswrapper -i sis163u.inf
```
instead of simply using the command's name.

---

### Post by dstew on 2008-03-11
Maybe your sudo timed out. Try sudo ndiswrapper. But, it should at least give you a usage list, even without sudo, so I don't know...

---

### Post by inksmithy on 2008-03-11
Scott, check this link out:

[http://ubuntuforums.org/showthread.php?t=606167&highlight=sis163u+gutsy](http://ubuntuforums.org/showthread.php?t=606167&highlight=sis163u+gutsy)

From what I can see, someone has gone through exactly what you have, with the same card.

Good luck,

Alan

---

