---
title: "How to change folder/file permissions - SUDO NAUTILUS does not work????"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2008-01-28
I copied several folders from one account to another and now all these folders and files within them are locked. 

I tried -**sudo nautilu**s- to change permissions, but when I click on the permissions tab the browser **freezes** and I cannot change anything. After several trials I was able to change permissions for one folder, but then [B]all the files and subfolders were still locked.
[/B]
If I cannot use graphical method, and BTW can I do it graphically anyway to click on say 12,000 photo files to change their permissions???,

how can I use terminal to change permissions for all Home folders **at once,** files within and subfolders without doing it for every folder within?

BTW, I tried under groups to make the account belong to root group but that does not help.

Thanx!!!!!!

---

### Post by Ub1476 on 2008-01-28
You use the chown command to change permissions. I think it's something like this:

```
sudo chown * username
```

*=All files

To change permission for one folder, which is called "Pictures" you do this:

```
sudo chown Pictures username
```


I haven't been using the chown command much, but hope I got it right:)

**NOTE: It might be that "username" should be infront of the file/folder name.**

---

### Post by MaximB on 2008-01-28
In the terminal :

sudo chown -R youusername:yourgroupname(which is your username) /path/to/home

something like this :

sudo chown -R maxim:maxim /home

This command making YOU the owner of those folders and subfolders.

more on that : man chown

---

### Post by amingv on 2008-01-28
> **MaximB said:**
> In the terminal :

sudo chown -R youusername:yourgroupname(which is your username) /path/to/home

something like this :

sudo chown -R maxim:maxim **/home**

This command making YOU the owner of those folders and subfolders.

more on that : man chown

I think you meant '/home/user'. It is not advisable to change the whole /home dir to your control.

---

### Post by MaximB on 2008-01-28
> **amingv said:**
> I think you meant '/home/user'. It is not advisable to change the whole /home dir to your control.

You are right.
But that was only a demonstration on how to use it.

---

### Post by Joeb454 on 2008-01-28
also you shouldn't really use ```
sudo nautilus
```

If you want to launch anything graphical with admin privileges you should use ```
gksu nautilus
```

---

### Post by Sidewinder1 on 2008-01-28
I believe the command to give Nautilus temporary Root privileges is:

gksudo nautilus
Please try that.

---

### Post by Sidewinder1 on 2008-01-28
Beat me too it :-)

---

### Post by MaximB on 2008-01-28
Two pairs of similar answers in one thread. 
Maybe we should make a forum game out of it called "beat me up !"
One asks a question and whoever answers faster wins and gets to ask his question ;)

---

### Post by bcrom on 2008-01-28
also try chmod for more control over permissions.  Type 'man chmod' or google it to learn the codes.  For example, chmod 777 [folder] gives all users all permissions on a file.

---

