---
title: "home network, windows not involved"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by shredfitz on 2008-03-10
Here'e the deal:

Windows is OUT of the picture in my home computing network. I have two machines. A thinkpad t-40 running feisty fawn and my tower that has a fresh install of gutsy.

Whenever I seek out how to have shared network folders, I am invariably led to solutions that involve a windows machine or samba or something else. That is not what I need.

I simply want to be upstairs on my Thinkpad, and if I come across a file that I want to store on a folder that exists on the hard drive of my tower, I can easily do so.

I have been hunting down the information to do this on my own, but all I can find is people talking about sharing amongst windows and ubuntu.

Can you point me to the info?

Thanks so much...

---

### Post by jcwmoore on 2008-03-10
sshfs

this program uses ssh to mount remote directories on to a local machine.  I have one machine where I use this to point the Documents folder to a folder on my server.  This sound exactly like what you want.  You'll need to install ssh server on to you tower and then sshfs to your lappy

EDIT:  A guide....
[http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html]("http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html")

---

### Post by tad1073 on 2008-03-10
have you enabled sharing? system>administration>shared folders

---

### Post by shredfitz on 2008-03-10
OK, great, thanks. What would be the procedure for doing this? Install this on both machines? Do you have a link to the most complete info for doing this? Thanks for getting me on the right path anyway...

---

### Post by jcwmoore on 2008-03-10
> 
EDIT: A guide....
[http://www.debianadmin.com/mount-a-r...ing-sshfs.html](http://www.debianadmin.com/mount-a-r...ing-sshfs.html)

I edited my post....  I think that is the guide I used when I set up sshfs...:popcorn:

---

### Post by shredfitz on 2008-03-10
> **tad1073 said:**
> have you enabled sharing? system>administration>shared folders

Yes. Question about that....

for allowed hosts...what would I enter? The IP address of the machine that will be accessing the one that I am allowing sharing?

---

### Post by shredfitz on 2008-03-10
> **jcwmoore said:**
> I edited my post....  I think that is the guide I used when I set up sshfs...:popcorn:

bummer jcw...I clicked your link and it leads to a page that says that page doesn't exist.

---

### Post by shredfitz on 2008-03-10
ok jc......got it. Gonna  get to work and see what happens. Thanks for your help.

---

### Post by jcwmoore on 2008-03-10
good luck

---

### Post by shredfitz on 2008-03-10
John- what exactly would the group name be?

---

### Post by jcwmoore on 2008-03-10
I think the group name is "fuse" but i'm not sure where you are in the process or exactly which group you are talking about....

---

### Post by shredfitz on 2008-03-10
at the link that you provided me, I am at the end of the tutorial, the 'using sshfs' portion and the example portion.

---

### Post by shredfitz on 2008-03-10
okay , at the terminal, I said this:  chown brian:fuse /mnt/remote

I didnt get anything in return, and right now I simply have a directory named /mnt/remote.

What I am expecting to be able to do is to have the ability to read and write to folders on the tower. I know you know that , I am just trying to talk this out.....not quite getting it.

---

### Post by jcwmoore on 2008-03-10
because of what I wanted to do I differed a little from this tutorial... I think you are safe to ignore the group name part for the folder in /mnt

so from where you are I did this...
I created a new folder on my desktop called "web"
I ran this command from the tutorial...
```
adduser [your-user] fuse
```
I then ran this command to mount the server folder
```
sshfs john@cassy: /home/john/Desktop/web
```
in this example john is my user name and cassy is the name of my server (although you can use the local ip address, probably something line 192.168.1.XXX) this command points the web folder on my desktop to the home folder on my server.

I have also found a way to automatically do this when you turn on you machine although I don't remember where the guide was or exactly how to do it...

---

### Post by jcwmoore on 2008-03-10
> okay , at the terminal, I said this: chown brian:fuse /mnt/remote

I didnt get anything in return, and right now I simply have a directory named /mnt/remote.

I think the group you are looking for is "users"... but you don't really need to worry about this step, see above post

---

### Post by shredfitz on 2008-03-10
> **jcwmoore said:**
> because of what I wanted to do I differed a little from this tutorial... I think you are safe to ignore the group name part for the folder in /mnt

so from where you are I did this...
I created a new folder on my desktop called "web"
I ran this command from the tutorial...
```
adduser [your-user] fuse
```
I then ran this command to mount the server folder
```
sshfs john@cassy: /home/john/Desktop/web
```
in this example john is my user name and cassy is the name of my server (although you can use the local ip address, probably something line 192.168.1.XXX) this command points the web folder on my desktop to the home folder on my server.

I have also found a way to automatically do this when you turn on you machine although I don't remember where the guide was or exactly how to do it...



This is where I'm at:

brian@bamco-mini:~$ sshfs brian@192.168.2.3: /home/brian/Desktop/web
brian@192.168.2.3's password: 
fuse: failed to exec fusermount: Permission denie

---

### Post by jcwmoore on 2008-03-10
[http://ubuntuforums.org/showthread.php?t=103860]("http://ubuntuforums.org/showthread.php?t=103860")

look at the 9th post in this thread

NEVER MIND.... look below

---

### Post by jcwmoore on 2008-03-10
AH!

ok you need to log in and log out, look in that post [http://ubuntuforums.org/showthread.php?t=103860]("http://ubuntuforums.org/showthread.php?t=103860")

at the 3rd step... I remember doing this when I first set everything up, but it is not included in the guide i gave you....:oops:

so if you are in the fuse group, log out and log back in and then try it...

---

### Post by shredfitz on 2008-03-10
how exactly should I log out? Unfortunately that post you referred me to is not making any sense to me.

---

### Post by shredfitz on 2008-03-10
ok- did this:

brian@bamco-mini:~$ sudo chmod +x /usr/bin/fusermount
brian@bamco-mini:~$ sshfs brian@192.168.2.3: /home/brian/Desktop/web
brian@192.168.2.3's password: 
fusermount: failed to open /dev/fuse: Permission denied


still no luck

---

### Post by jcwmoore on 2008-03-10
same way you shut down... if it is easier you can reboot, it accomplishes the same thing.

To log out, click on the shut down icon (in the top right of the screen by default)
and click on the log out icon...

[http://www.manucornet.net/ubuntu/dev/logout.png]("http://www.manucornet.net/ubuntu/dev/logout.png")

---

### Post by shredfitz on 2008-03-10
okay, logged out and back in and did the following, still no bueno:

brian@bamco-mini:~$ sshfs brian@192.168.2.3: /home/brian/Desktop/web
brian@192.168.2.3's password: 
fusermount: user has no write access to mountpoint /home/brian/Desktop/web
brian@bamco-mini:~$ sudo sshfs brian@192.168.2.3: /home/brian/Desktop/web
Password:
Sorry, try again.
Password:
The authenticity of host '192.168.2.3 (192.168.2.3)' can't be established.
RSA key fingerprint is 48:17:b9:0d:5f:e0:62:1e:bd:01:d8:4d:44:3d:0e:23.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
brian@192.168.2.3's password: 
brian@bamco-mini:~$ sudo sshfs brian@192.168.2.3: /home/brian/Desktop
brian@192.168.2.3's password: 
fusermount: mountpoint is not empty
fusermount: if you are sure this is safe, use the 'nonempty' mount option
brian@bamco-mini:~$

---

### Post by jcwmoore on 2008-03-10
sshfs by default will only mount to an empty directory and based on your output there is something in that folder, make sure that folder is empty hit CTRL H to see any hidden files

---

