---
title: "[SOLVED] Help! I messed everything up!"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by AndrewEsther on 2008-04-06
In a vain effort to get control of a folder, I changed my user's home directory to /...

oops..


now I log in and it gives me a bunch of garbage and then immediately logs me out. crap. should I reinstall now??

I tried logging in as an ftp user account that I made as a low-level restricted account for remote access, and when I try to edit users and groups, it asks me for my admin password. fine, that's expected. I enter it, over and over again, and to no avail. it informs me that my password for 'root' is wrong, and that I am unable to change these settings as this user.

how do I log in as root? or how do I fix this? GAH!

---

### Post by Rocket2DMn on 2008-04-06
Reboot into the recovery mode kernel from GRUB and run
```
usermod yourusername -d /home/yourusername 
```
Here is the man page for your reference: [http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)
Then reboot with
```
reboot
```

---

### Post by AndrewEsther on 2008-04-06
sweet... here it goes.. if you're not thanked when I log back in it didn't work :-)

---

### Post by Rocket2DMn on 2008-04-06
Just post back your results, if it doesn't work, we'll keep trying.  Good luck.

---

### Post by AndrewEsther on 2008-04-06
okay, perhaps I'm not doing this right... I went to sessions, selected the terminal one session....

I ran usermod andrew -d /home/andrew

and I got something along the lines of 'user /home/andrew does not exist'

wtf?

---

### Post by Rocket2DMn on 2008-04-06
Try it like this
```
usermod -d /home/andrew andrew
```
with your name at the end of the command.  Order often doesn't matter, but I guess in this case it does.

---

### Post by AndrewEsther on 2008-04-06
and now I'm getting an error about not being able to lock the password file...?

---

### Post by AndrewEsther on 2008-04-06
haha! got it!

I used

sudo usermod -d /home/andrew andrew

and now I am back on my account :-)

THANK YOU!

now I have another question... how do I give my user (andrew) read/write permissions to the folder /var/www so I can put .htm files etc. in there for use as a web server? I try to put files in there, or make directories, or anything and it tells me I don't have permissions for that folder... the only way I was able to make a directory in there has been to use

cd /var/www
sudo mkdir andrew

and it made me the directory /var/www/andrew but I still don't have ownership of it... blah!

---

### Post by Rocket2DMn on 2008-04-06
Yeah, you need to use chown.
```
sudo chown -R andrew:andrew /var/www/
```
That will change everything inside the /var/www to be under your ownership.  I think for security reasons you are supposed to run apache servers as limited users, so that is good.  You would just need to check who is actually running httpd (or whatever the daemon for apache is called).
The command to change read/write/execute (aka rwx) permissions is "chmod".  In your server you will want permissions like "644" for non-executable files and "755" for executable files like server side scripts.  If you have no idea what I'm talking about, 644 permissions are what you want (html files, images, etc).  The syntax for that is
```
chmod xyz filename
``` where xyz are the rwx permissions.  You can easily google around for help with that.

---

### Post by AndrewEsther on 2008-04-07
so does 644 and 755 refer to the level of permission for read/write/ex respectively?

Like, if I wanted to grant access to the file index.htm I would use

(inside /var/www)
sudo chmod 644 index.htm


can I do the same thing with the right-click function in the properties->permissions tab? can you tell I'm ingrained with the MS train of thought? haha

oh, and how do I 'thank' you? :-)

---

### Post by Rocket2DMn on 2008-04-07
Using the GUI will work just fine.  The number comes from binary, 3 bits = 2^3 = 8 different levels (or 0-7).
So 644 = rw-r--r-- for OwnerGroupWorld permissions.  That means you have read/write permissions and everybody else has read only permissions
755 = rwxr-xr-x - you have read/write/execute permissions and everybody else has read/execute permissions.  The World column is what people from the internet accessing your site have.

The GUI is easy for single files, but the terminal is powerful for doing multiple files or entire directory hierarchies.  The -R I used above means recursive.
Also, say you move a bunch of jpg files to a an image folder.  You can do
```
chmod 644 -R /path/to/image/folder
or
chmod 644 /path/to/image/folder/*
or for jpgs files only
chmod 644 /path/to/image/folder/*.jpg
```

To Thank a user on these forums, you click the little blue and gold medal at the bottom right of a post.  It is used to Thank users for especially useful posts/responses.  It's a fun little thing to have I guess, but don't judge people based on their Thanks or Bean counts.  There are plenty of knowledgable users out there with good advice to give but don't have a lot of participation.  I happen to prefer the excited responses people often give when I help them nail down a problem, even if they don't know how to "officially" Thank somebody.
:guitar:

---

### Post by AndrewEsther on 2008-04-07
sweet! I actually understand that now :-) I've gotten so used to not having to deal with anything deeper than just the bare subsurface of a GUI, that I didn't even know where to start thinking about what those values might have meant. and to think that this morning I was ready to give up on ubuntu all together... I'm still not sure if it's going to be a practical step for me to use it on my server, but I'm at least not going to throw it out as a nice option for an OS on a desktop or some non-mission critical pc whereupon it stops working and it's up to me to fix everything... I wish I could just sudo apt-get allknowledge.everyonesbrain.org/knoweverything

hahaha


thanks again. sorry in advance if you hear a lot of me whining and asking repetitive questions on these discussion boards.

---

### Post by Rocket2DMn on 2008-04-07
LOL, there really are no stupid questions, I've seen it all.  Everybody around here will be glad to help out, we're here to help ease people's transitions to Ubuntu and linux in general.  Linux really is a viable alternative for most people, you just have to be willing to learn - the common term is "Linux is Not Windows."
Happy Ubuntuing!

---

