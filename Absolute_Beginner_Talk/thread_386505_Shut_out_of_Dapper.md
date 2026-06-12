---
title: "Shut out of Dapper"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by nnjond on 2007-03-17
Oh,oh! Following  advice A, B has happened.


A:
 -type "sudo dpkg-reconfigure xserver-xorg"

Choose your graphics card/adapter from the list, follow the text, if there's anything you don't understand press "esc" (this will skip). When you come to resolution, enter 1600x1200 with the space-bar. Choose "medium" for the settings, move down to 1600x1200@75Hz.

This will give you a range of resoloutions between 1600x1200 and 648x480.


B: 
All seemed to go perfectly well. However when i restarted, the user and password screens appeared, so i tapped in my details... It halts on a black page of text before returning to the user and password screen. There dosen't seem to be a way in?

---

### Post by Arby on 2007-03-17
If it's what I think it is, then this happened to me a while back after I had been fiddling in xorg.conf. What happens when you try to login off the commandline? I suspect there may be a lock file in /tmp that isn't being deleted, or at least that's what happened to me.

Try this, when you get to the graphical login press crtl-alt-F1. You should get to a white on black text screen with a login prompt. Enter your username, hit enter then enter your password.

If you see error messages, post them here. If you can login OK then enter 'startx' (no quotes) at the commandline. Tell us what happens. Again, if there are error messages write them down and post them here.

Hope that helps.
Arby

---

### Post by nnjond on 2007-03-17
Thanks for your interest. Crtl- alt- F1 didn't work.

---

### Post by Arby on 2007-03-17
That's odd. CTRL-ALT-F1 should drop you to a terminal. I don't know why that won't work. OK try this instead. Boot the machine and press escape to get to your list of boot options. Select 'Single-user mode', it might also be called recovery mode.

This should get you to a terminal. Then try the login and startx commands I suggested earlier. Let us know what happens.

Arby

---

### Post by nnjond on 2007-03-17
Thanks again.

Recovery mode takes me to a promt

~# startx

Takes me to the desktop  with a warning:

Power Manager

- cannot start untill you start dbus system service

Strong recomend reboot after starting Messagebus

???

---

### Post by Arby on 2007-03-17
Hmm, if it takes you into the desktop it suggests that your original problem of not being able to login to an X session has been solved. Although I've no idea why. The powermanager warning is a separate thing. It could be because you are in recovery mode, I really don't know how the system services behave under those circumstances.

When you boot to recovery mode what does the prompt look like? Is it ```
you@yourcomputer
``` or ```
root@yourcomputer
``` I have a feeling it will be the second one. That means you are actually working as root, which would give you extra permissions. Don't worry too much about the power manager thing for now, lets just make sure we have your X problem sorted properly first.

Try doing this. When you boot to recovery mode run the following command and post the output here. ```
ls -la /tmp
``` You're looking for a file called something like .X0-lock. I think these lock files timeout eventually but I'm not sure. So it's possible that has happened while we have been looking at this.

Answer the question about the prompt and show the output of the above command then lets see what we've got.

---

### Post by nnjond on 2007-03-17
~# startx  takes me to a 'recovery'  desktop .

from a terminal i have...

root@nnjond-desktop:~# ls -la /tmp
total 44
drwxrwxrwt 10 root root 4096 Mar 17 17:52 .
drwxr-xr-x 21 root root 4096 Feb 22 07:36 ..
drwxrwxrwt  2 root root 4096 Mar 17 17:52 .ICE-unix
-r--r--r--  1 root root   11 Mar 17 17:52 .X0-lock
drwxrwxrwt  2 root root 4096 Mar 17 17:52 .X11-unix
drwxrwxrwt  2 root root 4096 Mar 17 17:52 .esd-0
drwx------  3 root root 4096 Mar 17 17:52 gconfd-root
drwx------  2 root root 4096 Mar 17 17:52 keyring-G3aDnq
srwxr-xr-x  1 root root    0 Mar 17 17:52 mapping-root
drwx------  2 root root 4096 Mar 17 17:54 orbit-root
drwx------  2 root root 4096 Mar 17 17:52 ssh-YBwWDo4051
drwx------  2 root root 4096 Mar 17 17:52 virtual-root.3nHLeC
root@nnjond-desktop:~#

---

### Post by Arby on 2007-03-17
> **nnjond said:**
> ~# startx  takes me to a 'recovery'  desktop .

from a terminal i have...

root@nnjond-desktop:~# ls -la /tmp
total 44
drwxrwxrwt 10 root root 4096 Mar 17 17:52 .
drwxr-xr-x 21 root root 4096 Feb 22 07:36 ..
drwxrwxrwt  2 root root 4096 Mar 17 17:52 .ICE-unix
**-r--r--r--  1 root root   11 Mar 17 17:52 .X0-lock**
drwxrwxrwt  2 root root 4096 Mar 17 17:52 .X11-unix
drwxrwxrwt  2 root root 4096 Mar 17 17:52 .esd-0
drwx------  3 root root 4096 Mar 17 17:52 gconfd-root
drwx------  2 root root 4096 Mar 17 17:52 keyring-G3aDnq
srwxr-xr-x  1 root root    0 Mar 17 17:52 mapping-root
drwx------  2 root root 4096 Mar 17 17:54 orbit-root
drwx------  2 root root 4096 Mar 17 17:52 ssh-YBwWDo4051
drwx------  2 root root 4096 Mar 17 17:52 virtual-root.3nHLeC
root@nnjond-desktop:~#

OK, I'm not sure but I *think* that the line in bold above might be the reason you can't login from the graphical login. Try deleting that file and then booting the machine in 'normal' mode and logging in from the graphical login, see what happens. Use the following command to remove the file ```
sudo rm /tmp/.X11-lock
```

---

### Post by nnjond on 2007-03-17
The line in bold is :

-r--r--r-- 1 root root 11 Mar 17 17:52 .X0-lock

i  guess your command 

sudo rm /tmp/.X11-lock

is an error.


sudo rm /tmp/.X0-lock

didn't let me in the 'front door' I'm afraid.

-r--r--r--  1 root root   11 Mar 17 18:48 .X0-lock
Is still there ?

 I am at a desktop but not with my icons on it. The res has gone up to 1600x1200 but the Refresh is still at 60Hz

---

### Post by nnjond on 2007-03-17
Have removed the .file but no joy.

---

### Post by Arby on 2007-03-17
Yes that was the right file to remove, my mistake

You can get to a graphical desktop which means you have a functional X setup. There is some kind of permissions problem that is preventing you logging into X as a regular user but I have no  idea what it is. 

I'm out of ideas sorry. I hope you can get it fixed.

---

### Post by Arby on 2007-03-17
This is niggling me now so I did a bit more searching on google. This is a complete hunch but it might be worth a go. I've read a few mailing list posts that imply that a change in the ownership of a file in your home directory called .Xauthority can block a non-root user from logging in. When you ran the dpkg-reconfigure command it is possible that the ownership of this file got changed in the process. We're in the realms of pure guesswork now but we may as well try.

Run this command ```
ls -la /home/you | grep X
``` then show us the output from that. For reference if I do it on my system I see this ```
-rw-------  1 richard richard  393 2007-03-17 09:07 .Xauthority

``` The two occurences of 'richard' are the owner and group of that file. If these are set as root on your system then that could be the problem. If not we'll have to keep looking.

---

