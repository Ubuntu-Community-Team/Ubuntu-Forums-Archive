---
title: "Gutsy File sharing: Vista"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by peaceforall on 2007-11-17
I have two computers: How to I read/write files from my vista computer to my gutsy computer and visa versa.

---

### Post by jaybombalous on 2007-11-17
U need a how-to on samba and file sharing.



[www.google.com](www.google.com) I would use search words like samba, file sharing, vista, gutsy ubuntu


U will have a enough to read through I am sure. The more u read the better u will be prepared for the problems that can arise. There is a few threads on these forums. search here first.

---

### Post by peaceforall on 2007-11-17
Thank you.  I can now see my ubu machine (icon) on my in my vista network browser.  When I click on it I get "windows cannot access\\ubunut".  All I want to do is share one folder.  Seems like this should be an easy setup vs. me having to read 40 pages and do terminal programming too?

---

### Post by torgrot on 2007-11-17
I wouldn't bother.  I have spent literally days trying to get my vista and XP machines to share files.  I have had assistance from several microsoft mvps etc...  And my conclusion is that it is always hit or miss.  They made significant changes to the way Vista shares files.  A good starting point is make sure both computers have user accounts with matching usernames and passwords.  I was never able to get anywhere until I did that.  In my opinion, with Vista you are back to sneakernet.

torgrot

---

### Post by peaceforall on 2007-11-17
Torgrot,  I looks like you are referring to sharing files between 2x windows machines?  I need help linking to a ubu folder from my vista machine so i can trade files back and forth. The goal is become ms windows free soon.

---

### Post by torgrot on 2007-11-17
That is correct, but the problem lies in the Vista machine.  They changed some of the security settings for Vista and it just doesn't play nice unless you are logged into a domain.  You may be able to do it from Vista to Ubuntu, but I am almost certain opening a shared folder, if you can even see it from Ubuntu, you will not be able to access the files.

torgrot

---

### Post by zkeng on 2007-11-17
I have no trouble sharing files btw gutsy and win. I have a machine with vista and gutsy and one with xp. Daily use a shared folder, either from gutsy or from vista and access it from the xp machine.

In Vista right click your network icon in the system tray (at the very right on your start menu panel) and start the network and sharing center. In there make sure you enable network discovery (so you are visible on networks) and then if you are planning to share files from vista enable folder sharing and make sure you have the password protected sharing on (think it is by default).
Now go to My Computer or Computer as I think the bright guys at Microsoft finally realized they could call it, right click anywhere on the white space in the explorer windows and go to properties or computer settings or whatever it is called. In there set the workgroup for your computer to the desired name. You must set the same workgroup in windows and linux-samba.

Oka doka, now we can finally leave vista and fire up your ubuntu computer instead.

Go to: System/Administaration/Shared Folders

Create a new shared folder with the following settings::

Share with: SMB
Name: anyname
Comment: anycomment
Uncheck "Read only"
Check "Allow browsing folder"

In General Windows sharing settings

Host description: anydescription
Domain/Workgroup: XXXX  Important same as your windows workgroup!
Allow ubuntu to install samba packages if asked to.

Fire up the terminal. It is time to create a user account for your samba server. In terminal::

sudo smbpasswd -a anyusername

(and type the password for anyusername when asked)

Now you have created a user account to login to your shared folder over the network. If you want to remove a samba account exchange  "-a" for "-x" in the above line.

Now in terminal write:

gksudo gedit /etc/samba/smbusers

In the text editor copy and paste exactly the line below (username should be username and not any desired username):

system_username = network username

Save and exit the text editor.

Now reboot (probably no need but anyway) computers, make sure you plug them in to the same network. Find your work group and the other computer should be there. Now with the right username and password any computer on the network in your workgroup shold be able to use the shared folder on the ubuntu computer (since we set up samba as a server). But to login to a shared folder on the vista box two things must be true:
1. In vista a user account must exist with the same username and password you use in ubuntu.
2 There must be at least one folder shared that the ubuntu username has the permission to access.

Hope this gets you going....
Time to put on the yellow and blue shirt and watch Sweden cruss Spain again in the Football Euro qualifiers...
Chers

---

### Post by peaceforall on 2007-11-17
zkeng,  Thank I'm following you except for:

system_username = network username

I have a username I used to log into ubu now, lets say it is "X"

Do I type  system_x =  network x      

Or do make up whole new password?

---

### Post by peaceforall on 2007-11-17
Meant so say to I set up whole new username

---

### Post by peaceforall on 2007-11-17
Any UBU geek out there who can help me with a rather the simple problem noted above. After 4 hours of browsing I'm finding no help for this one?

---

### Post by inzi2u on 2007-11-25
The solution that zkeng mentioned actually worked for me.. 

but..

you still have to assign a username and password.. for the people who are wishing to enter your shared folder..

I am a noob at this too.. so i am still trying to figure it out aswell..

i know this thread is about a week old.. so.. hope this helps..

I am using Ubuntu 7.1

---

### Post by Lvcoyote on 2007-12-09
Maybe you could provide a step by step as to what you did?? Or just copy the method from the previous post and change it to include what you did??

---

### Post by robertsaron on 2007-12-13
Zkeng

the steps you mentioned above I am sure are quite helpful. However when i was on edgy, and fiesty, I never have had to do a username and password. My room mate is on gutsy and can see the windows xp pro box with out having to type in a username/password. It worked with out going through all of this.

For a home network I think its silly to have to do so, unless your are paranoid about security. What I want to do is have a network share, all my dvds ripped out to one box, so every one in the house can see them across the network. 

samba/nfs should work out of the box with out having to go through all of this. Your average user (like myself) switching to linux does not have skills to do all of this.

There has to be a simpler better way, if anyone has it then that would be great. On my desktop I am running gutsy and cannot see my windows xp pro box. any ideas how to fix it? when after installing samba on her gutsy laptop my room mate can?

---

### Post by nooozeguy on 2008-02-05
This is a great guide!!

I have been trying to share files between my laptop running Vista and my desktop running Ubuntu for weeks--with no success.

I can now see Ubuntu files on my laptop, but when I try to copy or move files from my Windows laptop to my Linux PC, I get an error on the Vista machine that says, "you need permission to perform this action".

I have not been able to find a solution to this problem. Does anyone have any suggestions?

As background, on the Vista machine, I have:

* user accounts disabled
* the same user name and password for Windows and Linux
* file sharing is turned on
* I am sharing the folders in question

Thanks!!

-Josh

---

