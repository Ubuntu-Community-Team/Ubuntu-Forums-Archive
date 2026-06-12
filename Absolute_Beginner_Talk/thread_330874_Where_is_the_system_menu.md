---
title: "Where is the system menu?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by RoboAlex on 2007-01-03
Hi,

I am completely new to ubuntu, but although I consider myself very tech savvy, try as I might I cannot find the system menu.  I am using xubuntu but I have installed KDE also, I thought the settings menu under applications was the equivalent of the system menu but I could not find any of the things I wanted to change (remove a bad session, customize the logout menu, add users, etc)

Thanks ahead of time
-alex

---

### Post by Dmole on 2007-01-03
right click on a 'bar' and 'add new item'  from the list 'xfce menu'

---

### Post by RoboAlex on 2007-01-03
Thanks for the quick response Dmole.
I already have a Xfce menu (although it is labeled applications) but I dont understand how to do things such as (this is take from another thread):

Go under System > Prefrences > Power Management and click on the "General" tab. Now, where is says "Sleep button action" select standby. Check under System and click "Quit." The suspend option should be there.

where is this? the Xfce menu has a system menu but it is just a list of system related applications such as automatix, thor, kconsole etc.  But I cant find things like the preferences menu that is referred to above.

Thanks ahead of time
-Alex

---

### Post by Dmole on 2007-01-03
there is a Settings menu and a System menu in the Xfce menu with the things you want.
if you do not see it then you should change what is in your Xfce menu.
there is a menu editor in Settings.
(applications)>Settings>menu editor)

you can also read this for a non gui method:
[http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/)

hope this helps more
:)

---

### Post by RoboAlex on 2007-01-03
Setting seems like the right place to look but it seems to have mostly interface related things, not much along the lines of user management, power management etc... which is what I am really looking for.  If you open the settings manager it even points out that it is to "customize your xfce desktop".  This seems like overkill but maybe I should install gnome, that way what I see more closely resembles what most people see when they use ubuntu and use that to change settings in preferences, but I hope there is just some really easy obvious thing I am missing.
Thanks,
-Alex

---

### Post by Dmole on 2007-01-03
so you don't have (applications>Settings>menu editor) ?
well you can add tools with the (applications>System>Synaptic Package Manager)
also if it's not in the menu you can run it from a Terminal just like in windows.
I'm using xUbuntu and it has all the tools you are looking for.
gtg good luck

---

### Post by RoboAlex on 2007-01-04
Yeah, I have the Settings>menu editor along with many other interface related management such as desktop, splash screen, screen saver, workspace management ect... but i'm looking for things like power management, user management etc... For example I want to configure the power management because I am using a somewhat out of date laptop (500mhz thinkpad 600x) with barely adaquete battery life (2 hours) or add another user and from what I understand all of these things can be done through this "System" menu I keep reading about but just cant find.
Thanks,
-Alex

---

### Post by RoboAlex on 2007-01-05
Alright, I installed gnome and immediately found the system menu.  Xfce and Gnome have different ideas of what goes under system, and what goes under preferences.  Also along with gnome many other programs were installed, many of them involving system management.  My problem is solved. Thanks for the help.  I have now installed all the popular ubuntu desktop environments.

For anyone who might find this thread with the same problem I have here is my solution:
Install kde and gnome and remember to look under system and settings.  To install kde or gnome type:
sudo apt-get install kde
sudo apt-get install gnome
respectively.

-Alex

---

### Post by MkfIbK7a on 2007-01-05
> To install kde or gnome type:
sudo apt-get install kde
sudo apt-get install gnome
respectively.

well actually you should do

sudo apt-get install kubuntu-desktop
(KDE)
sudo apt-get install ubuntu-desktop
(GNOME)
sudo apt-get install xubuntu-desktop
(XFCE4)

---

### Post by RoboAlex on 2007-01-12
Oh, really?  What is the difference between

sudo apt-get install gnome
sudo apt-get install ubuntu-desktop

what is the difference?  I remember reading that sudo apt-get install gnome-core installs only the DE is that what ubuntu-desktop does?  I'd just like to know what I am doing when I type fancy words into that little box :P

---

