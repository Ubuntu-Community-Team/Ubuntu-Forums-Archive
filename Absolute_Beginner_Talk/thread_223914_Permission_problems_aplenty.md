---
title: "Permission problems aplenty"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Gyrotwister on 2006-07-27
Been having some permission type problems lately.  
When I try to delete files or folders I'm told “Access denied”.  

At the moment I'm trying to move some screensaver files from /usr/share/gnome-screensaver/themes so that I can keep a random screensaver setting but avoid the cpu intensive ones.  I wanted to create a sub folder in /usr/share/gnome-screensaver  and put the offending ones in there.  When I right click, the option to Create Folder is greyed out.  When I drag and drop a screensaver file I'm told Access denied.  

I'm the sole owner and user of this machine.  
How can I get around this permissions thing?

---

### Post by PingunZ on 2006-07-27
try ```
sudo *the command you'd like to do*
and enter your user password
```

---

### Post by Gyrotwister on 2006-07-27
I was afraid of that. Looks like it's time to learn some basic commands.  
 
If I'm going to have to do this sort of thing via the command line then could someone please point me to a "new user friendly guide to linux commands"?

Thus far I've been cutting and pasting.

---

### Post by moma on 2006-07-27
$ sudo nautilus 
But be careful. Your $HOME is beneath /home/.

$ gksudo nautilus
If you want a shortcut icon on desktop.

Command line stuff
[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")

For more help do:
$ man command_name
eg.
$ man find 


// moma
   [http://www.futuredesktop.com/ubuntu6.06.html#guides]("http://www.futuredesktop.com/ubuntu6.06.html#guides")

---

### Post by aysiu on 2006-07-27
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by justicerulesok on 2006-07-27
I'm having big problems with permissions - my first big linux test methinks.

I have no permissions on hdds, network or folder & files I create.

I will prevail, but not beofre my job ends tomorrow.

Good luck & if you find out beofre I do let me know & I'll do the same for you :-)

Justice.

---

### Post by Gyrotwister on 2006-08-01
Been busy for a few days but finally got around to trying out some of these suggestions.  
“sudo nautilus” worked for moving screensaver themes into another folder, but it wouldn't display files or folders on the Desktop.  

I had a locked folder on the desktop which was left over from a failed attempt to install the latest version of java.  Wound up using terminal commands to delete it and the contents.  

Desktop looks nice and tidy again.  

Thanks for the help.

---

