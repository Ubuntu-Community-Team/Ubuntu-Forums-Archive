---
title: "Auto-shut-down utility?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by jsiii on 2006-09-11
Hello, I was wondering if there is any tool that would turn off PC after specified amount of time passes.

I have tried KShutDown but it does not work (I suppose that's because Ubuntu does not use KDE), when I select Shut Down option Start button is disabled.

Do you have any suggestion? THX :-)

---

### Post by Najand on 2006-09-11
Usually the standard shutdown command can do it.
```
sudo shutdown -P <time>
``` 
The time argument is like now, Numerical (for N minutes)

---

### Post by jsiii on 2006-09-11
Thanks for the quick reply.

Now is there a way to store this as a script maybe and save it somewhere to have an icon on the desktop? It would be nice to skip password request for SUDO too. It would be nice if script asks user for the amount of minutes.

---

### Post by Najand on 2006-09-11
> **jsiii said:**
> Thanks for the quick reply.

Now is there a way to store this as a script maybe and save it somewhere to have an icon on the desktop? It would be nice to skip password request for SUDO too. It would be nice if script asks user for the amount of minutes.

Maybe this command can help when using Gui.
```
gksudo shutdown -P <time>
```

---

### Post by ruedu on 2006-09-11
I haven't been using Ubuntu long enough yet but there should be a group permission or shutdown setting you can set to allow a "normal" user to shutdown the computer as well, maybe someone else can comment on that.  Shutdown can/will use the /etc/shutdown.allow file to list people who can use shutdown.  You might also need to adjust the permissions on shutdown itself.

Anyway, you would just write a script that goes like this

#!/bin/bash

echo -n "Enter time to shutdown computer: "
read TIME

shutdown -h $TIME

Save the file and set the execute permission on it.

---

### Post by Najand on 2006-09-11
Sounds nice to me.

Maybe I can help you a little with the permission problem. shutdown
command itself need root permission, so even if you change the execute
permission of that shell script, it won't work... [COLOR="Red"]However I don't recommand  this method to newbies.[/COLOR]

So, first let us use ruedu shell script by adding sudo command before the shutdown command:
```

#!/bin/bash

echo -n "Enter time to shutdown computer (hh:mm): "
read TIME

[COLOR="Blue"]sudo[/COLOR] shutdown -h $TIME

```
Save this file something like shutdowntimer or something in /usr/bin and give the execute permission to users...

Then edit the /etc/sudoers:
Add the following lines to the /etc/sudoers (assume you want to give shutdown permission to a group called GROUPNAME):
```

#shutdown users
%GROUPNAME ALL=(root) NOPASSWD:/sbin/shutdown

```
[COLOR="Red"]
Caution:[/COLOR] You cannot edit /etc/sudoers even with sudo. You must change the permission from 0440 to 640. And when you changed the permission you cannot sudo until changing the permission value to 440. So it would be impossible to "sudo chmod 0440 /etc/sudoers" again, if you are planning to do it with sudo command. So [COLOR="Red"]DON'T[/COLOR] do "sudo chmod 640 /etc/sudoers, just login as root ... I know ubuntu is against using root or su... But in this case using root is recommanded... If you don't have a root accont just use "$ sudo su" and you will find yourself in root mode. then change the permission values of /etc/sudoers to 640. Edit it as above. Save it. change permission to 440 using "# chmod 440 /etc/sudoers" and "exit".


Now the people in GROUPNAME can set timer to shut-down computer at their desirable time.

---

### Post by frafu on 2006-09-18
Thanks for the explanation on how to shutdown in the terminal or within a script without being prompted for the administration password. 




@Najand 


Thanks for the explanation about how to edit sudoers. 

However I typed "sudo bash" in the terminal to get root access. 

Further, to allow the shutdown only to one user, I replaced %GROUPNAME with the login of that user:

```
 
loginname ALL= NOPASSWORD: /sbin/shutdown

``` 

Though I don't understand what the keyword ALL= does, it seems to be correct as it works. 


frafu

---

