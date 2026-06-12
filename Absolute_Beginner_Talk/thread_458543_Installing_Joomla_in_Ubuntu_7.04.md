---
title: "Installing Joomla in Ubuntu 7.04"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by crazydiver on 2007-05-29
Hello All,
 

      As of now, I am trying to successfully install Joomla.

 I have completed  installing the LAMP stack manually via synaptic package manager.
  
   Thereafter, I downloaded the Joomla package (Joomla_1.0.10-Stable-Full_Package.tar.bz2)  from Joomla.org and don't know how to proceed from there.

 According to this page, [https://help.ubuntu.com/community/Joomla?highlight=%28joomla%29](https://help.ubuntu.com/community/Joomla?highlight=%28joomla%29) , it instructs me to 
"Unpack it and then copy it to your webserver directory."  How do you do that??? and where is the webserver directory???  

 right beneath the instructions are these command codes

tar xvjf Joomla_1.0.10-Stable-Full_Package.tar.bz2 
sudo mv Joomla_1.0.10-Stable-Full_Package.tar.bz2_FILES /var/www/joomla
sudo chown -R www-data:www-data /var/www/joomla

I type them into a terminal and I get a message saying that error is not recoverable, or a message requesting a password. When I enter my user password, nothing happens.

 I did all the googling to solve my problems and I have been unable to succeed. 
 This is my third day using Ubuntu 7.04 and its been fun yet hard to learn!
All comments and possible solutions arehighly  appreciated and thanks for reading this!!!
:p

---

### Post by silent1643 on 2007-05-29
download the package, then upload all the files to your webserver, then navigate to the install directory and follow the steps should be simple...  do you have webspace? use an ftp program to upload the un packed files.. i think there is even an extension on joomlas website that will download and extract the files on your web server for you. this is more of a joomla forum question than a ubuntu question.

---

### Post by crazydiver on 2007-05-30
Hello Silent 1643,

   Thanks for your reply and I agree that this should be a Joomla forum...  I think I can get more of a jist of what Joomla is by checking out their forum.
 
   The problem I have with uploading the files to my web server is that I don't quite understand that direction. Is the web server a file in my computer (like a local installation) or do I need to subscribe to a web hosting service to have a web server?
 I'm confused. too much thinking I guess!
  But thanks for your time silent1643!:o

---

### Post by mlentink on 2007-05-30
You say you have installed LAMP, which stands for Linux Apache MySQL and Perl/PHP/Python.
So you must have installed the Apache webserver. Apache looks for files to serve in /var/www, so that's where your joomla files need to go. If you're on the same machine, try opening up a browser and open up localhost ([http://127.0.0.1](http://127.0.0.1)). What do you see? If you haven't uploaded any files yet, you should see a message from Apache that it has been installed correctly.

---

### Post by opossumjack on 2007-05-30
If you need Joomla to manage your personal web site, you need a web space first. You should subscribe to a hosting service. Every web spaces stands on a web server. You need to upload the joomla package onto your remote web server, where the site is located, using an FTP program or the file-uploader of your web space (usually in the control panel of your web space).

Then when you have uploaded it succesfully, you could follow the installation instructions.

---

### Post by crazydiver on 2007-05-30
Hello mlentink and opposumjack,

&#12288;Thanks for the advice.

 mlentink, when I open up my browser and check up my local host at [http://127.0.0.1](http://127.0.0.1) I see 

Index of /
[ICO]	Name	Last modified	Size	Description[DIR]	
apache2-default/	21-Nov-2004 05:16 	-
Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at 127.0.0.1 Port 80

I click on apache2-default/ and the message "it works" appears.... so I must be doing something right.  
Next I try to extract the Joomla package to /var/www/ and I get a message saying that I do not have permission to write to the folder.  I don't understand why I get this message, I'm the only user of my comp! 
I tried googling to solve this problem and found a post concerning su. I do the whole terminal thing with su, put in my password and get the message authentication failure sorry...  I think something is wrong.


opposumjack, subscribing to a webserver is another option I am going over as of now but I hear that with the use of Apache, that using web server is free... Is that true??? If so, I got to learn to use this stuff!

---

### Post by mlentink on 2007-05-30
> **crazydiver said:**
> I click on apache2-default/ and the message "it works" appears.... so I must be doing something right.  
Next I try to extract the Joomla package to /var/www/ and I get a message saying that I do not have permission to write to the folder.  I don't understand why I get this message, I'm the only user of my comp!
Your Apache server is working allright, so you're pretty much ok.
As for the copying: you are most certainly not the only user of your computer. There's always root, although in Ubuntu, root is hidden. Are you using ***sudo*** mv etc? That first sudo command is really important, because it makes you the superduperrootuser. You should then be able to move those files over to /var/www

---

### Post by crazydiver on 2007-05-30
Learning a lot mlentinkt.;) I didn't know that I'm not the only user to my computer. Sorry to say but I'm not sure if Im using sudo!  Btw, is there any other way to transfer the files without becoming a superuser? If not, how do i become a rootsuperuser?
  Sorry to bug all of you but I really thank all of you, esp mlentink!

---

### Post by mlentink on 2007-05-30
Don't thank me, I'm just one page ahead of you. 
Basically Ubuntu lets you become the root user by having you prefix all commands with "sudo" (don't ask me what it means, maybe something like 'as superuser do:'. So every command that follows 'sudo' is executed as if you were the root user.
e.g.
mlentink@mymachine$ cp file1 file2 (executes as current user)
mlentink@mymachine$ sudo cp file1 file2 (executes as root)

You need to have root privileges to copy files to a directory owned by another user. And /var/www is owned by Apache, or by root most likely.

So if you use the mv command to 'move' files to a directory not owned by you as the current user, make sure you precede it with 'sudo'

---

### Post by crazydiver on 2007-05-31
Mlentink and all, thanks! I appreciate all the support!

---

