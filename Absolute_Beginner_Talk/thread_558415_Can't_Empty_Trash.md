---
title: "Can't Empty Trash"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Paulmd on 2007-09-23
That is, I wasn't able to empty the trash normally. I had to drop into the console, and even then, i was forced to use sudo to remove the files in the trash folder. 

I'm curious as to why I was locked out, as a normal user from emptying my own trash.

---

### Post by Mister.Vash on 2007-09-24
Can you check ownership on your trash directory?
In your home directory you should have a file called .Trash
To check ownership, run the following from a terminal
```
cd ~
ls -ald .Trash* 
```

That command changes to your home directory, then provides details about any folder that start with .Trash

Hopefully you should see something like the following

drwx------ 19 *[COLOR="Red"]username[/COLOR]* *[COLOR="Red"]groupname[/COLOR]* 8192 2007-09-15 21:33 .Trash


If you don't have a .Trash folder in your home directory, you will need to create one, but from your description, it sounds like you do have one

My guess is that instead of seeing your username and groupname on the line, it may be showing root instead or a different name
drwx------ 19 **root** **root** 8192 2007-09-15 21:33 .Trash

If it is showing a name other than yours, then that needs to be changed to your name. So do the following, just replace user with your name and group with your group ( they should normally both be you logon name, but if you are not sure, you can do an ls -al to see what they are set to on your other files)
```
sudo chown [COLOR="Red"]*user*[/COLOR] .Trash
sudo chgrp [COLOR="Red"]*group*[/COLOR] .Trash 
```

Additionally, if the rights are not showing as drwx------ you would also need to do a 
```
sudo chmod 700 .Trash
```
to set the proper permissions

After doing these steps, change the directory into the .Trash folder, then use sudo to delete any existing files.  Then do a test by creating any test file, like a document someplace, either in your home folder or on your desktop, and then delete via the gui - see if it then shows up in the trash and if you are now able to empty it.

Regards

---

### Post by Paulmd on 2007-09-24
> **Mister.Vash said:**
> Can you check ownership on your trash directory?
In your home directory you should have a file called .Trash
To check ownership, run the following from a terminal
```
cd ~
ls -ald .Trash* 
```

That command changes to your home directory, then provides details about any folder that start with .Trash

Hopefully you should see something like the following

drwx------ 19 *[COLOR="Red"]username[/COLOR]* *[COLOR="Red"]groupname[/COLOR]* 8192 2007-09-15 21:33 .Trash


If you don't have a .Trash folder in your home directory, you will need to create one, but from your description, it sounds like you do have one

My guess is that instead of seeing your username and groupname on the line, it may be showing root instead or a different name
drwx------ 19 **root** **root** 8192 2007-09-15 21:33 .Trash

If it is showing a name other than yours, then that needs to be changed to your name. So do the following, just replace user with your name and group with your group ( they should normally both be you logon name, but if you are not sure, you can do an ls -al to see what they are set to on your other files)
```
sudo chown [COLOR="Red"]*user*[/COLOR] .Trash
sudo chgrp [COLOR="Red"]*group*[/COLOR] .Trash 
```

Additionally, if the rights are not showing as drwx------ you would also need to do a 
```
sudo chmod 700 .Trash
```
to set the proper permissions

After doing these steps, change the directory into the .Trash folder, then use sudo to delete any existing files.  Then do a test by creating any test file, like a document someplace, either in your home folder or on your desktop, and then delete via the gui - see if it then shows up in the trash and if you are now able to empty it.

Regards


Well, it works now, but i swear I didn't do anything.  Except reboot, and some cleaning up under the terminal. It seems that a certain photo editor had managed to fill my disk to 99% with temporary files, then crashed when there was no more room.  (Is it possible that it's not possible to empty the trash as a limited user when the disk is full ??? ) <shrug>

---

### Post by holihue on 2007-09-24
please mark this thread as [SLOVED]

---

