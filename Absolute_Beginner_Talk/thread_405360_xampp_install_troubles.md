---
title: "xampp install troubles"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Copland Audio on 2007-04-09
Good Afternoon - 
I'm having difficulty installing xampp:  I downloaded xampp to my desktop and did the following:

brian@server:~$ su
Password: 
root@server:/home/brian# cd      (**I'm new to the ubuntu - I assumed I needed to be at the root directory to do this...am I wrong?  I tried this also at the /home/brian directory with no success, either...)

root@server:~# tar xvfz xampp-linux-1.6.tar.gz-C /opt
tar: xampp-linux-1.6.tar.gz-C: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /opt: Not found in archive
tar: Error exit delayed from previous errors
root@server:~#

---

### Post by tonyr1988 on 2007-04-09
If you downloaded it to your desktop, you will have to navigate to your Desktop before you untar it:

> cd /home/brian/Desktop
sudo tar zxvf xampp* -C /opt

P.S. You don't need su. You can just use sudo when you have permissions problems.

---

### Post by Copland Audio on 2007-04-09
Thanks!!

---

### Post by Copland Audio on 2007-04-10
wow, am I learning a lot...
The end goal is to set up a basic website I can host and manage.
Thank you for the help installing XAMPP.  I need to further understand/comprehend where my 'home' directory is to post my site.  I think I need to understand directories in general better as well - I've been a dragger and dropper in mac os' for years, and find myself getting a lot of directory errors in the shell... I'll continue my research, but any help from anyone on basic directory navigation techniques would totally be appreciated.
I've decided to give Joomla a try, and could use some advice.  I have Ubuntu Edgy, but could only find Joomla install directions for Dapper at: [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)  Since I've installed XAMPP on Edgy, how are my command line directions going to vary?  
I think I'm grasping the larger concepts, just learning how to incorporate the minutia.  I appreciate y'all's time!

---

### Post by tonyr1988 on 2007-04-10
If you're willing to learn some Terminal commands, you really will have a problem turning back to all-GUI. :)

For basic directory navigation:

> *cd ______* will "change directories" to the _______ directory
*ls* will list the files / folders in the directory you are currently in

You can add some arguments to ls. The big ones are:

> *-a* will show "all" files, including hidden ones (in Linux, a file is hidden if the name starts with a period)
*-l* (that's a lowercase L) will show a "long" listing. It will show the size of the file, who owns the file, the permissions of the files, etc.

You use them like:

> ls -l
ls -a
ls -la (it does both)

Your home directory is at /home/[username]. It is also "shortcutted" to the ~ symbol. So...if you want to change directories to your home directory, just do:

> ls ~

There are some really good online guides to helping you get started - those are some of the basics. Sorry it's so poorly written - I'll try to find an online reference for you in a little bit.

P.S. These commands are the same for all Linux distributions.

---

