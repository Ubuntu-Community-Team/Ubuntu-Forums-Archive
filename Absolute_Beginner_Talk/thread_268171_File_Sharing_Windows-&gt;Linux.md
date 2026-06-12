---
title: "File Sharing Windows-&gt;Linux"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by johnnyloot on 2006-09-29
Hey Guys,
Ive been looking around the forums and cant seem to find a solution to what im looking for.

I have a network setup with 2 PCs, both with Win XP Pro, which share files and store all the media.

I have a laptop dual-booting XP Pro and Ubuntu 6.06 hooked up (wirelessly) to that same network.
On my Windows partition I can access the shared files via Windows File Sharing. I would like to be able to acess those files the same  way on the Ubuntu partition.

The file sharing is windows based and I dont have much control over that, I would just like to be able to access them on the laptop (preferably without changing the PCs at all).

From what I have read I would have to set up Samba not only as a client, but as a server as well on the PCs, I would like to avoid this. 

On the laptop I dont need or want any write permissions, I am just streaming video over the network to a laptop which is hooked up to a TV.

Thanks for the help

---

### Post by Old Pink on 2006-09-29
Great guide:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows) :)

---

### Post by bodhi.zazen on 2006-09-29
[file sharing](http://ubuntuforums.org/showthread.php?t=218630)

---

### Post by morphodone on 2006-09-29
If I understand your question correctly...

You want access to the two XP pc's from your ubuntu/xp laptop.
You can access them with xp on the laptop but not on ubuntu.

All you need then is to install samba on ubuntu.  It will
not automatically share anything on ubuntu but you should
be able to automatically see the XP boxes.

---

### Post by louieb on 2006-09-29
I have Ubuntu Linux installed on a couple of desktops and XP installed on another desktop all connected with wire through a router mainly for internet shareing. I also have a laptop (xp) that connects to the router through a wireless conection. I did not do anything special to be able to read the shared folders on my XP boxes from ubuntu. 

I go to places > network servers > ... until I get to the folder on XP that I want. 

BTW It the other way around I am still having trouble with. That is getting to data stored on Linux from windows.

---

### Post by kenshintomoe225 on 2007-03-08
a super easy solution I have found is just use an Apache server on the computer you want to get files from and download them.  Its super simple, although probably not the most secure way to just get files from one system to another.

On the system you want to take files from download and install Apache.  Its a pretty simple install.
Once that is done look for the config file and open it up, its just text.
Look for a line that says

DocumentRoot

and next to it should be a directory, change this to whatever directory you would like to share your files from.

do the same things next to the entry:

<Direcotry ...

then start/restart your apache server.  Now just put whatever files you are gonna be sharing in that folder you just gave the location of in the config file.  

Now go over to the computer you are gonna be putting the files on and open up a web browser.  Apache is an http server so as long as it is running (and you have your firewall either configured correctly or (dont do this) off) you will be able to access anything in that folder you specified earlier.  
In your address bar type in

*the ip address of the apache machine*/name of file

and there you go

now the main problem with this is the fact that your computer is now an http server and as such will be accessible to anyone who knows your ip address, which is probably not likely but you can never be too careful.  However, if you just wanna get that one song from your windows machine to your ubuntu machine this is a very easy, fast, and simple way to do so.

---

### Post by dstew on 2007-03-08
Despite what I have read in some posts, Samba has worked well for me. You do not need to do anything to the Windows machines, just make a shared folder as if you were sharing with any other Windows machine on the network. Install Samba client on your linux system. Read the man pages to see how to use it. Basically, you make a mount-point for the share, like a folder in your home directory (Windows_share for example). To mount the share, use the smbmount command.

sudo smbmount //server/sharename ~/Windows_share

---

### Post by kenshintomoe225 on 2007-03-09
i'll have to try that as well as the method i described is only one way and doesnt give too many options.

---

