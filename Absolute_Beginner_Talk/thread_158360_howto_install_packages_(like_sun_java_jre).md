---
title: "howto install packages (like sun java jre)"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by dooleydotdk on 2006-04-11
Hi 
I know this topic for sure is answered somewhere in forum, but I'm having a hard time finding it. As a newbie to the linux/unix world I need to get concepts right:

[B]My simple objective is to install Sun's java jre, for use in mainly the firefox browser.
[/B]
Back in windows I, in most cases, have a .exe file, when clicked will open a installation dialog. 

In linux I have several ways, this is the ones I've seen mentioned; 
1) a .bin which need further 'treatment' to be installed
2) a .rpm which I believe is a packed version of the bin
3) source to be compiled, which I not ready for at the moment     
4) synaptic, a package list and receiver
5) other ways

Could someone tell me a simple and intuitive way to handle tasks like this, not so much for my sake. But when I promote linux for friends and family, they refuse to   learn the terminal and issue a command. Myself has grown up with DOS and mainframes, so I actually love line commands. **What I need is to get the concept of packages/bin's, from they are downloaded to my desktop, until they work as a program/plugin in my browser.**  

I know that linux is very 'based' on line commands, and some tasks can't be done without. But I see the type of task mentioned as very basic.  

For example I find it hard, in synaptic, to find and choose suns java jre. If anybody could pinpoint this out it would be nice.

On the other hand I read Nanotubes howto:
```
cd Desktop
chmod +x jre-1_5_0_06-linux-i586.bin
sudo apt-get install fakeroot java-package java-common
sudo apt-get install build-essential
fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
sudo update-alternatives --config java
```
I this case I get errors on 'fakeroot'. 

Any suggestions welcome.
Tom

---

### Post by joshrobinson on 2006-04-11
i had problems with the 2 java files you installed.. the java-common and java-package

i installed those first and with them i got java 1.4.2 i think it was.. but i know it was a 1.4

i then grabbed the .bin file from the java website jre-1.5.0 i think it is

when i installed that bin file it was running java 1.4 for some applications.. such as azureus and limewire.. then on websites when i ran a java test i got 1.5

so i removed the java common and the java package

then i loged in as root, as the actual desktop not a sudo/su command, then i opened the bin file from terminal and installed it.. then my java was working perfect

so i would say remove the java common, and java package via apt-get or synaptic, then login as root and go into the terminal and run the jre 1.5 bin whever you want it to install

i had no luck either turning the bin file into a .deb package

but everything is working fine now

---

### Post by joshrobinson on 2006-04-11
heres alittle code help for you.. i just re-read your post

a .bin ususally has its own installer, such as the java.bin
if you do ./nameofbin.bin it should execute the small installer (as root with sudo or login by su)

an .rpm is a package such as a bin, but isnt used in ubuntu/debian (as far as ive seen so far debian/ubuntu is new to me)

a .deb is a is like an rpm that is special for debian/ubuntu
you can install .deb files in the gui not in the terminal by just double clicking the file and entering your root password

to remove files from apt-get with the terminal do sudo apt-get remove (package name) you can also use synaptic (in system-administration-synaptic) you may have to install it in add remove programs, right under the applications menu

you can also skip the sudo command if you type su then hit enter, then your root password, which will log you into root at the terminal (sudo just stands for super user do) but once you login with su you are in a super user account until you close terminal

now on to source files
i see you have the apt-get install build-essential in the code above, you need this to compile code

now unpackage the .tar file to say your desktop, and open a terminal and browse to that folder (type cd to change directory) remeber that case sensitvity (lower case and upper case) are very important in linux

now do su then your password
type ./configure to configure the source to your system
when its done then do: make
then make install when the make stops

if the ,/configure process stops it will tell you why it stoped, such as a missing dependency that you can track down with apt-get

if you want to do all 3 of those steps at once you can execute

./configure && make && make install

now

sudo apt-get remove java-common
sudp apt-get remove java-package

download java.bin from java website
make sure to put the .bin where you want it to install such as in / or /home/username
because it will install right where the .bin is
sudo ./bin name.bin

if the sudo doesnt work do:
su
enter password
./bin name.bin

hope i helped, and sorry if i said things you may already know

---

### Post by dooleydotdk on 2006-04-11
Thank you so much for the reply(s). It put something in place. I'll get back later when I've tried the good advices. And by the way, at my current level you cant say anything that is'nt new to me :-) 
Tom

---

### Post by joshrobinson on 2006-04-11
edit

---

### Post by joshrobinson on 2006-04-11
[QUOTE=dooleydotdk]Thank you so much for the reply(s). It put something in place. I'll get back later when I've tried the good advices. And by the way, at my current level you cant say anything that is'nt new to me :-) 
Tom[/QUOTE]

if you still have no luck with the .bin file
set your root password:

sudo passwd

click system, then administration, then login window: enter your password
click security tab then allow local system administrator login

click system, log out, switch user
username: put root
password: put the password you used on sudo passwd

open terminal, browse to where you placed the .bin file or download it again to the main filesystem /

now the following commands 

chmod +x jre-1_5_0_06-linux-i586.bin
./jre-1_5_0_06-linux-i586.bin

the end user agreement should show up.. hit the Q key
type yes for agree

it should do its thing then install.. log out root, switch back to your username, reopen firefox then go to the java website and test out the java install

remeber to go back into login window settings and uncheck the let system admin login for security reasons

just for alittle back information
chmod changes the access mode of a file, or in easier terms tells linux what kinda permissions to give a file

chmod +r = read permissions
chmod +w = write permissions
chmod +x = permission to execute a file/directory (in this case it gives the bin file permissions to execute and install)

---

### Post by jrib on 2006-04-11
Really, the easiest way is to add Seveas' java section in his repository [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages) and then install sun-j2re1.5 using synaptic.

---

### Post by dooleydotdk on 2006-04-11
[QUOTE=_jason]...add Seveas' java section in his repository ...and then install ...using synaptic.[/QUOTE]

Where and what are my repository? and how do I add Serveas? 
The link above talks about 'Falcon'.

---

### Post by joshrobinson on 2006-04-11
[QUOTE=dooleydotdk]Where and what are my repository? and how do I add Serveas? 
The link above talks about 'Falcon'.[/QUOTE]

repository is just a collection of packages that apt-get and synaptic access's to get files

you can either open synaptic, then go to settings repositories, add, then click custom
on the link posted above the repositories are under the mirrors section

deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) breezy-seveas list_of_sections
deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) breezy-seveas list_of_sections

you want to add those to your repositories

or what i do and find easier
in terminal:
sudo gedit /etc/apt/sources.list

then add the links above starting with deb and deb-src.. just paste them at the bottom of the file that opens up, save and exit the file editor

next do: sudo apt-get update to update the packages on the new repositories you did, or in synaptic hit the reload button

then follow the directions someone posted above on how to install it after the repositories are done, do a search for sun java and install

p.s. ive never done it this way(to install java), but thats how you add repositories

---

### Post by dooleydotdk on 2006-04-12
Thank so much for taking time to tell about both the repository/synaptic way and the 'terminal' way. It's nice and enlightning to hear both methods.

---

### Post by joshrobinson on 2006-04-12
[QUOTE=dooleydotdk]Thank so much for taking time to tell about both the repository/synaptic way and the 'terminal' way. It's nice and enlightning to hear both methods.[/QUOTE]

no problem :cool:

i grew up with command line type stuff.. so i like it better that way

---

### Post by dooleydotdk on 2006-04-22
[QUOTE=joshrobinson]if you still have no luck with the .bin file
set your root password:

sudo passwd

click system, then administration, then login window: enter your password
click security tab then allow local system administrator login

click system, log out, switch user
username: put root
password: put the password you used on sudo passwd

open terminal, browse to where you placed the .bin file or download it again to the main filesystem /

now the following commands 

chmod +x jre-1_5_0_06-linux-i586.bin
./jre-1_5_0_06-linux-i586.bin

the end user agreement should show up.. hit the Q key
type yes for agree

it should do its thing then install.. log out root, switch back to your username, reopen firefox then go to the java website and test out the java install
[/QUOTE]

Done! Everything worked as described. But still no java plugin in my firefox browser. Any ideas?
Tom

---

