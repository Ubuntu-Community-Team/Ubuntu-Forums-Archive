---
title: "Really basic help needed!"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by homersimpson on 2005-11-07
Hello

Total Linux novice, Ubuntu installed on a clean hard disc with no partitions/dual boot/previous versions etc.

I picked Ubuntu as I hoped it was going to be easy to use but I'm in trouble already.
All I want to do is install what I think is called a compiled binary on to Ubuntu so that I can have a look at it to see if it suits my requirements, but I can't seem to get anywhere with it.
I've managed to copy the folder from a CD into 'home' but that was not without a certain degree of frustration; now what I need to do is open an executable called 'Install'. Simple as that or so it seems, how does this thing work? I've tried virtually everything. I know I'm a complete novice to Linux butI didn't really envisage reading any more than 2-3 pages of help to do something as basic as this; is anyone generous enough to help?

Thanks if you are!

---

### Post by raublekick on 2005-11-07
I'm not sure how to do it the way you're asking, but try searching for it in Synaptic. 

Go to System -> Administration -> Synaptic Package Manager

You can use the search feature in there, there's tons of apps to try.

---

### Post by RawMustard on 2005-11-07
what is the binary program you ant to install?

---

### Post by ubuntu_demon on 2005-11-07
(I moved this thread to absolute beginner talk because you are a green user.)

What program do you want to install ? 

Isn't it available from the repositories ? What is the extension of the file ?

---

### Post by homersimpson on 2005-11-07
Sorry, didn't see the absolute beginner section.

I'm just trying to take a peek at the Darwin Streaming Server with a long term view of putting a bit richer content on a hobby website that I run. The download site suggests Red Hat 8 but says that other Linux should be okay.

There isn't a file extension on it in Ubuntu or in Windows, I have managed to get it open as a text file in the text editor which at some point said it was an 'excecutable text file'.
 
I can't get Synaptic to find it at all using either the 'search' or add 'new repository'.

It's not in a repository (as far as I know).

My attempts at command lines have been feeble and just say file not found.

I tried to get Synaptic to read it off the CD but it says 'not apt'.

Have I missed something here, can I only use certain programs with Ubuntu?

Thanks for the replies.

---

### Post by shof2k on 2005-11-07
Darwin streaming server is sourced from apple so it's unlikely to be in synaptic.  

Looking at your previous post, you mention a file called install.  Is there also a file with a .deb or .rpm suffix in your directory?  

If not then you should open a terminal, go to your directory and either type "./install" or "sudo ./install" to begin installation.  This will probably be trial and error as you may need additional libraries.

Let us know how you get on....and keep up the linux faith :)

---

### Post by ubuntu_demon on 2005-11-07
And if it's only 1 file then do this (without the $) in an terminal :

$sudo chmod +x ***filename***
$./***filename***

if it wants to install somewhere else then your homedir and you are okay with that and you trust it do :

$sudo ./***filename***

---

### Post by homersimpson on 2005-11-07
Thanks

It's just a 'see if it works' attempt, so I won't be spending ages on it.

One last try before I write it off for now.

I've got the directory 'home' whiich contains directory 'username' which contains 2 directories 'Desktop' and the copied in 'DarwinStreamingSrvr5.5-Linux'

The 'DarwinStreamingSrvr5.5-Linux' contains the file 'Install' and others none of which have extensions other than some .pl and some .xml

The readme text file in it matches your advice in suggesting type ' ./Install '

I open a Terminal which has in the title bar:

username@computername/home/username

and shows the command line:

username@computername:~$

I enter:

cd DarwinStreamingSrvr5.5-Linux

which returns:

username@computername:~/DarwinStreamingSrvr5.5-Linux $

and I enter ./Install which returns:

:bad interpreter: no such file or directory

so I try sudo./Install which returns:

Password?

so I enter this username's password and it returns:

unable to exec ./Install no such file or directory

(I am presuming I am correct in assuming 'Install' is capital 'I' to match the file name?)

---

### Post by Maverick911 on 2005-11-07
Quote :"The 'DarwinStreamingSrvr5.5-Linux' contains the file 'Install' and others none of which have extensions other than some .pl and some .xml"

I'm very new to Linux also, so if this is bad advice please tell me someone.

Try sudo make Install 
(remember commands and filenames are case sensitive)

---

### Post by patrick295767 on 2005-11-07
I am also new with linux (few months now)...
U can get nfo maybe from my progression threat of linux ... 
I reported even the simpliest simpliest simpliest things (newbie) I learned with this forum !
              [http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
I hope this will help you.
  
Good courage !
  
Pat'

---

### Post by LHZ on 2005-11-07
This may have been said before, but it's really important: everything in Linux is case sensitive. "install" and "Install" are different files to Linux, so make sure you got the cases right.

---

### Post by tonysathre on 2005-11-07
is there a configure script, if so, run ./configure from the directory containing the script, then run make, then sudo make install, then make clean

---

### Post by Jussi Kukkonen on 2005-11-07
Homer, 
 The last few pieces of advice are probably incorrect (people assume you have a source package, when quite probably you actually do have a binary release).

In any case, please copy-paste the names of files in the  ~/DarwinStreamingSrvr5.5-Linux directory and the contents of any README or INSTALL files. Someone will be able to help you after that.

To get a file listing in a terminal:
```
ls
```
To output file README:
```
cat README
```

---

### Post by oskude on 2005-11-07
hi,

i was kinda bored so i tried that DarwinStreamingSrvr5.5-Linux from here [http://developer.apple.com/darwin/projects/streaming/](http://developer.apple.com/darwin/projects/streaming/) on my testlab ubuntu partition and heres how i did it:

unpacked the DarwinStreamingSrvr5.5-Linux.tar.gz to my home directory
```
hacker@testlab:~$ tar -xvzf DarwinStreamingSrvr5.5-Linux.tar.gz
```
after running "sudo ./Install" in the depacked directory i saw many "libstdc++5 not found..." so i made
```
hacker@testlab:~/DarwinStreamingSrvr5.5-Linux$ sudo apt-get install libstdc++5
```
run again
```
hacker@testlab:~/DarwinStreamingSrvr5.5-Linux$ sudo ./Install
```
after that the installation seemed to work and i could open the web interface through "localhost:1220" in firefox

if the server is not started (like after reboot) you can start it with
```
sudo streamingadminserver.pl
```

i dont have any content to test with, but atleast it seems to run :)

cheers
osku[de]

edit: IMPORTANT, 
i allmost forgot. the DSS was complaining something about "qtss" group, and after googling i looked the /etc/passwd file
```
cat /etc/passwd
...[cut]...
gdm:x:106:113:Gnome Display Manager:/var/lib/gdm:/bin/false
hplip:x:107:7:HPLIP system user,,,:/var/run/hplip:/bin/false
qtss:x:1001:100::/home/qtss:
```
ok, user exists. lets see if a group exists
```
cat /etc/group
...[cut]...
hal:x:111:
saned:x:112:
gdm:x:113:

```
nope, group "qtss" doesnt exists... hmm, lets make one. i took the user id of "qtss" in /etc/passwd (1001) and added it in groups
```
sudo nano /etc/group
...[cut]...
hal:x:111:
saned:x:112:
gdm:x:113:
qtss:x:1001:

```
now restart the server and it should works...

---

