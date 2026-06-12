---
title: "How do I create a Folder?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by babel on 2006-04-26
This is the first time I have posted to this forum from Ubuntu instead of from Windows (I installed Ubuntu last weekend).

I am trying to create a folder to put documents into.  I pasted some information to an OpenOffice page.  I then used Nautilus 2.12.1 to open "File System".  When I tried to create a new folder in File System to keep my documents in, the option for  Unfortunately the right-click option to "Create Folder" is "greyed out".  I could only save the document in an existing folder.  The default location for it to go to is a folder called "Home" which contains a folder within it with my log-inb name.  So I saved it there.

How can I create a folder for any purpose within "File System"?  Why is the option to "Create Folder" greyed out?

I am trying to slowly make this system functional for me.

It's a slow process!

Thanks.

babel .

---

### Post by mjm115 on 2006-04-26
The file system folder (/) is the default root of the drive, kind of like the C:\ on windows.  By default, only the root user (in Windows the administrator) can alter this folder.  The home directory (My Documents) is set up so that you can place your documents in this folder.  You have both read and write access to your home folder.  You only have read access to the other folders as a regular user.  This is why you could not create a folder.  I'm sure if you did it in the home directory, the option would not be greyed out.

For more information about the way the file system is set up, please check [this]("https://wiki.ubuntu.com/LinuxFilesystemTreeOverview") out.

---

### Post by duality on 2006-04-26
you use "mkdir" command to create a folder.
example:
  sudo mkdir <foldername>
 or
  sudo mkdir /home/<foldername>        (to create a folder in the "home" directory)

--------------------------------------------------------------------------------
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
look here for more information on how to do stuff in ubuntu.

---

### Post by engla on 2006-04-26
Hello!

Creating folders should be easy of course, but I understand the usability issue here.

The thing that's not obvious is that you are not *allowed* to make folders anywhere (or modify files). Of course you can if you really want to, but the way the linux system is laid out and "protected" (proctecting the system from users, say, removing a crucial file), you can't create a folder at the "root" of the file system.

The thing is really easy when you get hold of it:** Your stuff goes in your home folde**r. You can do whatevery you want inside it and you will find that you don't need the file manager for other things than browsing your home folder (and perhaps some cds and so)

---

### Post by Bloch on 2006-04-26
Hi Babel;
In linux the user cannot change or delete any system files or directories. This makes the system more secure.

Only the "superuser" also known as "root" or "administrator" can change or delete system files. Did you install ubuntu yourself? You should take note of your user name, user password and root password.

Now to answer your question, EVERYWHERE is a system directory, except your home directory. Only in your home directory can you create directories and add files. The "filesystem" directory is the top directory of them all, and you will see bin, root, dev, etc, usr, and in among them home. in home directory there will be a directory for each user - presumably only one user. You know the way directoriy paths are written in linux? My home directory is /home/me   because I used the username me when installing ubuntu.

---

### Post by AdventChildren on 2006-04-26
May I know how to login as root since I no know what the root password is :o ?

---

### Post by delta32 on 2006-04-26
[QUOTE=AdventChildren]May I know how to login as root since I no know what the root password is :o ?[/QUOTE]
If you must, use "sudo passwd" to change the root password. You can then use su to become root. It's not recommended that you run as root all of the time though, because there is more of a chance you could mess something up.

---

### Post by duality on 2006-04-26
open a terminal and type "man sudo" and "man su"  and read that,, it explains some of the stuff about root and superuser.

you become root by typing "sudo su" and then password,, in terminal.

---

### Post by babel on 2006-04-27
OK - let me se if I understand this.

Unless I log in as Administrator, I can only create a folder in the Home folder.

(1) Should I add folders in the "Home" folder itself or in the folder within "Home" that contains my log-in name ?

(2) Not that I plan on doing it (as there seems to a good reason to leave the protections in place), but how would I log in as "Root" if I wanted to ?  When I installed Ubuntu onto this computer I created only one Username and one Password. I didn't see any place to create a "Root" password, but I certainly could have missed it. Maybe it's the same as my regular password, as I installed the Ubuntu myself and there are no other users.

Do I log out then log back in with "sudo passwd" ?

How do I "use su to become root" ?

(3)  Many of you kind enough to respond to me have mentioned certain commands that I can enter.  I really am an absolute beginner.  How/where do I enter a command ?

(4)  If I install a program (haven't tried this yet) does it also go into "Home" or will it create its own folder in "root" ?

I know it's a lot of questions but I am trying to learn how to do one thing in Ubuntu every week.

---

### Post by babel on 2006-04-27
mjm115**:**   Thanks for the link to "Ubuntu GNU/Linux Filesystem Tree Overview" !

---

### Post by malavar on 2006-04-27
[http://www.unix.org.ua/orelly/unix/lrnunix/index.htm](http://www.unix.org.ua/orelly/unix/lrnunix/index.htm) 
read that babel, it will give you an introduction to unix. these forums will help you, but are no substitute for actually reading books on this subject. 

p.s i really hope you enjoy your new linux system

---

### Post by Sarisar on 2006-04-27
Just remember.  If you think it's hard for YOU to make a directory on here how hard will it be for all the spamware that is expecting a windows machine with full admin rights!

Plus windows also does funny things with certain directories anyway (like the system restore ones that even AS admin you don't have rights to!)

This is the best way of doing it.  Although I cheat and created a new menu item for a 'root file manager' to steal the windows phrase by setting the new menu item to run 'sudo nautilus'.  I know this is REALLY bad as you can make your computer unbootable, but sometimes it's easier to run that (enter password) and then create any directories or move files over that way then using command prompts.

And I don't think anyone said but the sudo password is just YOUR password by default (you can probably change it - I'm still an Ubuntu noob myself :)

---

### Post by steve.horsley on 2006-04-28
You must put your stuff in **your** home folder, /home/babel. Other users put their stuff in their home folders. As normal users, they can't put stuff anywhere except in their home folders. There is one exception - anyone can use /tmp. 

I keep all my stuff in /home/steve, and my wife and kid can't even see my stuff, let alone mess with it. I like it that way. I'm fed up with my kid messing up my UT2004 settings on windows. On Ububtu, we have our own settings.

User root can do anything of course. But you can't log in as root. You have to use sudo to temporarily gain root privilege.

---

### Post by soc on 2006-04-28
just to make it clear:
in ubuntu the root account is completely disabled!
if you need root-privileges you can use sudo.
but _please_ don't enable the root account by giving it a new password!!!
it's the worst thing you can do, because ubuntu was set up to use sudo for every administrative tasks!
there is absolutely no point where you should use a root-account for anything!
just use sudo for these things, because it is
- more secure
- convenient to use
- able do everything you could do with root
if somebody tells you to do su or sudo passwd, just ignore it.
there are other distributions which work like this, but surely ubuntu doesn't belong to them!

---

### Post by gr0kzer0 on 2006-04-28
I agree that there's no point in enabling root login. When I started with Ubuntu, it annoyed me that I couldn't log in as root on my own computer. So I set root's password myself. Since then, I don't think I've _ever_ had to log in as root. Sudo is perfectly sufficient. You give a command, eg.

sudo nano /etc/crapfile

type in your password, and get on with it. If you need to do a few tasks that require superuser privileges, you don't need to type in your password every time you use sudo - it seems to remain "active" for some period of time, during which you just need to type in sudo+command. So, even though I _can_ log in as root... I never need to.

Oh, I'm not sure if anyone answered this question for you yet. Youtype commands in a terminal. The terminal can be reached through the menu, Applications > Accessories > Terminal. Or (my favorite) you can press Ctrl+Alt+F1, which will bring you to a new shell in a terminal. In fact, you can press Ctrl+Alt+F2, or F3, all the way to F6, and get new shells. This means you have access to 6 shells plus Gnome (which you get to with Ctrl+Alt+F7) - you can be logged in 7 times simultaneously, all with the same username if you like.

---

### Post by babel on 2006-04-28
Thanks, everyone !

Although I'm not sure I understand how to use Administrator rights, I understand that I probably should not try to.  I am much too new at Linux & Ubuntu to risk causing damage to my system.

Special thanks to **gr0kzer0** for explaining to me something I've been wondering about, that is, where to find the command line.

---

### Post by Bif Powell on 2007-07-27
First post here (it is prefered to ressurect old threads than to create new ones, yes? - Apologies if this is a faux pas here). 

I have 4 drives that I used for various storage when I was using Windows (switched on Wednesday).  I have the biggest and most important of these currently hooked up and I can read/view/listen to the files there, but I don't have any write/delete/create folder permissions.  As it's not on the drive with my /home the fixes and descriptions don't apply up to this point.  This drive also has folders which will ultimately be shared on my network and accessible to other family members to view and add content (pictures, music, movies, etc...) which I know is an issue for a different thread (SMB).  Am I at the point now where I need to create groups (wife with rwx - kids with rx) and so on, or should I be doing something else (reading about Linux security)?

In the short-term I would just like to be able to add folders and files to get them off my cameras rip some CDs into there and some time in the future really get my act together on permissions.

---

