---
title: "[SOLVED] Changing permissions in a network drive."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-03
I have an External hard drive (my Book World)  that is connected via ethernet cable and therefore is accessed through 

Places/Network/MSHOME/Mybookworld.

Currently the permissions are set at read only and the owner is listed as unknown. 

Does anybody know how to change the permission for this type of drive?

---

### Post by GMachine_24 on 2007-09-03
> **cwrann said:**
> I have an External hard drive (my Book World)  that is connected via ethernet cable and therefore is accessed through 

Places/Network/MSHOME/Mybookworld.

Currently the permissions are set at read only and the owner is listed as unknown. 

Does anybody know how to change the permission for this type of drive?

Is it connected to your Ubuntu computer or to a Windows computer .......???


Using the "chmod" command is relatively easy..... 

you can read about it by typing

man chmod | more

at a command prompt and hitting the space bar when you need to read more.

On an Ubuntu / Linux machine accessing a drive is relatively simple....

I use

<code>

user@computer~$sudo chmod 777 /pathtofolder/folder_to_enable

</code>

to enable universal read & write of a drive or folder.

You could try this on your book drive, making sure to select only the options you want to enable/disable.... or if it's on a Windows machine you have to do it from there.

[how do you connect a drive via a network cable?]

--gm

---

### Post by cwrann on 2007-09-03
The external Hard Drive is hooked up to my Computer via ethernet cable plugged into my wireless router. The only operating system on my computer is Ubuntu. For some reason when I plugged the ethernet cable into my router and browsed under "Connect to server" the hard drive appeared under MSHOME. 

My main confusion is that I'm not sure what the path to the folder is because of the way it is connected. 

I'm not even sure if it is listed here:

/media$ ls -al
total 28
drwxr-xr-x  7 root root    4096 2007-09-03 20:43 .
drwxr-xr-x 22 root root    4096 2007-08-12 00:27 ..
lrwxrwxrwx  1 root root       6 2007-08-05 12:15 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2007-08-05 12:15 cdrom0
lrwxrwxrwx  1 root root       7 2007-08-05 12:15 floppy -> floppy0
drwxr-xr-x  2 root root    4096 2007-08-05 12:15 floppy0
-rw-r--r--  1 root root       0 2007-09-03 20:43 .hal-mtab
-r-Sr-----  1 root root       0 2007-04-15 08:03 .hal-mtab-lock
drwxrwxrwx  3 root root    4096 2007-08-25 12:09 sda1
dr-xr-x---  1 root plugdev 4096 2007-08-17 21:44 sda2
drwxr-xr-x  2 root root    4096 2007-08-27 19:27 sharename

Any suggestions?

---

### Post by GMachine_24 on 2007-09-04
Ok, I still don't get it. You need an interface to connect a hard drive to a computer - and especially to a network. You can't just plug a hard drive - at least not as far as I know - into a router. You need a network cable and an RJ-45 jack to plug into the router and then on the other end some device that you plug your network cable into .........like a network (NIC) card attached to a computer ........which then has the hard drive attached to it via a PCI, USB, Firewire or other connector. External hard drives can also be connected if they are connected via a USB or Firewire cable and plugged directly into your Linux/Ubuntu computer. According to what you have told me, neither of these describes how your hard drive is connected.

As things are, I can't help you.

Again, I ask you: ARE YOU SURE YOUR YOUR HARD DRIVE IS CONNECTED VIA A NETWORK CABLE? WOULD YOU BET YOUR LIFE ON THIS?

I am guessing there is a major part of this story you are leaving out. At the very least you have to explain how you attach a network cable to a hard drive. I asked you this before and you didn't answer. You have to answer this question. It just doesn't make sense.

You need to have your hard drive mounted on your Linux computer. Typically hard drives are listed in either the /dev folder (under hd*) if they are attached via a PCI/IDE connector or sd* if they are attached via a SCSI or other card. Sometimes hard drives attached via PCI cards get listed as sd* devices as well.

If you attach an external hard drive, they typically show up in /media and also, frequently, with an icon on your desk top. These are typically connected via a USB cable or Firewire cable. I'm guessing you don't have an icon on your desk top and I'm guessing your Mybookworld drive is not listed in /media, either.

--gm

---

### Post by cwrann on 2007-09-04
The hard drive in question is an external hard drive. It does not connect to my computer via usb or firewire but by ethernet cable. This is the only way that this external hard drive can connect to my computer. The ethernet cable connects to my router and the My Book World icon appears under MSHOME in network. I have a second ethernet port in my computer that I was originally trying to connect the external hard drive to the computer with but this method did not work, the external hard drive didn't show up anywhere. I then plugged it into my router, at first nothing happened but that was because my network settings were set at static IP. I changed it to DHCP and the externa hard drive appeared under network.

It is connected by ethernet cable I would bet my life on it, if I had to do it over I would not have bought a My Book World I am just trying to work a bad situation.

---

### Post by qpieus on 2007-09-04
It looks to me like your computer is seeing the external drive as a samba shared folder, and that's why you can't change permissions. It doesn't show up when you "ls -la"  because that drive is not mounted anywhere on your filesystem.

Does the external drive have some kind of web interface you can access? I don't have this type of drive, but I've heard that external, network enabled drives usually have a web interface. If it does, maybe somewhere in there is a way to set permissions. Another option that may work is to mount the samba share into your filesystem. Then you should be able to change permissions and owners just like any other directory or file.

---

### Post by cwrann on 2007-09-04
The web interface for this drive is Mionet which is not compatible with linux systems. 

How do I mount the samba share into my file system?

---

### Post by qpieus on 2007-09-04
I have not actually done this, so I may be talking out my butt :). I did some searching here and it looks like you want to use cifs to mount the shared folder. Here's some threads that discuss cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)
[http://ubuntuforums.org/showthread.php?t=318943&highlight=cifs](http://ubuntuforums.org/showthread.php?t=318943&highlight=cifs)
[http://ubuntuforums.org/showthread.php?t=508785&highlight=cifs](http://ubuntuforums.org/showthread.php?t=508785&highlight=cifs)

There's also this in the community documentation area:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

The quick summary is that you'll need the IP address of the external drive and you'll end up putting an entry in your /etc/fstab file to make the drive mount in your filesystem. The fstab entry looks something like this:
//192.168.1.16/NETfolder	/home/jonboy99/netmount cifs user,username=admin,password=xxxxxx,iocharset=utf8,file_mode=0777,dir_mode=0777

//192.168.1.16/NETfolder = shared folder on drive
/home/jonboy99/netmount = mount point. You can create a folder name of your choice.
cifs  -  tells the OS to use the cifs protocol to mount the folder
The rest of the stuff are the some of options that can be used with cifs in fstab

I hope these threads can help....

---

### Post by cwrann on 2007-09-08
Thanks for all your help, I read through all the links that you provided and they certainly helped me understand how to set up a regular net work but I think that this problem is just beyond me. I tried editing fstab but to no avail I can't seem to figure out exactly what I'm doing.

---

### Post by niranjan on 2007-09-11
I have similar MyBookWorld.
[http://www.wdc.com/en/products/products.asp?driveid=319&language=en](http://www.wdc.com/en/products/products.asp?driveid=319&language=en)
It is one of these newer ethernet connectible hard drives.

It is rather simple: You can not change its permissions via external OS, since it is running its own linux/samba/apache, and allows windows like shares. 

You have to get to it via its http server and create shares and users, and assign permissions.

You will need to know its IP address, presuming you have not hooked directly into your Ubuntu/Windows PC, but via a hub or switch, in which case it gets IP address from the same DHCP server as your PC, and is in the same subnet. If so then just writing the IP in the Browser will  give you access to its Config Manager and change the way you want it. You will need to read the documentation of the device to know the username and password you could use to make the changes.

Once you know the IP address it is simple. In case you do not know the IP address, then a little more work is needed but it surely will work.

niranjan

---

### Post by cwrann on 2007-09-11
Finally a fellow My Book world user!!! Thank you for your help. I tried every way to connect to it through the Ubuntu network features and could not figure out how to wite to it. I never thought to write the IP into the browser. Now I got it to read and write to the public folder. Within that folder is every other folder that I have. I can read those folders but not write directly into them, is there a way to solve that?

Also I simply assigned full permissions to everyone. How can I change it to only allow myself full read and write permissions?

---

### Post by niranjan on 2007-09-12
I am glad you could get to its admin page.

"Now I got it to read and write to the public folder. Within that folder is every other folder that I have. I can read those folders but not write directly into them, is there a way to solve that?"

Right now I am in a hurry to give you a step by step guide so I will simply put some hints, and hope that lyou will find out the answers by trial and error or reading the manual.

-  First you should take control of the device by changing its admin pasword etc. You do that by Accessing General Setup Tab and then Update Admin Username and Password [Advanced]
- Second, create local users on the device. It does not accept users on other OSes (whether you access it from Linux, Windows or Mac.)
- Then you should create a shared folder. Once you have the folder shared, you can go to File Sharing tab, chose the right folder and chose 'Change security settings'. The device comes with a default folder called PUBLIC, which you have been using, but you should create folders other than PUBLIC and set permissions as you wish.

That is all about it.

Remember that you may chose the same user names as you may have on your Ubuntu or Windows, but you have to login (supply username and password) to the device at the time of  accessing the folders (or mapping to the drive), and only then permissions defined on the device, not your Ubuntu box, will be in force.

I will try to check this thread again somtime later. Feel free to ask if there is any other questions.

haven't spell checked, sorry for any typos..
niranjan

---

### Post by cwrann on 2007-09-12
Thank you very much for your help. When You say:

> It does not accept users on other OSes (whether you access it from Linux, Windows or Mac.)

Does this mean that if the IP address belongs to a linux system it can only be accessed by linux systems?

Also when You say create local users, do I make myself a local user by putting in my login information to my computer. In other words if to acces my computer I type in "Ububntu" at the login screen and the password "123456". Is this the information I give the configuration manager? 

I have the drive linked as a windows share with samba I don't enter and user information or password to access it so what user does it see is accessing it?

thanks again.

---

### Post by niranjan on 2007-09-13
> Does this mean that if the IP address belongs to a linux system it can only be accessed by linux systems?

The IP address never belongs to an OS (Linux, Windows, Mac, Solaris etc.) IP address is the address for a physical device (in this case the hard drive, which is running its own OS, but it can be anything like a computer, VOIP device or a PDA etc.)

You can identify and access the device via its IP address, or alternatively by its name translated to IP address via a DNS server. 

Your device presently allows two types of connections FTP and so-called Windows Share. Just like a Windows based machine would accept connections from any other device, but based on its own user-base. I mean one has to have a usernme and password and particular permissions linked to the shared folder and username on that device. Even though MyBookWorld (and similar devices like Lacie etc) locally runs some version of embedded Linux, it has a basic configuration of a Samba system to allow Windows users to access its shared folders as they are normally used to do. (obviously their lions share of users are Windows users).

To use your device, you should simply do the following:
[LIST]
[*]open the admin page of the device via its IP address (or even writing the name of the device like [http://myWorldBookWorld.local/](http://myWorldBookWorld.local/))
[*]crate a share other than PUBLIC
[*]create users (you do it by going to 'File Sharing' => 'User Management')
[*]create a set of permissions by going to  'File Sharing' => 'Update Security Settings'
[/LIST]
When you are done, you access the shared folder from Ubuntu like this:
[INDENT]Places => Connect to Server
Service Type = Window share, 
Server = Name or IP address of the device, 
Share = Name of the shared folder
UserName = the one you created on the device, not the one on your current computer
Domain Name = default one in the device is MSHOME, (I would suggest you change it on the device. I have changed it to the name of my street)
Name to use for the connection = The name with which the icon will appear on your desktop.[/INDENT]

Now when you connect, it should ask you for the username and password (only password in case the username is the same on both)

If you need to connect to the same folder via Windows you will do Map Network drive => Use Different Username => and provide username and password. (Windows would usually assume the same Domain name, but you can change it by domainanme/username).
 
> Also when You say create local users, do I make myself a local user by putting in my login information to my computer. In other words if to acces my computer I type in "Ububntu" at the login screen and the password "123456". Is this the information I give the configuration manager?

You already have a local account on your computer. That is what you use to login to your Ubuntu, BUT in order to access the shared folder, you have to provide the local (meaning user on the device) username and password. **Since you are currently accessing only the PUBLIC folder, and I guess its permissions allow everyone to access it, it is not asking for any password or user name. It will change once you do create a share which has limited access.**

> I have the drive linked as a windows share with samba I don't enter and user information or password to access it so what user does it see is accessing it?

It does not worry about username becuase the folder by default is open to all, but with no write permissions. Take a look at Config Page of the device, 'File Sharing' => chose the share PUBLIC and see 'Update Security Settings' and you will immediately notice what I am trying to say.

You would be better of if you change the name of the device to soemthing better than MyBookWorld, and change the Domain Name to something better than M$HOME. :)

Hope it helps you
niranjan

---

### Post by cwrann on 2007-09-13
You have been a huge help, thank you very much.

---

