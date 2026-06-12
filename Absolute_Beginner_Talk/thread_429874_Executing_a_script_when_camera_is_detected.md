---
title: "Executing a script when camera is detected"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Dial-Up on 2007-05-01
By default, Ubuntu will try to open some gthumb program when I plug my camera into USB. I'd rather have it just move the files off of the camera and then unmount. However, when I tried to make a simple bash script to copy the files, it didn't work. It didn't bring up a terminal either, so I couldn't see if there was an error or anything. (Note: I'm not a bash scripting expert, I just looked this up in a tutorial.)

Here's what my script looked like (saved to ~/test_bash):
```
#!/bin/bash
cp $1 ~/test/
```

And for the command when the camera is detected, I put this:
```
bash ~/test_bash %h
```

Nothing was copied, and there was no error message, or anything. When I executed the script from the terminal, it worked fine.

Also, I was looking at the eject command, and it wants the device to be in /etc/fstab, or I have to use sudo. Is it possible to set this up in fstab? (Or is there another way of doing this?)

Thanks.

---

### Post by LaurelLynn on 2007-05-01
When the camera is plugged in it should be mounted to a folder in /media so for example:

$  rsync -r /media/camera  /CameraPics  (assuming the folder is named "camera")

Would copy every new image from the camera to the CameraPics folder. So you could run
a command like  that every few minutes using a crontab entry.

For that read the manpages for "cron" and "crontab" it is not** too** cryptic.

---

### Post by Dial-Up on 2007-05-01
Thanks for the reply, however I'm hoping to be able to do something a little bit more advanced. I have a Windows batch file that I wrote to automatically organize the pictures into a year/month/date directory structure, and I would like to be able to replicated this, since I'm hoping to switch to Ubuntu permanently. Granted, this wouldn't be a deal breaker, but it would be very nice to have.

---

### Post by LaurelLynn on 2007-05-01
Dear Dial-Up,

I am sure there is a way to write a shell script that will accomplish what the batch file did. Also there will be a way to get it to run only when you plug the camera in. Problem is Windows batch files are windows and dos only.  So there are two options:

Find someone with the knowledge and experience to reproduce it for you, and be very nice to them (incentives help: "what a wonderful smell, are those cookies fresh baked." "Well I could part with one if...").

Or, learn the bash shell on your own (a fine and worthy endeavor!)

First I would search around online.  I bet there are several open source programs for camera syncing. They won't do it exactly as you had it before, but would take a lot less effort.

---

### Post by Dial-Up on 2007-05-01
I have no problem figuring out how to write the script myself. My problem is that the command in the "Removable Drives and Media Preferences" program for when a camera is connected doesn't seem to work for bash scripts.

---

### Post by LaurelLynn on 2007-05-01
Ahh, that is probably because it is running a gnome program, or uses gksudo/gksu. 

Shell script are used with sudo/su instead.

May still not work that way if it is bound to Gnome or other graphical apps. The source code for the underlying program may call a shell command though.

---

### Post by Delkster on 2007-05-01
The commands defined in "Removable Drives and Media Preferences" don't use any flavour of sudo, and I don't *think* it should matter if you launch just a shell script from such a place.

I don't have a camera at hand but I tried it with the mouse (the preference dialog also offers an option for running a command when a mouse is inserted) and a shell script ran just fine.

I didn't run the script with any arguments, though. I think this may be your stumbling point. It isn't completely clear to me if bash considers the first argument that isn't a known bash command-line switch as a filename for a script to be executed and all further arguments after that as arguments to the script, but to me it doesn't look like it does. I wouldn't be surprised at that either.

You can specify the script directly as a command rather than calling bash explicitly, though. That'll probably sort out the argument issue for you as well, although for future purposes it might of course be interesting to figure out how the arguments should be specified when running bash explicitly.

Another thing to consider is that ~ may not work as a reference to the home directory in the Gnome configuration dialog. Thus, at least if you're calling the script without giving it explicitly as an argument to bash, you probably need to use an absolute path name, such as /home/username/test_bash/foo.sh.

Good luck. You may want to look into rsync rather than just cp, though.

---

