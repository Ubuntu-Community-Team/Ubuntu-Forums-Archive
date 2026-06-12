---
title: "USB TV Tuner"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2006-10-11
:confused: I installed Ubuntu yesterday and I would like to use my USB TV tuner, it is a "VideoMate U3 USB 2.0 DVB-T Stick" I have downloaded and installed a few different TV programs but it does not come up in the settings. Could someone please tell me how to get my TV Tuner to work.:confused: 

I think i might need to download drivers for it but there are none on the manufacurers web site.

If the TV tuner can not be used in linux at all then i will probably go back to using windows.

:confused: :confused: :confused: Please Help!!!:confused: :confused: :confused:

---

### Post by wehttamb on 2006-10-11
The manufacturer is Compro Tecnology and the website is [http://www.comprousa.com]("http://www.comprousa.com").

---

### Post by anaconda on 2006-10-11
post number #48 in here:
[http://www.dvdplaza.fi/forums/showthread.php?p=695379](http://www.dvdplaza.fi/forums/showthread.php?p=695379)
says that your USB-tuner is internally exactly the same than:
Pinnacle PCTV USB Stick (DVB-T) Which is supported !!

So you should be able to get it to work..

Here is a link that might be of interest:
[http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php](http://www.marcushellberg.com/pages/projects/digital-tv-in-linux.php)

---

### Post by easyease on 2006-10-11
easiest way is to install kaffeine, and also install the kaffeine-xine plug in via synaptic. thats what i use

---

### Post by wehttamb on 2006-10-11
> Here is a link that might be of interest:
[http://www.marcushellberg.com/pages/...v-in-linux.php](http://www.marcushellberg.com/pages/...v-in-linux.php)

I have only been using ubuntu for a few days. This site explains how to install the drivers but it makes no sense. :confused:  Could someone please explain how to install the drivers.

---

### Post by dixonstalbert on 2006-10-11
hi wehttamb

to install the driver given in weblink above,  you need to first get and install a lot of 'helper' programs so your computer can read the source code the program is written in and 'build' into a running 'module' that your linux kernel can access.

To do this, you need to open a terminal window (Accessories>Terminal) and type the following commands one by one and hit return (I have put comments behind each command so you will have an idea what they are doing- the terminal recognizes everything behind a # is a comment and ignores it)

```
sudo apt-get install build-essential gcc python-dev  make linux-kernel-headers linux-source   #this downloads some helper programs from ubuntu


wget http://www.selenic.com/mercurial/release/mercurial-0.9.1.tar.gz  #this downloads tar compressed hg program

tar xvzf mercurial-0.9.1.tar.gz  #this uncompresses hg install program to the /mercurial-0.9.1 dir

cd mercurial-0.9.1   #this changes to mercurial directory

 

python setup.py install  # this runs setup program using python program language

```

If everything is working if you now type 'hg' <return> in the terminal you should get a listing of all of 'hg' 's programs options- now you are ready to follow the instructions from marcus helberg, (ie the version for ubuntu dapper) which i have copied below:

(you should start out in your home directory; if your not sure how to get back there just close the terminal window and reopen it again )

```
mkdir driver
hg clone http://linuxtv.org/hg/~mrechberger/v4l-dvb
cd v4l-dvb/v4l_experimental/xc3028
./convert emBDA.sys > /lib/firmware/$(uname -r)/xceive_xc_3028.fw
cd ../../v4l
make
sudo make install
```

the 'make' command above 'makes' an executable version of the driver, the 'make install' command puts it in subdirectory of the kernel and sets up links to it.

marcus now recommends you reboot your computer before you take the final step

again open a terminal and type 

```
sudo modprobe em2880-dvb
``` 

this will insert the em2880-dvb driver into your ubuntu kernel

now open synaptic package manager and search on kaffeine   and install it

I dont use kaffeine but I understand it should now be able to find your device and you should get a picture 

hope this helps. let me know if you have any problems

---

### Post by wehttamb on 2006-10-11
:-k :-k :-k what do i do then to use the TV :-k :-k :-k

---

### Post by wehttamb on 2006-10-12
> If everything is working if you now type 'hg' <return> in the terminal you should get a listing of all of 'hg' 's programs options
when i typed "hg" and pressed <return> in the terminal i got this "bash: hg: command not found"
Something did not work.

---

### Post by wehttamb on 2006-10-12
I tried the python part again and noticed that there was an error, access was denied to do something.
Here is what happened
> wehttamb@Matthews-Computer:~$ cd mercurial-0.9.1
wehttamb@Matthews-Computer:~/mercurial-0.9.1$ python setup.py install
running install
running build
running build_py
running build_ext
running build_scripts
running install_lib
creating /usr/lib/python2.4/site-packages/mercurial
error: could not create '/usr/lib/python2.4/site-packages/mercurial': Permission denied
wehttamb@Matthews-Computer:~/mercurial-0.9.1$


Could you please tell me how to fix this.:confused:

---

### Post by dixonstalbert on 2006-10-12
oops:p 

I forgot there was a little note on the mercurial website that suggested installing hg 'as root user' in ubuntu dapper. 

I had copyied and pasted their install command without making that change...

instead of  

```
python setup.py install 
```

use
```
[COLOR="Red"]sudo [/COLOR]python setup.py install 
```

this will give you proper permissions to change things in /usr/bin directory

---

### Post by wehttamb on 2006-10-12
Hi

that worked but now i have another permission denied on another comand here is what i got.

> wehttamb@Matthews-Computer:~$ hg clone [http://linuxtv.org/hg/~mrechberger/v4l-dvb](http://linuxtv.org/hg/~mrechberger/v4l-dvb)
requesting all changes
adding changesets
adding manifests
adding file changes
added 3574 changesets with 10680 changes to 735 files
533 files updated, 0 files merged, 0 files removed, 0 files unresolved
wehttamb@Matthews-Computer:~$ cd v4l-dvb/v4l_experimental/xc3028
wehttamb@Matthews-Computer:~/v4l-dvb/v4l_experimental/xc3028$ ./convert emBDA.sys > /lib/firmware/$(uname -r)/xceive_xc_3028.fw
bash: /lib/firmware/2.6.15-27-386/xceive_xc_3028.fw: Permission denied
wehttamb@Matthews-Computer:~/v4l-dvb/v4l_experimental/xc3028$ 

How do i fix this permission denied???:confused:

---

### Post by dixonstalbert on 2006-10-13
> **wehttamb said:**
> Hi

that worked but now i have another permission denied on another comand here is what i got.



How do i fix this permission denied???:confused:

sounds like a similar problem: In linux, the main operating system programs are kept in directorys like /usr/...     that are 'owned' by 'root' ; i.e. only the root administrator is allowed to modify any of the files in those directory. The command that you are having a problem with is trying to modify something in a /usr/lib subdirectory and you do not have permission to do that.

The big difference between ubuntu linux and Windoze is that even though you maybe  the only user account set up in ubuntu, by default you do not have full permission to change important stuff, only 'root' does. Ubuntu has 2 ways for you to modify important stuff ( like things in the usr/lib/... directories):

1. (not recommended) type sudo su in the terminal.   This logs you in as the 'root administrator' and you have complete permissions to totally destroy your system, and if someone has hacked into your session they too will have complete permission to destroy important stuff

2. type sudo (space) then the command that you are having a problem with. this gives you temporary permission for that command only

Note: When you first install Ubuntu, it sets the 'root' account's password to the same thing as whatever password you set up for your account. Tha'ts why your password works, even thought you are using it to open the root account and not your own account


sorry for not putting the sudo's in my first post. I have a different USB tv tuner and I was able to get my latest driver without using hg-  trying to remember the hg process from about a year when I used it once:)

---

### Post by wehttamb on 2006-10-14
i tried using ```
sudo
``` and still got the permission denied so i tried using ```
sudo su
``` i did not get rhe permission denied but it gave me this error
```
root@Matthews-Computer:/home/wehttamb/v4l-dvb/v4l_experimental/xc3028/v4l-dvb/v4l_experimental/xc3028# ./convert emBDA.sys > /lib/firmware/$(uname -r)/xceive_xc_3028.fw
bash: ./convert: No such file or directory
root@Matthews-Computer:/home/wehttamb/v4l-dvb/v4l_experimental/xc3028/v4l-dvb/v4l_experimental/xc3028#

```

What is wrong now???:confused: :confused:

---

### Post by dixonstalbert on 2006-10-14
> **wehttamb said:**
> i tried using ```
sudo
``` and still got the permission denied so i tried using ```
sudo su
``` i did not get rhe permission denied but it gave me this error
```
root@Matthews-Computer:/home/wehttamb/v4l-dvb/v4l_experimental/xc3028/v4l-dvb/v4l_experimental/xc3028# ./convert emBDA.sys > /lib/firmware/$(uname -r)/xceive_xc_3028.fw
bash: ./convert: No such file or directory
root@Matthews-Computer:/home/wehttamb/v4l-dvb/v4l_experimental/xc3028/v4l-dvb/v4l_experimental/xc3028#

```

What is wrong now???:confused: :confused:

i notice you are in a different directory then last time. convert program is in :/home/wehttamb/v4l-dvb/v4l_experimental/xc3028 directory. to get there type cd .. to move up directory tree until get you are there or type cd /home/wehttamb/v4l-dvb/v4l_experimental/xc3028

---

### Post by wehttamb on 2006-11-12
:confused: That didnt seem to work :confused: 


i got in the right directory and this is what happened
```

wehttamb@wehttamb-desktop:~$ cd v4l-dvb/v4l_experimental/xc3028
wehttamb@wehttamb-desktop:~/v4l-dvb/v4l_experimental/xc3028$ sudo ./convert emBDA.sys > /lib/firmware/$(uname -r)/xceive_xc_3028.fw
bash: /lib/firmware/2.6.15-23-386/xceive_xc_3028.fw: Permission denied
wehttamb@wehttamb-desktop:~/v4l-dvb/v4l_experimental/xc3028$

```

:confused: why cant i do it even though it has sudo before it??? :confused:

---

### Post by wehttamb on 2006-11-12
Is there anyway i can use my tv tuner in linux or should i go back to Windows???

---

### Post by dixonstalbert on 2006-11-27
are you still working on this?

not sure why sudo isnt giving you the correct permissions-

for fun, try logging in as 'root' by typing:

```
sudo su
```

then navigate to the directory you used last time and try the command:

```
./convert emBDA.sys > /lib/firmware/$(uname -r)/xceive_xc_3028.fw
```

let me know how that works out. if you get an error, maybe post lines from system log ( click on System > Administration > System Log ) that  have to do with command

---

