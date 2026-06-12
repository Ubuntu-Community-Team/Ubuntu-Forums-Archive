---
title: "I need to be root for all of two seconds"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Justin Holt on 2006-06-04
Right now i am experimenting witht the whole ipod linux thing.  And well, ubuntu is the only linux i have, and it doesn't allow me to be root.  What i need to do is to get files on to the linux partition of my ipod but the computer won't let me because i am not the "root" which is who my ipod currently belongs too. So at the current time, i can get files on to the ipod's windows partition but can not get them on the linux partition.  If i knew how to move files through the terminal i would and would not be posting here.  So can someone please tell me the right code to put into the terminal to get it to move files or can you tell me how to be root and move files through gnome.

thank you

---

### Post by Klaidas on 2006-06-04
To move a file:
```
mv /the/file/you/want/to/move /the_place/where/you_want_to_move/it
```
Example:
```
mv /home/klaidas/file /home/klaidas/Desktop
``` :)

As for root: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by steve.horsley on 2006-06-04
Easiest for you would be to open a command line and enter the command:
**gksudo nautilus**
Which will open a nautilus window with root privilege. **Be careful!**
If you want to copy between two root windows, File->New Window in your root nautilus opens a second root-privilege window so you can drag/drop between them.

---

### Post by cromestant on 2006-06-04
First of all Ubuntu does let you be root, you just have to know how.
There are tow ways :
sudo prefix, let's you run commands as root
For example :
sudo apt-cache search bla

Apt can only be run as root, so you see that sudo, checks wheter or not the user using it belongs to the sudoers group, and asks for the password.

I personally like to have my root user active ( gentoo habit) so I just activated it ( it's the same way for mac os BTW)
sudo passwd root
enter your user password, then the root password ( sometimes it doesn't ask for the user password , just for the root password)

Then you can use your root :
su
'root password'


Now, if you say that the partition is owned by root, then why not just change the owner?
man chown

you'll see, and, chown might want to be run as root since the partition belongs to root. so just use your root user, or sudo

Hope you can understand me.

Hope it helps.

---

### Post by aysiu on 2006-06-04
You may want to read these:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

