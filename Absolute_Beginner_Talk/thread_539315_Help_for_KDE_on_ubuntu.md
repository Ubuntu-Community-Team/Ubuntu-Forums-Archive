---
title: "Help for KDE on ubuntu"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by apparle on 2007-08-31
I would like to know how to install KDE on ubuntu without removing GNOME.
I use Ubuntu Feisty Fawn 7.04 .
[COLOR="Red"]***I donot have internet on my computer. I use net in my college***[/COLOR]

Also I am an beginner to linux (Have been using it only a week).
Please tell me if any direct package is available

---

### Post by apparle on 2007-08-31
Anothere question is it possible to install kde on ubuntu with the help of kubuntu CD

---

### Post by xaco1234 on 2007-08-31
iif you had internett you woud just do sudo apt-get install kubuntu-desktop if i'm not very wrong

---

### Post by wieman01 on 2007-08-31
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
That should work after putting in the disk.

---

### Post by apparle on 2007-09-04
Thanks man
I have requested for shipping of kubuntu CD I will see if it works

---

### Post by wieman01 on 2007-09-04
> **apparle said:**
> Thanks man
I have requested for shipping of kubuntu CD I will see if it works
Alternatively install KDE-Core from the Ubuntu CD:
> sudo apt-cdrom add
sudo aptitude update
sudo apt-get install kde-core xorg kdm
sudo /etc/init.d/kdm restart
No need to wait for the Kubuntu Live CD. :-)

---

### Post by apparle on 2007-09-04
But are you sure it will not ask for net connection

---

### Post by apparle on 2007-09-04
These commands? What do the actually do

---

### Post by wieman01 on 2007-09-04
> **apparle said:**
> But are you sure it will not ask for net connection
Not with "sudo apt-cdrom add" in front of it. Try it out, it won't do any harm. You can remove KDE later on.

---

### Post by apparle on 2007-09-04
I will give it a try when I go home and how to switch desktops
On a site
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
 it said use these commands it will be better
*sudo aptitude update && sudo aptitude install kubuntu-desktop*
for installation and
*sudo aptitude remove kubuntu-desktop*
for removal 

Off course from internet

---

### Post by apparle on 2007-09-04
How to install KDE on Ubuntu
Ubuntu's default desktop environment is Gnome. Sometimes people using Ubuntu want to try out KDE as well, though. 

Warning: having KDE and Gnome together means you'll have cluttered application menus full of KDE applications and Gnome applications. You may also run into some other cosmetic problems (the KDE QT look taking over some of your Gnome themes, a hidden file on your desktop that keeps appearing in Gnome after you've just logged out of KDE). One of the most common problems is the new desktop environment "taking over" the boot splash screen. Here are some instructions to fix that problem. 

Even though these instructions are for KDE, the same principle applies for adding Gnome to Kubuntu or XFCE to Kubuntu or Ubuntu. Basically, you install the desktop environment, log out, and choose the desktop environment. 

Note: Some people may tell you to install KDE using Synaptic Package Manager or apt-get. Using aptitude instead will make KDE easier to remove later if you wish to do so. 

Paste this command in the terminal:


sudo aptitude update && sudo aptitude install kubuntu-desktop
 
During the installation process, you should be asked whether you want to use KDM or GDM as your default display manager. If you think you'll use KDE more frequently, make KDM your default. If you think you'll use Gnome more frequently, keep GDM as your default. 

The default can always be changed later by modifying the /etc/X11/default-display-manager file. For KDM, the file should read /usr/bin/kdm; for GDM, the file should read /usr/sbin/gdm 

 
When KDE is done installing, log out. 

 
If you're using Dapper, Edgy, or Feisty, once you get to the login screen, click on Options and then Select Session. 

In older versions of Ubuntu (Breezy, Hoary, Warty), you would have a separate Session button instead of drilling down to Session from Options. 

 
In the Sessions dialogue, select KDE and then Change Session. 

 
Finally, before you log back in again, decide whether you want to change to KDE just for this session or if you want to make KDE your default desktop environment. 

Then, log back in, and you should be using KDE. 

To switch back to Gnome, just log out and select Gnome from the session menu. 

If you later decide you don't want KDE any more, go back to the terminal and paste in 

sudo aptitude remove kubuntu-desktop. 

Page updated 08/30/2007 

***_[COLOR="Red"]THis info was on the site[/COLOR]_***



Site : [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by wieman01 on 2007-09-04
Yes, follow Psychocat's (Aysiu's) tutorial, that's definitely a safe bet. :-)

---

### Post by apparle on 2007-09-04
What do u mean 
Should I add "sudo apt-cdrom add" before their command

---

### Post by Happy_Man on 2007-09-04
If you don't have internet, then yes, you will need to wait for a CD and then use it to install, using "sudo apt-cdrom add" before following aysiu's tutorial.

---

### Post by wieman01 on 2007-09-04
> **apparle said:**
> What do u mean 
Should I add "sudo apt-cdrom add" before their command
Installing from CD, you should do that. Yes.

---

### Post by apparle on 2007-09-04
Somebody says wait for CD other says use ubuntu CD???????????



What should I do

---

### Post by Happy_Man on 2007-09-04
I suggest to wait for the Kubuntu CD, it will have more packages you can use than the Ubuntu CD.

---

### Post by wieman01 on 2007-09-04
> **Happy_Man said:**
> I suggest to wait for the Kubuntu CD, it will have more packages you can use than the Ubuntu CD.
I agree. Do exactly that. Fullstop.

---

### Post by apparle on 2007-09-04
When the Cd comes should I install fresh Kubuntu or use ur commands on ubuntu

---

### Post by apparle on 2007-09-04
Thanks Guys. I am really grateful for all this info

---

### Post by wieman01 on 2007-09-04
> **apparle said:**
> When the Cd comes should I install fresh Kubuntu or use ur commands on ubuntu
Entirely up to you. If you can afford a fresh install and don't want to keep Gnome, then go ahead. But if you want both DEs, then do it as described... no fresh install in that case.

---

### Post by apparle on 2007-10-08
the method u told is not working. cannot install KDE from kubuntu Cd on ubuntu

---

