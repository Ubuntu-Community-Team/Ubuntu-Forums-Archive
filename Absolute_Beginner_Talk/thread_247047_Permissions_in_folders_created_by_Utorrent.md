---
title: "Permissions in folders created by Utorrent"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by arkangl on 2006-08-30
Hi, I'm new here, and I have a pretty specific question :
(I apologies, I don't remember if the right word to use is 'folder' or 'directory')

I am running Ubuntu on a laptop, and everything is perfect.
The laptop is kept in a closet, and I access it remotely (from a Windows besktop) via : 
- ssh
- remote desktop
- samba

I installed Wine and Utorrent, who are running just fine.

When a download is completed, I retrieve the file via Samba and delete it the same way.

My problem is with folders : 
My download folder has very liberal permissions, so that I can delete the downloaded files via Samba (as a guest).
When Utorrent downloads a folder, it is created with more restrictive permissions.
I can copy it via Samba, but not delete it.
For that, I have to use SSH, log in as a real user, and manually 'rm -R' the folder.

I can live with it, sure.

**But isn't there a simple way to make sure that all the folders created by Utorrent will have writing permissions enabled by default?**

All your tips are welcome.

---

### Post by bullgr on 2006-08-30
open a terminal and try this command:
> sudo chmod -R 777 /folder
there "/folder" put your folder you like to change the permitions

this command change the permitions of the folder and subfolders (-R) to read-write any user

for more info type in a terminal
> man chmod

---

### Post by arkangl on 2006-08-30
Thanks for replying.

I don't think it will sold my problem, though.

```
sudo chmod -R 777 /folder
```
will indeed grant the permissions I want, to all the folders contained in 'folder'.

But if Utorrent creates a new folder later on, the new folder won't have these permissions, and I wil have to use chmod again, right? 

I wonder if 'chwown nobody' could solve the problem...

To restate my question : 
**Is there a way for new folders to automatically inherit the permissions of the folder they are created into.**
(or is it already the case?)

---

### Post by arkangl on 2006-08-30
I found [this discussion](http://www.experts-exchange.com/Security/Linux_Security/Q_21794883.html) about a similar question, where someone mentioned the SGID bit.

Would it solve my problem?
(I'm currently at work, so I can't try anything before a few hours)

---

### Post by Nameless_one on 2006-11-19
So? Did anyone come up with an answer? :) 

(I am bumping this as I have the same question and the thread seems to have died before the issue was answered)

---

### Post by arkangl on 2007-02-28
I apologize for replying so lately.
I haven't been using this forum in a long while.

I have solved the problem by creating a cron job who runs a chmod -R 777 every few minutes.

It's not elegant at all, but it does the trick just fine.

---

