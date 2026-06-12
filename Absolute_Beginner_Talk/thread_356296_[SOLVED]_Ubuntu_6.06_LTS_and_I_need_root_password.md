---
title: "[SOLVED] Ubuntu 6.06 LTS and I need root password"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by L a r r y on 2007-02-08
Hello,
I have installed Ubuntu 6.06 LTS on my secondary hard drive, and was successfully logged in as user "me" with a password.  Because I have a Winmodem that Linux did not recognize, I have to use Windows XP to use the Internet, and probably to use my Canon BJC 2110 printer.

When I installed Ubuntu on my secondary 80 gig hard drive, I made 3 partitions, an extended 3 file system for Ubuntu and fat32 for sharing between Windows and Linux.  And of course the Linux Swap.

During the install procedure there was no place where I was asked to set up a Root password.

I downloaded Abiword for Linux while in Windows and saved it in my fat32 partition.  Rebooted into Linux and could not install the software because I do not have permission.  The downloaded file belongs to root.

I also wanted to edit my boot menu.  That too requires that I log in as root.

**So my question is, where to from here?  I need to use a password I don't know.**

I reinstalled Ubuntu and specified my user id as "root."  I set a password, but when I rebooted, I tried to sign in.  I cannot log in as root on this screen.  So I need to re install as I was to begin with and seek answers.

Thank you in advance.
Larry

---

### Post by Stemp on 2007-02-08
Ubuntu doesn't use root.
Check [Sudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by tbroderick on 2007-02-08
The password you entered for your user is the "root" password. You just need to use sudo or gksu for GUI programs.

---

### Post by dannyboy79 on 2007-02-08
> **tbroderick said:**
> The password you entered for your user is the "root" password. You just need to use sudo or gksu for GUI programs.


NOT TRUE. There is NO root password in Ubuntu be default. The password you set up during the install was YOUR password. If you want one, you need to do sudo passwd root. Then you enter YOUR password first, then you enter the ROOT password that you desire twice. I beleive this is how it works. Ubuntu doesn't make a ROOT password because they disables the ROOT account from ever logging in from the login screen. You can enable it but I wouldn't suggest to. So, when you need to do a lot of commands as root, you can do sudo -i, then enter YOUR password. now you are user ROOT so be careful. If you really want to be able to log in as root, then do what I suggest at the top and there is somewhere in the users and groups gui that you can enable ROOT to login. good luck.

---

### Post by jvc26 on 2007-02-08
You can just surely use sudo or gksudo as the prefix to the command you re tying and then put in your password at the prompt.
Il

---

### Post by finer recliner on 2007-02-08
'sudo -i' opens a root shell using your own password. please use this only as a last resort. as mentioned above, use sudo first.

---

### Post by tbroderick on 2007-02-08
> **dannyboy79 said:**
> NOT TRUE. There is NO root password in Ubuntu be default.

I'm talking about sudo or gksu which is "root" access. But thanks.

---

### Post by dannyboy79 on 2007-02-08
> **tbroderick said:**
> I'm talking about sudo or gksu which is "root" access. But thanks.

That sounds better. Sudo and gksudo give you root privalages for that command only, depending on whether the user has changed the amount of time that the password you entered to gain root privalages is active for. For example: a person could enter sudo cat /etc/apt/sources.list and enter HIS password, look at the output and then do sudo cat /etc/fstab and not have to enter HIS password again because Ubuntu default I think is 5 mins. Someone correct me here if I am wrong.

You can easily mess up a newbie by mischosing your phrases and comments. Your first statement of, "The password you entered for your user is the "root" password" is not true at all any which way you look at it. So I merely wanted to point this out. You have to realize that other distros use the root account and not sudo so it's paramount that this is pointed out.

---

### Post by Brunellus on 2007-02-08
the definitive explanation for all this is at

[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

Abiword is easily installable through synaptic or aptitude.  No need to go to the website.  For general help on how to install software on Ubuntu--and why we do the things we do, see

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by L a r r y on 2007-02-08
Thanks for all the tips.  you have pointed me to the place in the documentation where I need to read and apply what I have read.  I saved the page to my computer on RootSudo so I can view it while I am in Linux.

I have years of experience in MS-DOS and Windows 3.1, 3.11, 95, 98, me, 2000 and xp, and before that Radio Shack Color Computer 2 and 3.

I saw where I can even run Windows from Ubuntu, something to look at way down the road.

I will follow up with another post with my progress.  Thanks again.
Larry

---

### Post by L a r r y on 2008-06-01
I just wanted to add a word of thanks to all who partook of this thread discussion.  There was a time when I had no Internet access in Ubuntu, so I could not take advantage of the excellent ways devised for upgrades and add-remove programs.  Now that I have a DSL connection, I re-installed my Ubuntu 6.06 from the live CD, and promptly found an opportunity to upgrade to 8.04.

Add-Remove programs is a breeze -- Run the utility and it displays all of the programs I have and all the programs I can get, uncheck the ones I want to remove, check the ones I want to install and follow through.

When I make a change to my system, I am prompted to enter my sign-on password to gain administrative privileges for the duration of the work.  I can run a command prefaced with gksu whenever I need to change something owned by root.

I have, for instance added the hosts file entries from [www.mvps.org](www.mvps.org), appending the advertising restrictions to the end of my hosts file in /etc/hosts.  In order to make the change, I had to run [COLOR="DarkRed"]**gksu gedit /etc/hosts**[/COLOR].  That asked me for my password, and then launched the text editor with permission to save changes to the file.

It is a bit late, but I have marked the thread as Solved.

Kind regards,
Larry

---

