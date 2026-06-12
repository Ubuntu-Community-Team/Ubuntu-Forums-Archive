---
title: "Is it possible to set up a shared file between Window$ and Ubuntu?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-14
the title kind of explains it.

my dad has not yet seen the amazingness of ubuntu and is still using window$.

can i set up a shared folder with him anyway?

if so... how?

---

### Post by NeoGreen on 2007-06-14
Yeah you can use samba, this will enable you to share files with windows.

---

### Post by antharr on 2007-06-14
Yes. Search the forum for installing Samba.

---

### Post by gdoermann on 2007-06-14
Are you networking between two computers (one running Windows and the other Ubuntu) or are you trying to write to NTFS partitions on the same machine?

---

### Post by Tyke91 on 2007-06-14
any tutorials... i saw the samba website and got lost :(


EDIT: WOW... in the time it took me to post, 2 more posted


EDIT again: yes, it is two computers. connected by a physical line to a router (i think linksys)

---

### Post by Omnios on 2007-06-14
It is possible and I have done it before.

 This might help.

 [https://help.ubuntu.com/7.04/internet/C/networking.html](https://help.ubuntu.com/7.04/internet/C/networking.html)

---

### Post by dreadlord_chris on 2007-06-14
> **Tyke91 said:**
> the title kind of explains it.

my dad has not yet seen the amazingness of ubuntu and is still using window$.

can i set up a shared folder with him anyway?

if so... how?

Yup, you sure can. How you do it will depend on your setup. Mainly it will depend on whether you and your dad share a computer, or each have your own.

---

### Post by Tyke91 on 2007-06-14
>  EDIT again: yes, it is two computers. connected by a physical line to a router (i think linksys)

;)

ill check it out and post any other questions here :D

---

### Post by gdoermann on 2007-06-14
this is a wiki that walks you through the installation and helps you set it up.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

### Post by BLTicklemonster on 2007-06-14
Show of hands; how many of you who posted, actually have it set up right now and use it?


If any, then please, can you do a walk through on how you accomplished this amazing feat?

If not, is there anyone on the planet who actually does know, not just people who know where the links are that make people think it can be easily done?

---

### Post by rscott5 on 2007-06-14
> **BLTicklemonster said:**
> Show of hands; how many of you who posted, actually have it set up right now and use it?


If any, then please, can you do a walk through on how you accomplished this amazing feat?

If not, is there anyone on the planet who actually does know, not just people who know where the links are that make people think it can be easily done?

I didn't post before but ya I have Samba running on two Ubuntu Feisty machines and it is working flawlessly on both. I followed the instructions here: [HTML]http://ubuntuforums.org/showthread.php?t=202605&highlight=samba[/HTML] and they worked perfect, not one problem. Best of luck.

---

### Post by gdoermann on 2007-06-15
Ok, first I'm pretty new at this, but I have a pretty basic setup for just sharing folders between a laptop (Windows) and a desktop (Ubuntu).  First, I followed the directions on the link I sent, but I will repeat the necessary ones here. (See [link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service") for setting up users, folders and settings in the terminal).

**First install samba:**

```
sudo apt-get install samba smbfs
```

Now you need to add some users:
Make the new file-
```
sudo smbpasswd -a system_username
gksudo gedit /etc/samba/smbusers
```

Insert the following line into the new file:
```
system_username = "network username"
```
Where you replace "system_username" with your username and "network username" with the username you want to sign in with.

Save the file.

To edit network user:
```
sudo smbpasswd -a system_username
```

To delete network user:
```
sudo smbpasswd -x system_username
```


**Now for Samba Web Administration Tool (SWAT):**

```
sudo apt-get install netkit-inetd
sudo apt-get install swat
```

Open inetd daemon configuration:
```
sudo gksu gedit /etc/inetd.conf
```

If string is:
```
<#off#> swat            stream  tcp     nowait.400      root    /usr/sbin/tcpd  /usr/sbin/swat
```

Change to (due to know BUG which resets peer connection):
```
swat            stream  tcp     nowait.400      root    /usr/sbin/swat  swat
```

Restart daemon:
```
sudo /etc/init.d/inetd restart
```

**Install SSH Server for remote administration service**

```
sudo apt-get install ssh
```

Now to SSH into a remote Ubuntu machine  from Ubuntu(a side note on this post):
```
ssh username@192.168.0.1
```
Obviously, change the IP address to the computer you are hooking up to.  


 How to SSH into remote Ubuntu machine via Windows machine:
Download PuTTY: [Here]("http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe")

 How to copy files/folders from/into remote Ubuntu machine via Windows machine:
Download FileZilla: [Here]("http://prdownloads.sourceforge.net/filezilla/FileZilla_2_2_18_setup.exe?download")

Ok, so now you have everything installed. 

Go to System->Administration-> Network
Under the General Tab setup your Host Name and Domain.

Go to System-> Administration -> Shared Folders
Under General Properties tab enter your Workgroup/Domain (same as windows computer)
Set computer as WINS server.
Then go to the tab Shared Folders.
Add folders you want to share and choose Share Through: Windows Network (SMB).

I would restart your computer.  I think that is all there is to it (at least that's all I remember doing)   and mine works for what I need.

---

### Post by gdoermann on 2007-06-15
Follow RScott's link... it's more complete.

---

### Post by Tyke91 on 2007-06-15
grr... If i could program, i would create some sort of graphical thing where it would ask you your username, password, and I.P. adress of connecting computer... if only i could program ;)


*note to self, get 1337 programming skillz*

---

### Post by BLTicklemonster on 2007-06-15
So it can be done after all. Excellent. Now if someone who actually has it and uses it posted how to do it so that there were no usernames or passwords, I'd attempt it. But I detest our IT department, and their "you need to generate a new password monthly, and no, you can't get admin priveleges to install printer drivers to print out the tickets you need to print out daily, you'll have to wait a few days until we get around to you" bullsh*t, so no, I'm not about to put a shared folder on my network at my house that has to use a username and password. (I've about got our bosses talked in to telling IT to defrag itself, and we'll set up our own stuff and to heck with them. Several other departments are ready to do the same thing.)

I find it incredible that there's not a GUI solution to this in the first place.

---

### Post by bren on 2007-06-15
following the wiki instructions in post #9 worked good for me

xp box on wireless playing music on wired ubuntu box

on the xp box going to network places and then MSHOME / SAMBA / MYFILESYSTEM is fine

not sure about the other way about though....

the xpbox sits in a workgroup called MYFIRMNAME

looking at the network from ubuntu end i only see MSHOME (created by Samba i think) and cannot navigate to workgroup MYFIRMNAME where i had set up a shared folder in XP

Hope that makes sense
Any help appreciated.

bren


EDIT - workgroup MYFIRMNAME now appears

I can click on MYXPBOXNAME in this workgroup but it asks for a password to login

It doenst accept my standard XP login

---

### Post by BLTicklemonster on 2007-06-15
> **bren said:**
> 


EDIT - workgroup MYFIRMNAME now appears

I can click on MYXPBOXNAME in this workgroup but it asks for a password to login

It doenst accept my standard XP login

Bingo. That's what I'm trying to get away from. I can go to any folder from any windows machine here on Ubuntu and see what's in them without ever being asked for a password or anything. I want it like that when I'm on a windows machine looking at shared folders I have on my Ubuntu machine.

---

### Post by bren on 2007-06-15
hi BLT
 
ok i think i set the samba user name and password up wrong.
i should have used my standard xp login details when creating the samba usr

i got this idea and a few others from here

[http://ubuntuforums.org/showthread.php?t=202605&highlight=xp+network+loging](http://ubuntuforums.org/showthread.php?t=202605&highlight=xp+network+loging)

good luck

bren

---

### Post by gdoermann on 2007-06-16
> **Tyke91 said:**
> grr... If i could program, i would create some sort of graphical thing where it would ask you your username, password, and I.P. adress of connecting computer... if only i could program ;)


*note to self, get 1337 programming skillz*

I vivaciously agree.  I think that this is an area that needs to be improved in Ubuntu for it to become more mainstream.  As much as many of us dislike Microsoft products, I think seamless communication with Windows is vital to Ubuntu's success in General Public/Mainstream usage.

---

### Post by gdoermann on 2007-06-16
> **BLTicklemonster said:**
> Bingo. That's what I'm trying to get away from. I can go to any folder from any windows machine here on Ubuntu and see what's in them without ever being asked for a password or anything. I want it like that when I'm on a windows machine looking at shared folders I have on my Ubuntu machine.

You do not have to enter your password each time if you create an account in Ubuntu that matches the account in Windows (same username and password, no spaces and less than 31 char).  Then add the user to samba and then enable the user.  Wammo!  You are in business!

```
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark
```

---

### Post by bren on 2007-06-16
> **gdoermann said:**
> You do not have to enter your password each time if you create an account in Ubuntu that matches the account in Windows (same username and password, **no spaces** and less than 31 char).  Then add the user to samba and then enable the user.  Wammo!  You are in business!

```
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark
```

Hi gdoerman

Thank you for this - i get the idea now of creating samba user which has network name = windows login.

however see bold bit above.    
my windows login is my full name with a space in the middle
cannot change it since locked by work admin people

any answers?
bren

---

### Post by gdoermann on 2007-06-16
> **bren said:**
> Hi gdoerman

Thank you for this - i get the idea now of creating samba user which has network name = windows login.

however see bold bit above.    
my windows login is my full name with a space in the middle
cannot change it since locked by work admin people

any answers?
bren

samba accepts "\040" without quotes, as a space

---

### Post by bren on 2007-06-16
> **gdoermann said:**
> samba accepts "\040" without quotes, as a space


thanks gdoerman - good to know

samba actually accepts backslash convention too - i tried and it worked 

so (for others) looking to make a samba user name (which if you are accessing windows is also your windows login name) with a space in it you can use

```
sudo smbpasswd -a firstname\ lastname
```

I think gdoerman means the below will also work

```
sudo smbpasswd -a firstname\040lastname
```

bren

---

### Post by phr0ze on 2007-06-16
Did you ever specify that you want the folder to be on the ubuntu machine? Because you can share a folder on the windows machine and ubuntu will work with it fine.

---

### Post by BLTicklemonster on 2007-06-16
> **gdoermann said:**
> You do not have to enter your password each time if you create an account in Ubuntu that matches the account in Windows (same username and password, no spaces and less than 31 char).  Then add the user to samba and then enable the user.  Wammo!  You are in business!

```
sudo useradd -s /bin/true mark
sudo smbpasswd -L -a mark
sudo smbpasswd -L -e mark
```

I don't have a password for windows, now pass that by me again for a username like maybe Gunther.

(surely I'm not going to have to put a password on windows to make this work, right? Computers are for fun around here. We have a hardware firewall, and use AVG, etc, so I really don't worry about trojans and viruses, and no way I keep any banking info on any of the windows machines. Only a fool would use a windows computer for anything private)

---

### Post by bren on 2007-06-16
hi gunther

i think the above will still work for your case where you do not have a password for your windows machine if you make the samba password null or ""

> sudo smbpasswd -L -a WINDOWS_USERNAME

so the line above will ask for a password and if you hit return maybe this will work?     Maybe you could briefly turn on password for your windows box briefly to check what your WINDOWS_USERNAME is.

good luck

I am all up and running now

bren

---

