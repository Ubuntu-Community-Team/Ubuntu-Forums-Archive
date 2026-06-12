---
title: "emusic tar file"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-13
Hi

I feel i should know this by now, but i'm having trouble installing music downloader/management file 'Emusic' 

emusicdlm-2.0.1.9.tar.gz

I've untarred it:

emusicdlm-2.0.1

and it is sitting on Desktop (both are) and now i'm stuck as i don't know where to go from here.
I feel i should have downloaded it elsewhere. I have my download set or default to Desktop, hence everything lands here. But i wouldn't have known what the right place to download it to would be anyways!

If someone can tell me both how to know where to download things to and how to do that, and now, given the situation also how to install Emusic once untarred
sudo apt-get install emusicdlm-2.0.1 ???

thank you,

--
sophtpaw

---

### Post by Ampersand on 2005-08-13
Hi
Emusic doesn't seem to be in the apt repositories, so apt-get won't work.

You can download files to anywhere in your home directory. You should be able to set the directory in the settings of whichever browser you use.

Make sure you've got the build-essential package from apt. To install emusic, you'll probably need to open a terminal, cd into ~/Desktop/emusicdlm-2.0.1/ and run './configure' followed by 'make' and finally 'sudo make install'. There should be a readme file in the directory.

---

### Post by sophtpaw on 2005-08-13
[QUOTE=Ampersand]Hi
Emusic doesn't seem to be in the apt repositories, so apt-get won't work.

You can download files to anywhere in your home directory. You should be able to set the directory in the settings of whichever browser you use.

Make sure you've got the build-essential package from apt. To install emusic, you'll probably need to open a terminal, cd into ~/Desktop/emusicdlm-2.0.1/ and run './configure' followed by 'make' and finally 'sudo make install'. There should be a readme file in the directory.[/QUOTE]

when i ./ :

conrad@x1-6-00-0b-6a-16-78-f0kernel:~/Desktop/emusicdlm-2.0.1$ ./configure
bash: ./configure: No such file or directory

what have i missed or not done to get No such file or directory?

equally, 'make' :

conrad@x1-6-00-0b-6a-16-78-f0kernel:~/Desktop/emusicdlm-2.0.1$ make
make: *** No targets specified and no makefile found.  Stop.


finally, for install: 

conrad@x1-6-00-0b-6a-16-78-f0kernel:~/Desktop/emusicdlm-2.0.1$ sudo make install
Password:

cat install.sh >install
chmod a+x install

what does that mean? 

thank you,

--
sophtpaw

---

### Post by Ampersand on 2005-08-13
Is there any form of documentation in the tar.gz you downloaded? After a brief look through their message boards, it seems that the Linux client is no longer supported by them. 

If you do an 'ls' in the directory, what do you get?

---

### Post by sophtpaw on 2005-08-13
[QUOTE=Ampersand]Is there any form of documentation in the tar.gz you downloaded? After a brief look through their message boards, it seems that the Linux client is no longer supported by them. 

If you do an 'ls' in the directory, what do you get?[/QUOTE]

Do you mean this:

conrad@x1-6-00-0b-6a-16-78-f0kernel:~/Desktop/emusicdlm-2.0.1$ dir
emusicdlm          emusicdlm.desktop.gnome  install     README
emusicdlm-bin      emusicdlm.png            install.sh  uninstall.sh
emusicdlm.desktop  help                     lib

I don't know how to open README or any of the files stated. As far as supporting Linux, i think Emusic do, because i only just got an email from them inviting me back, and for downloading their music manager (Emusic) it included linux both in gz and rpm. And we cannot use rpm's am i right, so i clicked on gz, but maybe you know something i don't know, i.e. message boards,

--
sophtpaw

---

### Post by Ampersand on 2005-08-13
you should be able to open "README" with gedit or any other text editor, but it looks like you should run 'sudo ./install.sh'.

You could also download the rpm, then use alien to change it to a deb. If the rpm is called "emusicdlm-2.0.1.rpm" for example, run in a terminal:

'alien emusicdlm-2.0.1.rpm'

This will create a deb called emusicdlm-2.0.1.deb . You can then run

'sudo dpkg -i emusicdlm-2.0.1.deb' to install it.

Richard

---

### Post by polo_step on 2005-08-13
[QUOTE=Ampersand]
You could also download the rpm, then use alien to change it to a deb. If the rpm is called "emusicdlm-2.0.1.rpm" for example, run in a terminal:

'alien emusicdlm-2.0.1.rpm'

This will create a deb called emusicdlm-2.0.1.deb . You can then run

'sudo dpkg -i emusicdlm-2.0.1.deb' to install it.[/QUOTE]
That's interesting to know, as I've wondered how to do this.

Is this generally a safe way to install something not in the Ubuntu repositories? I've been warned against trying to install stuff from tarballs.

---

### Post by Ampersand on 2005-08-13
They're generally safe as long as they come from a trustworthy site. Installing random packages has the same risks as installing random programs on windows (except with these you can look through the source and see exactly what you're installing if you have more programming knowledge than me). 

It's usually best to install programs from the ubuntu repositories to make it easier to work out dependancies, and also so that you can easily uninstall them more easily.

---

### Post by sophtpaw on 2005-08-14
[QUOTE=Ampersand]you should be able to open "README" with gedit or any other text editor, but it looks like you should run 'sudo ./install.sh'.

You could also download the rpm, then use alien to change it to a deb. If the rpm is called "emusicdlm-2.0.1.rpm" for example, run in a terminal:

'alien emusicdlm-2.0.1.rpm'

This will create a deb called emusicdlm-2.0.1.deb . You can then run

'sudo dpkg -i emusicdlm-2.0.1.deb' to install it.

Richard[/QUOTE]

Thank you Ampersand,

sudo ./install.sh infact did it, as i already had the gz untarred sitting there i opted for that.
However, i hadn't heard of alien and of being able to converts rpm's into .deb files. That sounds like it could be real handi, and i would have tried that had the sudo ./install.sh not worked for me. Now i have freedom of another option with alien, and i look forward to the opportunity of using it

--
sophtpaw

---

### Post by bloodyserb on 2006-04-09
Hi,

I'm having a similar problem, and followed along to the end.  When I did the install I got:

sam@ubuntu:~/emusicdlm-2.0.1$ sudo ./install.sh
Installing application.
install: cannot run strip: No such file or directory
install: strip failed
KDE is installed. Installing icon and menu item.
Gnome is installed. Installing icon and menu item.
install: cannot create regular file `/usr/share/gnome/apps/Internet/emusicdlm.desktop': No such file or directory

EMusic Download Manager sucessfully installed.

IMPORTANT: Please read the installation instructions on the EMusic
           web page for details on how to setup the download manager
           so your web browser launches the manager when you download
           and album from EMusic.

I know it says it installed sucessfully, but the rest of it didn't look very encouraging, and I don't see an icon anywhere.  Any help would be much appreciated.

Thanks,

Sam

---

### Post by ddonky on 2006-05-23
The eMusic downloader for *nix isn't supported by them anymore, but there is one that was written by a fan, it uses java. Try it here:

[http://www.kallisti.net.nz/EMusicJ/HomePage/](http://www.kallisti.net.nz/EMusicJ/HomePage/)

---

