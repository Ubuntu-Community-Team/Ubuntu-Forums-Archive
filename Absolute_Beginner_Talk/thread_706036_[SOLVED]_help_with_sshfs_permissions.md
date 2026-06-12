---
title: "[SOLVED] help with sshfs permissions"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by belfasttim on 2008-02-24
Hi-- sorry for the dumb question, but here's an easy one for you guys:

I'm running 2 gutsy machines in my local network, one is server edition and one is desktop, the server is used as my web dev platform but also serves pages outside too.

I mounted the dev directory (/var/www) of the server machine via sshfs onto my local desktop, no problems, I can now view files on the server. 

However, even when the sshfs login user is a member of the www-data, admin, and even root groups on the server machine, and the whole /var/www dir is chmod'd to 775, I still can't modify or create files on the dev box. Not via command line ssh, not via sshfs.  

I am getting kinda tired of typing sudo to write a file, and I don't think I can chown the web directories for fear of blowing away permissions for apache, lightty, rails, mysql, etc.

One other odd thing-- root owns most of the files and folders in the /var/www directory, but inside the html root "1010" owns most of the files-- however, this user doesn't show up in my userlist. Is this the "nobody" user?

Any hints much appreciated!

Tim

---

### Post by m@ra on 2008-02-24
Let's say you have chmod all the files to 775 that means owner and group has full access (maybe you are in neither one!). I would recommend now to check the group membership.

What u can do of course is change the group owners. I have exactly similar set up (two gutsys which of another www) and rights are with chmod 744. I'm owner and group. Others can only read.

For html files under www read is fine at least.

Hope this helps.

---

### Post by belfasttim on 2008-02-25
> **m@ra said:**
> Let's say you have chmod all the files to 775 that means owner and group has full access (maybe you are in neither one!). I would recommend now to check the group membership.

What u can do of course is change the group owners. I have exactly similar set up (two gutsys which of another www) and rights are with chmod 744. I'm owner and group. Others can only read.

For html files under www read is fine at least.

Hope this helps.

thanks m@ra, but the files are 775 and I am in the groups. I'm an idiot-- I think I just had to log out and back in. My bad! Appears to be working now!

---

