---
title: "I'm not the owner?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-04
I don't think it was like this before, but I just noticed that the File System has certain permissions that I don't think were there before (If they were, I didn't notice the little icon). When I went to properties, it said that I'm not allowed to edit them becuase I'm not the owner. There's only two accounts on this computer, mine (which is the one I made when I was installing Ubuntu) and one for my brother if he wants to use my computer.

---

### Post by catlett on 2006-06-04
[http://www.psychocats.net/ubuntu/permissions.php](http://www.psychocats.net/ubuntu/permissions.php) This is a detailed explanation ot permissions and how to edit them. 
It's a little confusing but it does have a logic to it. In linux (even though it may be your computer and noone else is on it) you only can alter/write to files in your home folder.
Each user has a home folder. That user can do anything to documents,files,applications,etc in his/her home folder. Only root (root in linux means administrative powers or account) can change,edit,alter files in all folders. So to change anything outside of your home folder you have to have root priveleges. In Ubuntu that is done through the use of the command sudo.
For instance if you want to edit the menu for grub it is owned by root not the user. So instead of calling up the document in gedit as a user with```
 gedit /boot/grub/menu.lst
``` You would do it with sudo in front because sudo invokes root priveleges (to learn more about root/sudo, this is the official document [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)) ```
sudo gedit /boot/grub/menu.lst
``` It may seem overkill if you are using linux for your personal computer but using root and user accounts are for security. This is one of the major reasons linux is not plagued by viruses like microsoft. In a microsoft system you run as administrator (root) all the time. That is why viruses wreak havoc in a windows system. Once they get in they have administrative priveleges and can do/alter any file in your system.
Anyways that page is written by forum member Aysiu and will explain in detail how to edit/change files that a user doesn't have permission to change

---

### Post by Amablue on 2006-06-04
Okay, as long as it's not a problem. I just hadn't noticed it there before and thought something might be wrong. 

Just to clarify though, the Home folder is the rough equivalent of the My Documents folder in windows, right? Where I'm supposed to keep my stuff?

---

### Post by catlett on 2006-06-04
[QUOTE=Amablue]Okay, as long as it's not a problem. I just hadn't noticed it there before and thought something might be wrong. 

Just to clarify though, the Home folder is the rough equivalent of the My Documents folder in windows, right? Where I'm supposed to keep my stuff?[/QUOTE]
Exactly. That is exactly what it is and how you should view it. Again it is a security measure. But anything in home (aka linux "my documents") can be accessed/altered by you as user.

---

### Post by alexamike on 2006-07-13
My problem is: My "home" folder appears to be owned by "root" .. not by me. I am getting this little window at logon which complains about this. How do I reset it to be owned by me?

---

### Post by aysiu on 2006-07-13
/home is owned by root.

But /home/alexamike is owned by alexamike

/home/username is always owned by username

---

