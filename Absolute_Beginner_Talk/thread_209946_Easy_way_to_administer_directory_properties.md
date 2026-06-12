---
title: "Easy way to administer directory properties?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by nameiwantistaken on 2006-07-05
I'm being a tad driven nuts by most GUI applications requiring root access to do anything.  Much of this is caused by write problems.  How can I assign certain users to have access to certain folders graphically?

---

### Post by adwait on 2006-07-05
In KDE, open up the parent folder in Konqueror and riight click>properties and then the permissions tab. In Gnome, open up the parent folder in Nautilus and the rest should remain the same.

---

### Post by fluffington on 2006-07-05
First off, what GUI applications do you run that require root access? The only apps I need extra permissions for are VMWare (if I want to change the system-wide settings; I can run normally otherwise) and the stuff in the admin menu.

Second, you can change the group that a file or directory belongs to by right-clicking on it, going to properties, then the permissions tab, and clicking the combo box labeled "File group". If the file belongs to a group that the users happen to be a member of, then their access is determined by the group permissions (second row of checkboxes on the same tab). You might have to start Nautilus as root (ALT+F2, then type "gksu nautilus") to mess with files that you don't own or change to groups that you're not a member of. You can change your users' groups by going to System -> Administration -> Users and groups.

---

### Post by catlett on 2006-07-05
You can run any gui application as root by using gksudo before the apps name in the terminal (gksudo is "run as a different user - root"
So if you want to browse with the file manager as root enter ```
gksudo nautilus 
``` If you wanted to open a text document in the text editor as root enter ```
gksudo gedit
``` Obviously you have to enter the text documents path and name after gedit but you get the point. Enter gksudo + the apps name in the terminal and it will run as root.

---

### Post by bruenig on 2006-07-06
You can always go into the command line and do
```
chmod ### file
chmod ### -R directory
```
You can use [this](http://www.elated.com/tutorials/management/unix/permissions/) to determine what to fill those #'s in with

chmod 777 is probably the simplest, gives all permissions to everybody

---

### Post by aysiu on 2006-07-06
Changing permissions on a system folder is a quick way to end up with a broken system.

*gksudo nautilus* or *kdesu konqueror* are the way to go.

---

### Post by nameiwantistaken on 2006-07-06
Adwait, thanks but I thought I was in the Ubuntu forum not the Kubuntu forum.  In terms of what applications?  Any application that writes to disc runs into this problem.  So I need to make a group for users that I want to access a certain directory and assign the group to the users?  

The gksudo is a nice suggestion, but seems like a waste of time given that I want to launch things from the GUI.  Given that the apps will be running as root, why doesn't the desktop just launch them as this in the first place.  This is a HUGE issue.  Nobody using a desktop OS from Apple/MS could ever fathom not being able to save a file on their hard drive.  Ubuntu really should address this automatically.  Not being able to save an HTML file in my web folder or save a file in my home directory is pretty silly.  That is ignoring the fact that the naming convention of the main folders of the file system should be changed to something resembling English.  My rant for the day I guess. 

The chmod command is interesting and I have read up on it and tried it, but it didnt' really work and couldn't really make sense of it.  I'll give the user group thing a try.  Ubuntu really needs to address this though if it wasnt to be a mainstream desktop choice.

---

### Post by nameiwantistaken on 2006-07-06
I just tried the group directory thing but that doesn't seem to have worked.

---

### Post by aysiu on 2006-07-06
You should be able to save to your /home directory. If not, something is wrong.

And *gksudo nautilus* can be a graphical icon launcher or a keyboard shortcut. Use it and you'll realize quickly how it will let you make changes through the GUI.

Not being able to modify every single file on your system without taking extra steps for systemwide files is part of what makes Ubuntu more secure than Windows.

Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by nameiwantistaken on 2006-07-06
Well my RAID is mounted in /home, but not in my normal desktop user's directory under home.  I want to be able to add, edit, cut and paste files within this RAID.  Also, I want to be able to edit photographs I upload.  I also want to be able to edit/add files into my apache www directory.  Pretty normal stuff, but it seems like adding a file anywhere under linux is an ordeal unless you're root.  Any easy ways to do this?

---

### Post by fluffington on 2006-07-06
[QUOTE=nameiwantistaken]Adwait, thanks but I thought I was in the Ubuntu forum not the Kubuntu forum.[/QUOTE]

There are Kubuntu people here too (I run both at the moment, and will probably just be running Kubuntu in the near future), and running KDE on top of Ubuntu isn't terribly uncommon.

[QUOTE=nameiwantistaken]In terms of what applications?  Any application that writes to disc runs into this problem.[/QUOTE]

I'm pretty sure all of my apps write to disc at some point, and I've never needed to mess with special permissions outside of VMWare and admin stuff.

[QUOTE=nameiwantistaken]So I need to make a group for users that I want to access a certain directory and assign the group to the users?[/QUOTE]

That's it. Here's an [article](http://www.perlfect.com/articles/chmod.shtml) that explains the basics of UNIX permissions if you're interested.

[QUOTE=nameiwantistaken]The gksudo is a nice suggestion, but seems like a waste of time given that I want to launch things from the GUI.  Given that the apps will be running as root, why doesn't the desktop just launch them as this in the first place.[/QUOTE]

You can create a desktop launcher (right click on desktop -> "Create Launcher...") or change menu entries (Applications -> Accessories -> Alacarte, right-click on menu entry -> "Properties") to use gksu fairly easily.

[QUOTE=nameiwantistaken]This is a HUGE issue.  Nobody using a desktop OS from Apple/MS could ever fathom not being able to save a file on their hard drive.  Ubuntu really should address this automatically.  Not being able to save an HTML file in my web folder or save a file in my home directory is pretty silly.[/QUOTE]

By default, you have unlimited access to your home directory. If this isn't the case, then you messed up your permissions somehow. Assuming that you're talking about Apache's (or some other HTTP server's) document root by "web folder", there's one in your home direcory by default (~/public_html). If you want access to the root of the server directly from your username, simply change the owner of the directory ('tis what I did, but I'm the only user on this box) or change the group to users (or add a new group just for server admin, which is probably the "correct" way to do it).

[QUOTE=nameiwantistaken]That is ignoring the fact that the naming convention of the main folders of the file system should be changed to something resembling English.[/QUOTE]

The directory structure does resemble English:[list]
[*]/bin -> Binaries
[*]/boot -> Bootloader
[*]/dev -> Devices
[*]/etc -> Etcetera
[*]/home -> Home directories
[*]/lib -> Libraries
[*]/media -> Removable media
[*]/root -> Root's home directory
[*]/sbin -> System binaries
[*]/srv -> Services
[*]/tmp -> Temporary files
[*]/usr -> User stuff
[*]/var -> Variable data
[/list]
The abbreviated names are also a hell of a lot easier to type than anything in the Windows hierarchy (ever try typing C:\Documents and Settings\User's full name\Application Data\....? It's a pain, even with autocomplete). It's also a [well-documented standard](http://www.pathname.com/fhs/), as opposed to Windows, where everything is just kind of thrown about. I can't comment on the Mac hierarchy, as I haven't used one for an extended period of time.

[QUOTE=nameiwantistaken]My rant for the day I guess.[/QUOTE]

I didn't mean to, but it looks like you got mine in response. Feel free to poke holes in anything I said if you disagree.

[QUOTE=nameiwantistaken]The chmod command is interesting and I have read up on it and tried it, but it didnt' really work and couldn't really make sense of it.  I'll give the user group thing a try.  Ubuntu really needs to address this though if it wasnt to be a mainstream desktop choice.[/QUOTE]

In my opinion, the UNIX permissions make perfect sense, and they're a hell of a lot simpler than Windows NT permissions. Besides, the Ubuntu desktop install is set up in such a way that most people should never have to mess with the permissions on anything (I'm a power user, and I've only ever had to touch the permissions once on the four Ubuntu machines I'm running right now).

---

### Post by fluffington on 2006-07-06
[QUOTE=nameiwantistaken]Well my RAID is mounted in /home, but not in my normal desktop user's directory under home.  I want to be able to add, edit, cut and paste files within this RAID.  Also, I want to be able to edit photographs I upload.[/QUOTE]

Assuming I understand what you're saying, which is questionable, you have a setup like this:
```

/home/
   your_home_directory/
   somewhere_else/  <- the RAID
```
This is a fairly nonstandard setup (in fact, I can't recall ever seeing such a thing). You own everything in your_home_directory, which the RAID is not in, and by default, you can't mess with things that aren't yours. You you want control over the RAID, you need to unmount it, change permissions of the mount point, and mount it again. Depending on how you've been using it before, you may need to change the permissions of the stuff that's already on the RAID after doing this:
```

# assuming your RAID is /home/raid and your username is user:
sudo umount /home/raid
sudo chown user:user /home/raid
sudo mount /home/raid

# if the files on the RAID are owned by root, which they might be:
sudo chown -R user:user /home/raid
```

[QUOTE=nameiwantistaken]I also want to be able to edit/add files into my apache www directory.  Pretty normal stuff, but it seems like adding a file anywhere under linux is an ordeal unless you're root.  Any easy ways to do this?[/QUOTE]

Running a webserver is generally not considered "normal stuff". It's easy to take ownership of the document root, though:

```

#assuming username is usr and document root is /var/www
sudo chown user:user /var/www
```

Of course, a separate group permission is perferable, but this is easier if you're the only one who will be messing with it.

---

### Post by aysiu on 2006-07-06
[QUOTE=fluffington]I can't comment on the Mac hierarchy, as I haven't used one for an extended period of time.[/QUOTE] Mac has a very similar, *nix-like structure, with some subtle differences I found out when setting up *rsync* for my wife on her Powerbook.

For example, users don't live in /home. They live in /Users. And devices don't get mounted in /media or /mnt. They get mounted in /Volumes.

Interestingly enough, Mac OS X uses the exact same security model as Ubuntu--*sudo*.

---

### Post by nameiwantistaken on 2006-07-07
Yeah, the RAID is mounted in /home, but not in the folder of my desktop user as it will not be used only by one user.  It is something that is more of a global repository that will be used by all desktop users, FTP users, Apache and SAMBA.  I've read the chmod link.  It still doesn't seem clear what the nubmers do.  Does it give universal access to all users and groups?  I have tried creating a group, giving ownership of a folder to that group and associating it with the desktop user but that hasn't seemed to work.

---

### Post by fluffington on 2006-07-08
> **nameiwantistaken said:**
> Yeah, the RAID is mounted in /home, but not in the folder of my desktop user as it will not be used only by one user.  It is something that is more of a global repository that will be used by all desktop users, FTP users, Apache and SAMBA.  I've read the chmod link.  It still doesn't seem clear what the nubmers do.  Does it give universal access to all users and groups?  I have tried creating a group, giving ownership of a folder to that group and associating it with the desktop user but that hasn't seemed to work.

You probably want to make it owned by root:users (user "root", group "users"), then. All users should be part of the users group (add them if they're not) and will use the group permissions to access it.

You'll have to be a little careful to make sure that everything within the RAID also has the same group and is readable/writable by that group. You may want to look at the umask command (it determines what permissions newly-created files have). It's strangely absent from the man pages on my machine and may be on yours as well, so [here's a link](http://bama.ua.edu/cgi-bin/man-cgi?umask+1). I'm not sure how to specify the group for a new file (I always use chgrp or chown for that after it's already created).

---

### Post by catlett on 2006-07-08
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) This may help explain permissions.

The point about gksudo nautilus is that when you launch nautilus in that way you can go to whatever file or folder you want and change permissions by right-clicking on it. A menu willappear. Select properties. Then there is a permissions tab. Select it and check off all the tabs, and it is open to everyone, or you can pick and chose. It is not designed to run all the time, just to get to the properties and change permissions.

The point about gksudo gedit is that opens up a file in an editable state.That way you can work on it or change it.

---

