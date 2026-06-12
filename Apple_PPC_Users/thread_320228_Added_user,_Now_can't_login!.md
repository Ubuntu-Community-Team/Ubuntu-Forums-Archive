---
title: "Added user, Now can't login!"
date: 2006-12-16
forum: Apple PPC Users
---

### Post by vengeance316 on 2006-12-16
I'm running Xubuntu 6.10 on my ppc iBook. It's been running great and I've been playing with it and have managed to get it just about perfect for me. The only thing that bothers me is the whole SUDO thing, so rather than mess with the way the root user is configured, I just added a new user as an admin to use for basic tasks that I don't want to be restricted to using a terminal for. Ever since adding the user, I can't login under any name... it usually just goes black, then shows a lot of code too fast to read, then starts the login window again. Every once in a while I get a message like "unable to write authorization, your hard disk may be full, please contact your administrator". I'm thinking about doing a clean install again, but I really don't want to lose all the tweaks and packages I had. Anyone know what can be done to fix this? Thanks.

---

### Post by taurus on 2006-12-16
What's the name of the new user that you added?

---

### Post by vengeance316 on 2006-12-16
It was oholyadmin. Kinda ironic, huh? ;)

---

### Post by taurus on 2006-12-16
And what groups does oholyadmin belong to and your regular user as well?

```
id
```

---

### Post by vengeance316 on 2006-12-17
My regular username was created during the install... I'm not sure what the default group is. oholyadmin is part of the admin group.

Is it possible to id the user if I'm not logged in?

---

### Post by vengeance316 on 2006-12-17
The exact error says:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator."

---

### Post by taurus on 2006-12-17
You can tell which groups a user belongs to by looking in /etc/group!  Now, you get that error message when you try to log in with your original account?  What's the output of this command then?

```
ls -la /home
```

---

### Post by vengeance316 on 2006-12-17
# cd group
cd: 5: can't cd to group


# ls -la home
total 4
drwxr-xr-x  4  root                root            1024  Dec 17 2006 .
drwxr-xr-x 21 root                root            1024  Dec 14 18:50 ..
drwxr-xr-x   2 oholyadmin     root            1024  Dec 17 2006 oholyadmin
drwxr-xr-x 15 vengeance      vengeance  1024   Dec 17 2006 vengeance

---

### Post by vengeance316 on 2006-12-17
Yes, when I log in under vengeance I get the error message like 1 out of 3 times.

---

### Post by taurus on 2006-12-17
It's

```
cat /etc/group
```

Is user vengeance the one having problem login in from GUI?  What does this look like then?

```
ls -la /home/vengeance
(delete files/directories that you don't want people to see...)
```

Also, what's the current disk status on your machine?

```
df -h
```

---

### Post by vengeance316 on 2006-12-17
vengeance is the only one that gives me the error message, the other users just recycle the login screen... regardless I can't login under any name.

cat /etc/group has way too much output for me to put on here.

Somehow df -h reports 0 Avail and 100% use on every drive it reports. No idea why, but I'm going to try and delete a large file and see if it will at least let me log in then...

---

### Post by taurus on 2006-12-17
Boot into recovery mode and do some house cleaning!!!

```
aptitude clean
```
Look in the /root/.Trash to make sure it's empty.  Then, look in both /home/oholyadmin/.Trash and /home/vengeance/.Trash as well.

---

### Post by vengeance316 on 2006-12-17
Ok, I managed to get it down to 94% by cleaning out my home folder... which is still pretty scary, but I seem to be able to log in now. Strangely enough, my panel is completely different... Items are moved around, launchers are gone, and my "applications" became "Xfce Menu"... I think my default environment got changed. :)  Thanks for the help Taurus, you saved me the pain of redoing everything over again! =D>

---

### Post by taurus on 2006-12-17
I guess your last success log in session must have filled up the space so stuff got moved around to accumulate it.  Therefore, you need to keep your eyes on the disk space if you know it is running low...  It wouldn't hurt to remove stuff that you don't want or don't need and look at this command every once in a while.  ;) 

```
df -h
```

Have fun.

---

### Post by coiske on 2006-12-17
Taurus: How do you boot into recovery mode?

I've come across loads of posts saying how to do this on intel machines that have Grub.  But I can't figure out how to do it on my powerpc machine, which has yaboot instead of grub.  (I desperately need to get into recovery mode to fix my corrupt /etc/sudoers file, so I can administer my computer again.)




Oops, nevermind.  I just figured it out.  (Apparently you can boot off the Live CD, open a terminal, use sudo passwd to create a temporary root password just for the duration of your Live CD session, use this new password to become root, figure out which hard drive partition contains your root file system using Gnome Partition Editor, manually mount that partition, and edit its /etc/sudoers file.  That did the trick for me.)

---

### Post by carlmccall on 2007-08-13
> **taurus said:**
> Boot into recovery mode and do some house cleaning!!!

```
aptitude clean
```
Look in the /root/.Trash to make sure it's empty.  Then, look in both /home/oholyadmin/.Trash and /home/vengeance/.Trash as well.

I can't change users to login as the system admin anymore. I set the autologin to start up the regular desktop user each time and now I get no option to switch that off.

How do you boot into recovery mode? And is it sufficient to type "aptitude clean" in the terminal upon opening it?

Typing **Linux single** at the boot prompt locks the computer up as does logging out (So I could SEE the login Panel again.)

How do I force the login panel to appear on boot up?

Thanks!

I have the "PowerMac7,3" system (Dual 2.0 GHz G5 Tower) with 512 of RAM.

---

