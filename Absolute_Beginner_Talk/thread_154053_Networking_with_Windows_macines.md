---
title: "Networking with Windows macines"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by onemoremile on 2006-04-02
I have just installed BreezyBadger 5.10.  I would like to network my Linux machine with the four Windows boxes on my home network in order to use the hard drive on the Linux machine as a backup repsository for the Windows boxes.  I have installed Samba and it appears to be running, yet I am unable to access the Linux machine from a Windows machine.

I have created a folder on my GNU desktop.  I enabled Windows sharing.  According to the sharing dialogue box the path to this folder is /home/user_name/Desktop/folder_name.  I have named my Linux box ubuntu.  (I know, this is not very original.)  From the Windows XP box, I went to "add a network place" and entered \\ubuntu\home\user_name\Desktop\folder_name and received the error message: "The folder you entered does not appear to be valid."  I get the same relsult when I substitute the ip address of ubuntu for the server name.

I am able to ping my Windows XP machine from my Linux box, ubuntu, and can ping the Linux machine from the Windows box.

What am I doing wrong?

---

### Post by catlett on 2006-04-02
Are you typing \\ubuntu\home\user_name\Desktop\folder_name? You are supposed to be replacing user-name with your user name, for example onemoremile. And you're supposed to be replacing folder_name with the folder you created, for example ubuntu. You're path should be \\ubuntu\home\onemoremile\Desktop\ubuntu. You might have done this and are just posting the instructions the way they were written, but  just in case you made this oversite I thought I would point it out. In the mean time I'll try to find out more info on networking or even better someone smarter than me will come along. Regards.

---

### Post by catlett on 2006-04-02
I found these links 
This is for linux to windows
[http://www.oreilly.com/catalog/samba...ook/index.html](http://www.oreilly.com/catalog/samba...ook/index.html)
[http://www.samba.org/samba/docs/man/...TO-Collection/](http://www.samba.org/samba/docs/man/...TO-Collection/)
[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)
 from this thread [http://www.ubuntuforums.org/showthread.php?t=150163](http://www.ubuntuforums.org/showthread.php?t=150163)
Good luck.

---

### Post by onemoremile on 2006-04-02
Yes, I did actually substitute my user name and the actual folder name for "user_name" and for "folder name."  I typed it exactly as specified.

---

### Post by onemoremile on 2006-04-02
Thank you for the links.  I had found the thread that you referenced earlier.  The first two links in your post were broken.  I was able to access the Oregon page and quickly got lost.  I attempted (with great trepidation to modify my smb.conf file and found that it opened as a "Read Only" file.  Since Samba seems to have configured itself when I installed it, I am not sure that I need to fool around with these settings anyway.

---

### Post by catlett on 2006-04-02
I apologise for not being able to give you the answer but I found a link that may help. This is the Ubuntu guide. Follow this link. The rest is the headings on the guide that I thoiught might help.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-ssh-server](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-ssh-server)
Chapter 7. Networking

Table of Contents

Samba Server
AntiVirus Server
SSH Server
DHCP Server
MySQL Database Server
Apache HTTP Server
Streaming Media Server

7.1. How do I configure network connections?
7.2. How do I activate/deactivate network connections?
7.3. How do I change computer name?
7.4. How do I browse network computers?
7.5. How do I use the DynDNS service?
7.6. How do I use Ethernet over Firewire?

One last link. This might be the best one for your problem.  [http://smorgasbord.net/samba_file_sharing_linux?PHPSESSID=3dc9ca9bcc1182ec9220f0ed36aa3323](http://smorgasbord.net/samba_file_sharing_linux?PHPSESSID=3dc9ca9bcc1182ec9220f0ed36aa3323)

---

