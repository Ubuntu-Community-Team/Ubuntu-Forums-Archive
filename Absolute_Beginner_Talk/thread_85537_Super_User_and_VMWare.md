---
title: "Super User and VMWare"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by rhpt on 2005-11-02
I installed Ubuntu on my Windows machine via VMWare, and I am trying to install the "VMWare Tools". However, Ubuntu keeps telling me that I should log on as a "super user". Can someone please tell me how to create a super user account or change my account to have those privileges?
 
Thank you

---

### Post by dbott67 on 2005-11-02
Open a terminal and type 'sudo' in front of the command you wish to execute.  You will be prompted to enter your password to switch to 'super user' mode.

-Dave

---

### Post by Donnut on 2005-11-02
If you need to log in as "super user" you simply log in as "root".  This link has all info on that.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by GreyFox503 on 2005-11-03
A default Ubuntu install disables the root account.  Normally, to execute a command w/ root privileges, you use sudo before the command.

If you want to enable root access, you use:

```
sudo passwd root
``` 

This will prompt you for a password.  You will be setting the password for the root account.  Then you can use su anytime to change to root.

If you want to log into GNOME as root (not recommended, but you can) then first go to System > Administration > Login Screen Setup > Security.  Then check "Allow root to login with GDM".  This will allow you to log in as root from the GNOME login screen.

---

### Post by Perfect Storm on 2005-11-03
[QUOTE=Donnut]If you need to log in as "super user" you simply log in as "root".  This link has all info on that.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)[/QUOTE]

Not a good idea. I rephrase that: It's a very bad Idea. 

The simplest way without sacrifing security is to do if it want su and not sudo
```

sudo su

```

---

### Post by patrick295767 on 2005-11-03
[QUOTE=Artificial Intelligence]Not a good idea. I rephrase that: It's a very bad Idea. 

The simplest way without sacrifing security is to do if it want su and not sudo
```

sudo su

```[/QUOTE]
  
If I recall well, there is an option (at least working for last version of vmware) as: 
vmware -superuser 
  or sthg like that ... or vmware -super user... 
     
Is there someone that has the right command line ... ??
 
Pat'

---

### Post by rhpt on 2005-11-03
Thank you for all the help. sudo worked like a charm!

---

### Post by Donnut on 2005-11-03
[QUOTE=patrick295767]If I recall well, there is an option (at least working for last version of vmware) as: 
vmware -superuser 
  or sthg like that ... or vmware -super user... 
     
Is there someone that has the right command line ... ??
 
Pat'[/QUOTE]

Is this a Bad Idea?  Some programs require you to do this...

---

### Post by rhpt on 2005-11-03
I notice that there are certain folders to which I cannot copy files. For example, I want to edit my Firefox prefs, but Ubuntu will not allow me to make changes to the \etc\mozilla-firefox folder. How can I give my user "root" privileges? Using the instructions given above, I still cannot logon as the root user.

---

### Post by mlomker on 2005-11-03
> Using the instructions given above, I still cannot logon as the root user.

You're not supposed to in Ubuntu.  If you want to run firefox with sudo permissions then type **sudo firefox** in a terminal and it'll open that one application with root permissions.  If you want a command prompt as root then you just type **sudo bash** and you'll have one.

---

### Post by patrick295767 on 2005-11-03
[QUOTE=Donnut]Is this a Bad Idea?  Some programs require you to do this...[/QUOTE]
  
Just I recall that when I was student, at school, we had absolutely no rights on PC ...
the only way to skip the admin installations and obligation was to run the windows onto linux ...
  
I had no rights at all, just user : 
 and i was doing : 
vmware -super user ... 
stuff like that from the xterm
  
No rights absolutely and that helped me more than a lot !! 
  
I dont know more about last versions of vmware ..
its now 5 years ago ...long time 

Kind regards

Patrick

---

### Post by GreyFox503 on 2005-11-04
[quote=rhpt]I notice that there are certain folders to which I cannot copy files. For example, I want to edit my Firefox prefs, but Ubuntu will not allow me to make changes to the \etc\mozilla-firefox folder. How can I give my user "root" privileges? Using the instructions given above, I still cannot logon as the root user.[/quote] 

If its at the terminal, sudo should work for you again.  However, if you want to do this graphically, you can run:

```
gksudo nautilus
``` 
or in KDE:

```
gksudo konqueror
``` 
This should prompt you for a password and then open up the file manager.  The new windows will have been opened as root, so it should let you do anything root can do.  Be careful with it.

---

### Post by LHZ on 2005-11-04
[QUOTE=rhpt]I notice that there are certain folders to which I cannot copy files. For example, I want to edit my Firefox prefs, but Ubuntu will not allow me to make changes to the \etc\mozilla-firefox folder. How can I give my user "root" privileges? Using the instructions given above, I still cannot logon as the root user.[/QUOTE]
Just for the record, what would you like to change in \etc\mozilla-firefox ? You can change all you preferences through Edit->Preferences in Firefox itself, which has zero chance of messing up your system.

---

