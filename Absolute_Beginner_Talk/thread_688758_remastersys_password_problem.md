---
title: "remastersys password problem"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by dabsan on 2008-02-05
I have been trying to re-install from a DVD I made with remastersys but it asks for a password before installing. I have tried my password but it still doesn't work. Can anyone help me?

---

### Post by rachel10123@msn.com on 2008-02-08
Try remaking the DVD.

---

### Post by gilf on 2008-02-10
Same problem here. Why would re-making the DVD produce a different result?

---

### Post by gilf on 2008-02-10
Unless you do something differently.

Here's a possible explanation of what happened in our cases:

> You should start with a clean install of Klikit, Ubuntu or variant and use a single user to make all changes.  You should not install any proprietary video drivers like the nvidia or ati drivers as they will not be used on the livecd and users will have to reinstall them after installation.  Clean up history and cache and copy over the contents to /etc/skel but be sure to change the ownership of everything in /etc/skel to root.  While the livecd/dvd is being created, you will not be able to open any other apps or windows.  It is highly recommended to become root to do this by issuing "sudo su" in a terminal window and then running "remastersys dist".  The reason for this is that the uid for the users on the system have to be changed to be below 1000 or the casper livecd scripts will not create the live session user properly.  Remastersys will restore the UID's back to their original values once it is finished.

---

### Post by gilf on 2008-02-11
Tried it again with same results.

Finally, solved.

The how-to repository isn't current.
  
update /etc/apt/sources.list with


> # Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

then reload
then upgrade Remastersys to latest.

The password problem is a bug.

Newest version has a GUI, as well

---

### Post by gilf on 2008-02-11
This is like pulling teeth.

The new version worked great up to the point of making a good LiveCD that no longer required a password for root operations.

However,
Upon doing an install of that system to HD, and rebooting to HD, another problem occurs. 

The Ubuntu login screen appears. It won't accept "custom" or "ubuntu" or "root", or blank in any combination as username and /passwords, but it will accept my old username and password. 

However, the login gets no further because the system cannot find my /home/username folder.

I've put the question here:

[http://loscompanion.com/forums/index.php?topic=1962.0](http://loscompanion.com/forums/index.php?topic=1962.0)

---

### Post by dabsan on 2008-02-11
Thanks for all the postings. There seems to be a lot of problems with this software.
I will experiment with a few ideas and try installing into virtualbox. 
One idea I had was maybe adding into Users and Groups, Manage Groups, Add Group, remastersys, Properties and selecting user name and root. Not sure if this will make any difference. 
Many Thanks

---

### Post by dabsan on 2008-02-12
Hi, I have successfully installed into Virtual Box, so I guess installing for real would be ok also.

I think adding into Users and Groups, Manage Groups, Add Group, remastersys, Properties and selecting user name and root is the way to get this to work, doing that before making your CD image. 

If anyone tries this let me know if it was successful. 
Thanks :)

---

### Post by gilf on 2008-02-13
It turns out after much duiscussion, that remastersys at present, does not support setting up a user in a HDinstall from a remastered LiveCD who* has the same username* as the one who created the LiveCD.

In other words, if user Tom makes a liveCD with  remastersys, he cannot do an HD install from that disk and set up a primary user named Tom. The system will not create a /home folder for Tom in that case

I got around this limitation by using a liveCD to insert a /home/tom folder copy from my main system,( pruned of some data)  into the new HDinstall

I then booted into failsafe mode and issued

> chown -R tom: /home/tom

This seemed to work -- to allow me to login as tom. I don't know if there will be any adverse effects of the chown -R or the "foreign" user home directory.  Perhaps others with more experience will comment here.

Another thing to be aware of when installing the new remastersys with GUI:

It will place two shortcut icons on a gnome desktop -- identical looking. If you do a properties, however, you will see that one does a kdesu command (for Kubuntu or KDE systems, only) and the other does gdesu (for ubuntu and gnome systems). If you want use a desktop icon to start the program, be sure not to discard the appropriate one for your system. Easy to do if you don't realize they are different. I got rid of them both because I prefer to do it from the terminal -- you also have the option of running the GUI from the System Administration dropdown.

Another unexpected occurence will be that an installed system will still have the LiveCD's **Install **to disk Icon on the desktop, unlike a normal Ubuntu install, which removes it. You normally only see it on the LiveCD session. I don't know what would happen if you tried to use it, but personally, I sent it to the trash. Seems like you could do some damage with it, and I don't understand the purpose.

Hope this helps others.

---

### Post by iamkrazee on 2008-05-20
I'm using 2.0.5 right now and much to my dismay, the same password issue persists with strangest of errors such as "user not known to underlying authentication module" or a KDM crash in graphical mode telling a similar story. What if I just WANT to have a username with my own password? Does(/Will) creating a system user work? As in when creating a liveDVD I'll have created a couple of usernames with "useradd -r", set some passwords manually and then go "remastersys dist" .. ?

---

### Post by lisati on 2008-07-04
I stumbled onto this thread researching an unrelated problem with a disk I'd created myself with remastersys. 

I encountered the same issues about needing a password. The solution for me was to start the live CD, log out, and then log back in as myself. For the particular LiveCD currently in my machine logs in as "Ubuntu", but still has the users I'd set up on the system I created it on.

(Trouble is, on the disk I created, the install failed: an error popped up during the copying of the files about "not a file or a directory. Back to the research.........)

---

