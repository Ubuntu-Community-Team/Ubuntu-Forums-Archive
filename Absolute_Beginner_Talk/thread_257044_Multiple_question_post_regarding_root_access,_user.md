---
title: "Multiple question post regarding root access, users and Starcraft"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by powergrip on 2006-09-14
I installed Ubuntu 6.06 LTS (that I got from a local Linux club that I go to, VanLUG.) and I installed it using a general user ID name (my name). When I logged in under my name everything worked sound was working and the whole bit. I later realized that the only program I really wanted to work was Starcraft. The only way I know how is by using Wine or Win4lin.  

I have no idea how to get Wine to work or install and when I tried installing win4lin through the terminal (as it directs you to do through a manual) I was told that I needed superuser privileges.  I thought I had them but apparently not. I then tried logging in as /root but quickly realized that I couldn’t. I ended up getting frustrated and reinstalled Ubuntu as set up my primary ID as root so that I was able to manipulate my password. (it doesn’t allow you to change the password of the root user through Gnome interface due to “security” reasons.)

After I reinstalled I tried to login to gnome using the root id but was given a message that said I couldn’t log in as root. Additionally I was unable to create any other users as I was never given the option at setup nor was I allowed to access gnome using the one ID I had. I then restarted the computer and ran terminal under the “recovery mode.” From there I was able to log into root and, after hours of mixing up DOS and Linux commands, I was able to create a new user and attach him to the root GID. 

I restarted the computer and logged into the new user through Gnome. Now nothing works right nor can I find the box thing that allows me to setup new users through Gnome. I don’t have sound, I don’t think I have root permissions, and I can’t get into my flash drive that my exes, pics and docs. Now I’m at the point where it’s useless to be able to access the root user id if nothing else works in Gnome. 

SO FINALY MY QUESTION… (I put it in caps so if you wanted to skip the story you’d see it) Please help answer even one of the following…

A)	Can I in fact access the “root” user through gnome on Ubuntu 6.06 LTS
B)	[If No to “A”] Is there an Ubuntu version that will allow it? 
C)	[If Yes to “B”] Can you direct me to the URL?
D)	How do I access the Gnome GUI for setting up accounts through terminal or other?
E)	How does your primary account (not root) get superuser privileges in the Gnome GUI Terminal?
F)	Is there any easier way to install Starcraft? 
G)	[If Yes to “E”] URL or instructions please? *beg*
H)	Is there a way that I can create users in the recovery mode of Ubuntu that when I log in to Gnome I have full usage of the GUI and its perks? (When creating new users through Gnome there isn’t an issue but initially I don’t have the option to create the users when I can’t log into Gnome.)
I)	Is there a way I can create multiple user IDs through, during or before installation?

Thank you everyone for your help, I really and truly appreciate any help you can give on helping this total newb learn the wonders of Linux. :D

---

### Post by snapcase16 on 2006-09-14
To temporarly obtain root privileges, one must enter 'sudo' before a command in the terminal.

---

### Post by TheMono on 2006-09-14
I'd suggest reinstalling again after what you did with creating root as your main identity lol.

After that,

A) Yes, you can.

Simply prefix any command you type into the terminal with "sudo", ie, "sudo make install"

It will then prompt you for a password - you enter your own password, nothing to do with any other root password. It will then execute your command as the super user (root effectively).

Further, in the system menu, you will find that if you launch any of the config tools, ie, "users and groups" to do what you wanted there, it will automatically ask for your password and execute that admin program as the super user.

---

### Post by powergrip on 2006-09-14
Well that explains a lot. I can't believe 4 letters could have saved me so much greif. I literaly spent 2 days trying to get this to work. On a brighter side I'm really starting to get use to the Linux Terminal commands. LOL. Thanks again :)

---

### Post by Skia_42 on 2006-09-14
Another usefull option is "sudo -s". It permantly enables the superuser for the session.

---

