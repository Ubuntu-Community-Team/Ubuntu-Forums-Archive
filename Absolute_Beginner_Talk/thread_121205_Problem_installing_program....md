---
title: "Problem installing program..."
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by sudirt on 2006-01-24
**Disclosure:** I am new to this...please assume that I have no prior knowledge of Ubuntu or Linux in responses. Thank you.

**System:** PowerEdge 2450, Ubuntu 5.10, Automatix used to get Java 1.5

I need to install Seatools Enterprise on this system to test fibre channel hard drives through a PowerVault 660F. 
**I use Seatools because it is free though I am open to suggestions on any other program that might be more compatible with Ubuntu**

**Process:** I downloaded the RPM from seagate.com, got Alien, converted the RPM with Alien to a Deb file, finally, used the command sudo dpkg -i <deb directory> to extract the file.

**Problem:** I am missing a folder and a few files through that process in the desired folder: usr/local/Seatools. The reason this is happening is because I am denied access due to the owner being ROOT. The files I need are inside a file named: Data.tar.gz. Is there a way that I can perhaps extract the needed files from the .tar.gz file type to a "ROOT owned folder"? 

Thank you for any help/advice.

Sudirt

---

### Post by sudirt on 2006-01-24
[QUOTE=sudirt]The files I need are inside a file named: Data.tar.gz. Is there a way that I can perhaps extract the needed files from the .tar.gz file type to a "ROOT owned folder"? 
Sudirt[/QUOTE]


**Update:** I attempted to use the "gunzip" and "tar xf" commands to extract, but it only extracts to the current folder that the file resides like I unfortunately expected. I will continue to search the net for solutions until someone might be able to help me.

Thanks ahead of time for any help/assistance.

Sudirt

---

### Post by public_void on 2006-01-24
See this link found in aysiu sig (IMO great link) [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php). When installing .deb file no files are extracting like with .tar.gz files. The command "sudo dpkg -i <File.deb>" will install the file for you.

EDIT: On reading again I may have get the wrong idea. Hope what I said helps somehow.

---

### Post by sudirt on 2006-01-25
Thanks for the advice...Though it will not resolve my problem. I think though that it addresses the fact that I have some dependencies that I need to install **the files that I can't write to the /usr/local/Seatools folder** 

I still need a way to take the files/folders in the data.tar.gz file and put them into the folder /usr/local/Seatools. I will conquer this problem one day...Hoping that today is that day hah. It had frustrated me for about a week now.

Just fyi for anyone that reads this:

1. Tried to just do the install for the RPM with alien *failed*
2. Tried to convert to a .deb with alien, then install *failed*
3. Tried to install in a different directory with all dependent files *failed because I do not have the knowledge to edit the proper programing files to point to new target locations*
4. Tried to copy/paste *failed owner is ROOT*
5. Tried kpackage *failed*
6. Tried the Synaptic Package Manager *failed*
7. Awaiting any ideas.

Thanks ahead of time

Sudirt

---

### Post by steve.horsley on 2006-01-25
When you copy files to /usr you need root privilege.

You can gain root privilege for any command by prefixing it with **sudo**. 

If you need to do lots of things as root you can say sudo bash, which leaves you in a root shell (# prompt), and you can do what you like, and use **exit** when finished. 

If you prefer a GUI file manager, use **sudo nautilus**. This launches the file manager with root priv. Use File->New Window if you want to drag/drop between windows as root - the new window will also have root priv. I always change the background to red on my root nautilus, so I don't forget it has extra destructive privs.

---

### Post by sudirt on 2006-01-25
Great!...ok thanks steve.horsley. I am trying right after I type this.

Sudirt

---

### Post by sudirt on 2006-01-25
Ok...that worked 100% thanks a TON! Yet now I have one more problem. I think it is much more simple though.

I need to create a symbolic link: ldconfig
/usr/local/Seatools/lib

But I am denied permission. Is there a way I could do that through Nautilus?

Again thank you a ton.

Sudirt

---

### Post by Perfect Storm on 2006-01-25
sudo ln -s <source path> <destination path>

---

### Post by sudirt on 2006-01-27
Thanks again guys. I got the link in and everything will atleast come up, yet now I am getting a different set of errors. Either Seagate didn't think the linux version through too much, or there are still some files that are not found when Java goes to access them. I have no idea.

I wonder if anyone on the boards use Ubuntu as a server with fibre channel drives...or for that matter if anyone has ever messed around with Seatools at all. I have no problems with Windows at all, but well with costs and such for my boss to worry about, he has been hiding from me! 

Thanks again,

Sudirt

---

