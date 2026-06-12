---
title: "How do I log on as root in the GUI?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by evolving_monkey on 2007-05-30
Root seems to own everything and I have not been able to change file permissions.  I need to edit files like menu,lst and smb.conf but it says they are owned by root and I do not have permission. When it's done scolding me it sends me to my room.

I would like to edit these things with the training wheel like comfort of a GUI. At least until I figure out what I'm doing. I realize this is a security nightmare but it really isn't a big deal in this case. Also i haven't been able to write to an ntfs drive because I can't enable read/write for a similar reason and I am hoping this might help me fix that as well (ntfs-3g is installed). 

If there is a way to do this please let me know.

Thanks for your time.

---

### Post by mkoehler on 2007-05-30
Just go to System>Administration>Login Window, then click the Security tab, then check the box that says "Allow local system administrator login"

---

### Post by sankarv on 2007-05-30
the initial user u created in installing ubuntu has the most priority among the users to work as root (it was set as that) . 

u can login with username as root and password as the initial user u created in installing ubuntu. it should login as root.





if it fails go for this.... 




u could openup a terminal and use sudo for running apps.


for e.g.
sudo firefox
also u can see the system preferences-> users and groups and in that for your user u can set the permissions for each type/group of applications with allow/deny (similar to root)  and then u can work without problems.

---

### Post by aysiu on 2007-05-30
There's no need to log in as root:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

And don't use *sudo* with graphical applications:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by eentonig on 2007-05-30
Short answer.

DON'T LOG IN AS ROOT.

And the answer to your problem?
> 
<alt><F2>
gksudo gedit
This will open the notepad program as root (works for all applications.) Now open the file you want to edit.

Homework: Read the links Aysu posted.

---

### Post by evolving_monkey on 2007-05-30
Thanks for the replies. I will try a everything out later today. I'll post back with the results.

Hoping this helps to solve a few of my issues. 

Thanks again for everyones time.

---

### Post by evolving_monkey on 2007-05-30
I tried "gksudo gedit" and got this:

(gedit:12478): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I tried "gksudo nautilus" to change permission an the ntfs partition:
It said that folder is read only (have ntfs-3g and ntfsprogs installed) and can not change permission.

I have done a fair amount of reading and I can't seem to change anything owned by root. This is a problem because root is never around to use the computer....I am. I'm beginning to feel that root doesn't like me and wants me to have a bad Ubuntu experience...........or I'm just missing something.

How do I change the NTFS partition from read only? Is that something I need to do from windows or is this a symptom of something else?

Thanks, as always, for your time.

---

### Post by wormser on 2007-05-30
Try going to Applications> System Tools> NTFS Configuration Tool.  Enter your password then check Enable write support.

---

### Post by aysiu on 2007-05-30
By the way, that warning for *gksudo gedit* is normal. Just ignore it.

To make NTFS read/write, follow [this tutorial](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html#more-143).

---

### Post by lazyart on 2007-05-30
The message you received after gksudo gedit is normal.  Just ignore it.

As for writing to NTFS, have you set things up with```
gksu ntfs-config
```
The preferred method is not to write to NTFS.  If you can create a FAT32 partition for files you want to edit in both Linux and Windows you'll be much better off.

Logging in as root is dangeous-- you can accidentally change permissions and ownership on stuff and make it hard to get back in.  Customarily when you need to use root to edit a file, you specify the filename when you call gedit:```
gksudo gedit /etc/X11/xorg.conf
```and then close gedit when you're done.  If you start opening other files from within the same instance of gedit (lets say you have files in your home directory you also open to edit) you could inadvertently save them with root permissions and have trouble fixing it later.

---

### Post by evolving_monkey on 2007-05-30
I appreciate the input, but unfortunately the commands don't help at this point. Not that I don't appreciate it. I just don't know what to do with things once I open them that way. New to Linux and the language. I want to learn all of the commands but I want to get to a certain point with the system so that I can do what I need to while I am learning. 

I am looking for graphical way to do these things for now. Like most people new to Linux, I simply don't have the know how to do much in a Linux terminal window..........yet.  It doesn't mean we're stupid...just not exposed.

I think I'll keep looking for the graphical solution for now. I am reading over the pages that Aysiu mentioned. We'll see if that spreads some light on my Linux dilemma and will maybe teach me a little about the command prompt stuff.

---

### Post by aysiu on 2007-05-30
Maybe you missed this screenshot-laden tutorial that I linked to earlier:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html#more-143](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html#more-143)

---

### Post by evolving_monkey on 2007-05-30
Or maybe you missed the part where I said I was reading over the pages you posted. I appreciate what you have done and I will look over the pages.

Thanks again for your time.

---

### Post by aysiu on 2007-05-30
> **evolving_monkey said:**
> Or maybe you missed the part where I said I was reading over the pages you posted.
Doh! I did miss that.

Well, hopefully that will get you sorted. If not... well, we'll worry about that then.

---

### Post by evolving_monkey on 2007-05-30
No problem....I am actually looking over them now. I think I might have a few answers. I'll post back with the new questions these answers inspire.
These pages look good....thanks again.

---

### Post by evolving_monkey on 2007-05-31
I figured out part of the problem. This is the post where I explain it. [http://ubuntuforums.org/showthread.php?t=450493](http://ubuntuforums.org/showthread.php?t=450493). 

I thought this was an unrelated issue so I started another thread. They sort of ran into the same problem. It did seem to solve at least part of what was wrong.

Thanks again for everything. I'll post back if the rest of the issue did not clear up.

---

### Post by evolving_monkey on 2007-05-31
Aysiu, the pages have been incredibly helpful. Thank you very much. They helped a lot once I figure out what was wrong. Almost forgot to mention.
Thanks again to everyone for the help.

---

### Post by eddieb on 2007-05-31
sudo -i

---

