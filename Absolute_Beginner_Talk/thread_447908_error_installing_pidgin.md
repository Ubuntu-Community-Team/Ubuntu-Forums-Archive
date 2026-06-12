---
title: "error installing pidgin"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by djeepgu on 2007-05-18
root@andrei-laptop:/home/andrei/pidgin-2.0.0# ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

why do i get this error?

10x

---

### Post by carlosqueso on 2007-05-18
To build from source, you need the build-essential package.  Type ```
sudo apt-get install build-essential
``` at a command prompt to get it.

---

### Post by djeepgu on 2007-05-18
now i get this error:
root@andrei-laptop:/home/andrei/pidgin-2.0.0# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
root@andrei-laptop:/home/andrei/pidgin-2.0.0#


i have tried also from :
andrei@andrei-laptop:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
andrei@andrei-laptop:~$

---

### Post by carlosqueso on 2007-05-18
Are you conneted to the internet? If so run ```
sudo apt-get update
``` and try again. otherwise...we're gonna have a lot of fun:roll: getting you all the stuff we need.

---

### Post by theicyj on 2007-05-18
You could try the .deb file here:
[http://www.getdeb.net/release.php?id=817]("http://www.getdeb.net/release.php?id=817")

---

### Post by gmjs on 2007-05-18
The error is due to a missing C compiler that will create executables.   Try installing the g++ package.

# aptitude install g++


I found that I also had to install the following packages to compile Pidgin from source.  It worked once, but for some reason it will not make correctly for me anymore!  It works in Edgy though with no problems.

# aptitude install libgtk2.0-dev

# aptitude install libglib2.0-dev

# aptitude install libxml2-dev

# aptitude install libgnutls-dev

libgnutls is required for SSL support which is required if using the MSN or Google Talk protocols.

Hope this helps,

Graham

---

### Post by djeepgu on 2007-05-19
:confused: i have nothing installed on. i just installed ubuntu for the first time :) 
take me step by step because i have never used linux 
thanks a lot

---

### Post by gmjs on 2007-05-19
Sorry!

This should work after a clean install of Ubuntu.

First, you need to open a Terminal Window (Applications > Accessories > Terminal).

The Terminal opens by default with your current user credentials.  To compile software, you need to be running as the Root (aka Super) user.  Type the following after the **$** prompt to run the terminal as the Root user:

$ **sudo -i**

and then enter your current password.

Now you need to install the following packages before compiling Pidgin 2.0.0.  Installing them all together means that the ./configure command will not stop half way through.  Type the following, stating **Y** to install the selected packages and then waiting for each command to finish before moving on to the next.  Note that you will need the Ubuntu CD for the very first command, as the packages it requires are already available on it.  You will need a working connection to the Internet for the remainder:

$ **aptitude install g++**

$ **aptitude install libgtk2.0-dev**

$ **aptitude install libglib2.0-dev**

$ **aptitude install libxml2-dev**

$ **aptitude install libgnutls-dev**

Now you should be able to compile Pidgin with the following commands.  Make sure you are in your **/home/andrei/pidgin-2.0.0** folder first:

$ **cd ~/pidgin-2.0.0**

(Note: The tilde character **~** denotes your home folder)

$ **./configure**

Configure will then state "enter 'make'".

$ **make**

Make will take a few seconds to complete.  When it has finished type:

$ **make install**

That should be it.  Type:

$ **logout**

to leave the Root session and then type:

$ **pidgin**

to run Pidgin.

Of course, after not too long, I'm sure Pidgin will replace Gaim in the **Applications>Add/Remove...** programs list.  You will then just be able to select it and Ubuntu will handle the rest.  I'd also hope that the next version of Ubuntu will ship with Pidgin pre-installed as it has done with Gaim in this version.  So, if the worst comes to the worst...!

Hope this works for you.  I'm also fairly new to Linux, so if there are still problems, I'm stuck now too!

Graham

---------------------
Update: Installing Pidgin 2.0.1

I've just compiled the newest version of Pidgin (2.0.1) and you also need to install gettext using the following command:

$ **aptitude install gettext**

Ubuntu will ask for the installation CD, as this package is available on your Ubuntu disk.

Now continue to **make** and **make install**.

Also, the bug I had after installing the Ubuntu updates when compiling Pidgin 2.0.0 has gone in version 2.0.1.  Good work Pidgin!

---

### Post by krisfrajer on 2007-05-19
do you have any preferences for pidgim? Because ubuntu comes with gaim (applications >> internet >> gaim) and it does pretty much the same as pidgin. It happens pidgin is the newest version of gaim. Anyways if you do not have gaim, you can install it through add/remove software. Another service to try is aMSN if you are interested in having msn under linux. That is what I use anyway.

---

