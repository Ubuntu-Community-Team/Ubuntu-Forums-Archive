---
title: "Newbie questions... bit more advanced"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by FDavid on 2007-06-28
Installed Ubuntu 7x today. :)  thanks to Andy Ithnako's column in the Chicago Sun-Times.  dual boot system with xp pro.

Since I used the update manager and it downloaded and installed 72 updates, I downloaded and installed a defrag program. defrag (0.73pjm1-7)

It installed into usr/sbin folder which is protected and it won't let me execute the program.  It says that since "you are not the owner"....

questions...
as I was checking out the file structure of the ubuntu partion, I noticed 2 users (root and David).  I set up David as the administrator so why won't Linux let me run the program?

How can I change "David" to the owner and not just a user?

since I am the only user on the computer, can I get rid of "user root"? 

how can I disable having to enter a password to access system programs and files?

am I correct in assuming that .../home/David is where data is kept?

I'm sure I'll have many more questions as this is just the beginning... :D

---

### Post by kevinlyfellow on 2007-06-28
Normal users don't run as administrators in linux.  This is something that makes it so secure.  In order to run your program, you need to ask for permission.  You do this by putting "sudo" in front of the command you are trying to run.  So for instance (I don't know the program, so this is just for an example!)
```
sudo defrag /dev/sda1
```
MacOSX uses the same method for security.

Also, there isn't as much issues with fragmentation in linux.  Most users never even bother defragging.

As far as "accessing system files..." you have access to read almost everything on your system, you don't have rights to write to those files.  It is unwise to disable the password, weak passwords are the main vector for security problems in linux/unix environments.  Have a look at this site [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Oh, and I should also add, if you want to automatically login without putting in a password, go to system -> Administration -> Login window.  Its under the tab security

Edit again... geesh.  Welcome to Ubuntu linux and the forums!

---

### Post by expatCM on 2007-06-28
erm .... since this is not Windows I was just wondering what you were anticipating that the defrag program would do for you since the Linux file structure works in a different way such that there are no fragmentation issues?

---

### Post by Nythain on 2007-06-28
ok

a. anytime something tells you you dont have permission to run or access something, try it with sudo (if its a command line app) or gksudo (if its a gui app you are launching from teh command line and you use gnome) or kdesu (same as gksudo but with kde). It will as for a password, thats YOUR password, not the root password, you should never really have to log in as root or su to root like some will suggest.

b. user David should belong to a group Aministrator along with many other groups, by default. Don't mistake this with windows Administrator. it means much less in linux, but it is the group that is default allowed to sudo

c. i would keep the user root just in case, not sure how linux likes to operate without the account, even though you should never really be accessing or logging in with it.

d. files can be kept anywhere... but /home/David is going to be the place that David has permission to write to by default... the rest of the file structure should be owned by root root, for security reasons, so you will need to sudo to write or access anything out of /home/David

e. most files will be installed into either /bin, /sbin, /usr/bin, /usr/sbin... and can usually be called from anywhere at the command line by just typing the name of the command. Some programs are downloaded as executable binaries and put wherever you want, and can only be called from within the directory they are located by typing ./command (where command is the name of the executable binary.... or from somewhere else in the command line probably by typing the full path like /home/David/downloadedprogramsdirectory/command but im not sure on that as i usually just cd to the location of the binary and ./ from there (that probably just confused the crap out of you)

f. a few sites that better explain the filesystem of linux
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

there are many other sites, i just grabbed the first couple i found since they will all pretty much explain the exact same thing

---

### Post by rillip on 2007-06-28
I think everything else has been covered pretty well, but wanted to touch on the root user.

Root is the same, essentially, as the Windows Administrator account.  It owns everything. It does everything. It knows EVERYTHING!! A bit over the top, but fairly accurate.

Go to a terminal and type ```
ps aux.
```  See all that stuff in there, like init, that's running as root?  Removing root would cause none of those to run, which would catistrophically nuke your system. No root = no OS, pretty much.

But as has been said, you won't reallly use the root account often, if at all.  It's just something the system needs.

---

### Post by FDavid on 2007-06-28
wow.  You guys really know your stuff.  And how refreshing not to get attitude with my morning coffee.  
Thank you.  I'll be back for more.

---

### Post by freebeer on 2007-06-28
Depends on the quality of coffee that you have... ***then*** we'll give you attitude!  :D

---

