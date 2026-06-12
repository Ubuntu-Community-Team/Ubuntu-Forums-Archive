---
title: "Network Servers confusion.. help!"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by zomgie on 2005-11-29
Hi guys,

My first few days of Ubuntu life Network Servers worked like a treat. Id enter it, It would find my windows network and find and connect to my other pc.

To the best of my knowledge *nothing* has been changed on either pc..

Now when I go to Network Servers, it prompts "you must log in to access UBUNTU on MSHOME", and similar messages.  I enter my correct username / password but it just keeps on prompting for it.. (there is only one account.)

If i click "cancel" the windows network shows up, but its empty.

Im a very, very confused little camper right now.  :confused: 

Thankyou for taking the time to read this post.

---

### Post by Ulokye on 2005-11-29
Are you trying to access this from a windows system to the ubuntu server? if so you need to look over your samba configuration. /etc/samba/smb.conf i think it is :)

---

### Post by zomgie on 2005-11-29
[QUOTE=Ulokye]Are you trying to access this from a windows system to the ubuntu server? if so you need to look over your samba configuration. /etc/samba/smb.conf i think it is :)[/QUOTE]

Thanks for replying.

No, Im in Ubuntu and want to look at the windows network.. which I used to be able to do..

This problem has really rendered Ubuntu half useless until fixed. :(

---

### Post by halfvolle melk on 2005-11-29
I had a similar problem, differing at 2 points:
- it didn't work from the start
- it was from ubuntu-to-ubuntu machine

Then I found this:
> Q: How to share public folders with read only permission (Authentication=No)?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3.

sudo mkdir /home/public
sudo chmod 777 /home/public/
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf

   4. Find this line

...
;   security = user
...

   5. Replace with the following line

   security = share

   6. Append the following lines at the end of file

[public]
   comment = Public Folder
   path = /home/public
   public = yes
   writable = no
   create mask = 0777
   directory mask = 0777
   force user = nobody
   force group = nogroup

   7. Save the edited file (sample)
   8.

sudo testparm
sudo /etc/init.d/samba restart
and now it works! Though I wouldn't know if setting up public folders raises any security issues.

For any of these topics:
> 3. How to share home folders with read only permission (Authentication=Yes)?
   4. How to share home folders with read/write permissions (Authentication=Yes)?
   5. How to share group folders with read only permission (Authentication=Yes)?
   6. How to share group folders with read/write permissions (Authentication=Yes)?
   7. How to share public folders with read only permission (Authentication=Yes)?
   8. How to share public folders with read/write permissions (Authentication=Yes)?
   9. How to share public folders with read only permission (Authentication=No)?
  10. How to share public folders with read/write permissions (Authentication=No)?
look here:
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by zomgie on 2005-11-29
Thanks man Ill try that out.. its definately something to do with Ubuntu..

I just figured out if I select the "connect to server" and enter the windows hosts ip address, its all peachy.

fingers crossed I can get this solution to work ! :p

---

### Post by halfvolle melk on 2005-11-29
Ps: If I remember correctly "sudo /etc/init.d/samba restart" didn't do the trick but rebooting did. Might just be something with my neolithic computers.

Good luck!

---

### Post by greenway on 2005-11-29
Had the same problem as half volle melk (originele naam trouwens!;)) after the second time a tried to get smb to work, also between several Ubuntu hosts. Wasted two days of my valuable time on this and decided to move to NFS since I am switching the entire office to Ubuntu, there's no need for smb anymore. And in my experience, NFS works one hell of a lot better then smb.

[EDIT]hmmm, after posting this, I realized I didn't really contribute anything to this thread; sorry for that:)[/EDIT]

---

