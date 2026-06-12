---
title: "Cannot access new samba folder from windows"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by hvollebregt on 2007-07-24
I have installed Xubuntu 7 on an old computer. The purpose is to build a computer that I can use to store backups of my photos on, and use for downloads (the latter using hellanzb). So far, so good: I have successfully installed Xubuntu, samba, and hellanzb. It is all working. I can make backups of photos, download stuff, etc. 

I can access all folders, place backup files in them, retrieve downloaded files from them. No problem.

Where it becomes a problem is here: hellanzb creates new folders for stuff it downloads. For some reason I can *not* delete files from the new folders from windows. I can pick up files from them, but not delete them. In order to be able to delete them, I have to go to my xubuntu system and use chown, and chmod for every folder.

What I want to achieve is that all authorisations are applied to new folders.

I am a newbie to Linux, and was quite proud that I could install Xubuntu (this shows the quality of Xubuntu!). I have been looking for an answer for this for quite a while now. Any help highly appreciated!

-----
Hans | [http://www.okebaja.com/](http://www.okebaja.com/)

---

### Post by kngunn on 2007-07-24
Samba is REALLY powerful -- so it can get quite complex as well.

Check your smb.conf file (/etc/samba/smb.conf).  The share in question (if not a home folder) needs to be writable = yes OR read only = no.  Also, check who the owner of the files is versus the user trying to delete the files.  If they don't match you can set force user = <username> (put in the actual username and no brackets) so that when you log in via samba you can match the name  (and rights) of the user that created the files.

Lots of options...  You might want to post the folder name, share name, owner of the files, and username you are using when you log in via samba as well as your smb.conf file.  That should make the answer fairly obvious to some of the folks around here that have used samba quite a bit.

---

### Post by hvollebregt on 2007-07-25
Perfect! Thanks a lot, it works now.

Setting 'force user' and 'force group' did the trick. According to the guide I used to set samba up, I had to set 'force user' to nobody, and force group to nogroup. After I changed these into force user = <my user> and force group = <my user's group> it worked.  

I also noticed that for one folder the group was different. Don't know how that happened, anyway I changed the owner and it all works as expected now. New folders created by hellenzb get my user as owner and my group as group.

Thanks a lot, much appreciated!

---

