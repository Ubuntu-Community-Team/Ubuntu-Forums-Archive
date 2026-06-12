---
title: "Windows Shares"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by joey222 on 2006-01-23
Hey guys, another somewhat linux newbie :p  so dont be hard on me. 

I am trying to set up samba on vr5.10 so i can access my Windows HD and also be able to access a linux share via Windows. 

I have followed these guides to the later:

[http://ubuntuguide.org/#automountnetworkfoldersall](http://ubuntuguide.org/#automountnetworkfoldersall) and here:
[http://ubuntuforums.org/showthread.php?t=76647&highlight=windows+shares](http://ubuntuforums.org/showthread.php?t=76647&highlight=windows+shares)

to no joy. 

This is what i see from windows:

[IMG]http://i4.photobucket.com/albums/y105/joey222/MshomePic1.jpg[/IMG]

and when i try to access it, i enter my username and password, and this keeps poping up.
[IMG]http://i4.photobucket.com/albums/y105/joey222/MshomePic2.jpg[/IMG]

from the linux box this is what i see:
[IMG]http://i4.photobucket.com/albums/y105/joey222/Screenshot.png[/IMG]

And the same thing, everytime i put in my password it shows up again. Its not my password cause i know its right :)

Any help would be great guys and gals

---

### Post by FlightlessWaterfowl on 2006-01-23
Joey,

I frequently need to transfer files between my Ubuntu box and my Wife's XP box, and have encountered similar problems.

I found that when connecting from XP to Ubuntu, it is helpful to change the username from *UBUNTU\joey* to simply your Ubuntu login (presumably just *joey*), along with your Ubuntu password.

Secondly, when connecting from Ubuntu to XP, I have found that I am always presented with an intitial login for the *local* machine (in your case, UBUNTU). After I cancel the initial *Authentication Required* window, I am then presented with a login for the XP box. There, I enter my local username in XP, set the Domain to the hostname of the XP box, and finally my XP password.

I hope that helps!

---

### Post by joey222 on 2006-01-25
still didnt help mate. 

check here for my smb.conf file: [http://paste.ubuntu-nl.org/7626](http://paste.ubuntu-nl.org/7626)

---

### Post by Zimmer on 2006-01-25
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)

Have a look at this thread for posts regarding adding Samba Users.....

Regards

---

### Post by joey222 on 2006-01-26
I have already added the same user that i use on thw windows box

---

### Post by Iowan on 2006-01-26
I'm probably waay off base, but the workgroup for the Samba server is set BEGIN1... the login screen is workgroup/domain MSHOME.

---

### Post by joey222 on 2006-01-26
i seen that to but wen i change it to BIGIN1 its doesnt make a diffeerence :(

---

### Post by AndyCooll on 2006-01-26
Just a couple of thoughts.

Are your two pc's on the same domain?

On your Linux box have you manually set your password for Samba?

```
smbpasswd -a yourusername
```

It will then ask you to input a password

:cool:

---

### Post by joey222 on 2006-01-26
I started all over again using this page:

[http://easylinux.info/wiki/Ubuntu#How_to_mount_network_folders_on_boot_up.2C_and_allow_all_users_to_read.2Fwrite]("http://easylinux.info/wiki/Ubuntu#How_to_mount_network_folders_on_boot_up.2C_and_allow_all_users_to_read.2Fwrite")

This is from my Terminal:

> joey@ubuntu:~$ sudo apt-get install samba
Password:
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joey@ubuntu:~$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree... Done
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joey@ubuntu:~$ sudo mkdir /media/linuxshare
joey@ubuntu:~$ sudo gedit /root/.smbcredentials
joey@ubuntu:~$ sudo chmod 700 /root/.smbcredentials
joey@ubuntu:~$ sudo cp /etc/fstab /etc/fstab_backup
joey@ubuntu:~$ sudo gedit /etc/fstab
joey@ubuntu:~$


And i still get the same result. 

Can anyone help :confused:

Has anyone got any links to a tutorial or anything that explains everything about getting samba to work. 

All i want to do is to be able to pull files from a Hard Drive on my Windows machine to a folder in linux and from the folder in linux to windows. 

Thanks
Joey

---

### Post by Iowan on 2006-01-26
Short term:  Try editing the /etc/samba/smb.conf file - make "workgroup = MSHOME" to make Samba serve the default windows workgroup.

---

### Post by mettallicat on 2006-01-26
try to put samba checking users from pam ... i know that is possible check out the samba webpage...

another thing .. in order to some machine connect to your samba you sould make that folder public or add the name of windows machine to your smbpasswd and passwd file.

i don't remember well of all this but check on "http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/"

---

### Post by Mutt on 2006-01-26
I'm no expert and what I did could very well be wrong but this is the way I got around the same problem.

On the windows box go to start > control panel > folder options > view and uncheck "use simple file sharing".

Then run the set up a small office or home network wizard and you will find an option to share flies and printers, check that and you should now be able to access windows from the linux box using your windows user name and password.

John

---

### Post by mettallicat on 2006-01-26
i'm not use to make shares with GTKappz :D

i make Primaries Domain Controlers with samba :D

---

### Post by breezyfox on 2006-01-27
Hi 
I had the same problem in the begening but working around and serching some resources i was able to share files from both and it is very easy.
Do the following:

1.you need to create shared folders that you want to share.

2. you need to either create a user on your ubuntu box with your windows login or create a window login with the same user name on your ubuntu machine.
optionally you can have the window login and password as your linux samba name and it willmnot prompt for password.this ofcourse has a security issue.
you can play around later to tighten security.

3.edit /etc/samba/smb.conf file and look at section security = user. just change this to security = share.
now you be able to access the shares.but time now to tihten yiur security and play around and other members wil also help.

after every change in your conf file do restart samba by doing 
root@XXxx$/etc/init.d/samba stop
                /etc/init.d/samba start
your workgroup should be the same. i am sure it will work.
to create share system>administration>sharedfolder and create share.

all the best. let us know. we then can work on security issues.

brz

---

### Post by bavs on 2006-01-27
have  u tried setting windows firewall settings??
thats all i can say coz mine works fine

all i did was 
sudo smbpasswd -a (username)

---

