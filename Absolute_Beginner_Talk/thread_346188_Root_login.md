---
title: "Root login"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Village on 2007-01-25
I'm trying to get LAMP running, I've been able to install all the necessary files though synaptic. 

Now though I need to get access as root, however I am trying to do this in the GUI as opposed to though the terminal. As I think graphically and then I can see what I'm doing.

Any advice, I will turn root off afterwards as I can see the use in not needing it for day-to-day activities. 

Thanks,

Village

---

### Post by taurus on 2007-01-25
Use

```
gksudo **command**
```

Otherwise, be careful with

```
sudo su
```

---

### Post by roger99 on 2007-01-25
You can also use

```
gksudo nautilus
```

In a terminal to give you a gui window but with root privilages.  Tread carefully though! :)

---

### Post by Village on 2007-01-25
Done the first one, it popped up with the root login as promised. Thanks.

I still can't change the files for the LAMP as it says we're not the user, permissions are set for root only and I'm not logged in as the user?

Any ideas,

Thanks

---

### Post by taurus on 2007-01-25
What files and where they are located?

---

### Post by Village on 2007-01-25
Trying to change document root from /var/www to one within my control, so that I can set up a testing server.

---

### Post by taurus on 2007-01-25
You mean you want to have write permission to /var/www!

---

### Post by Village on 2007-01-25
yes (sorry) write permission is needed. or the ability to change to a different folder. 

Have I made myself look silly?

---

### Post by taurus on 2007-01-25
You can change the ownership of /var/www so you can change and modify whatever you want in there.  _Assuming_ your login name is **village**, do

```
sudo chown -R **village** /var/www
```
Now, see if you can write to /var/www as **village**.

---

### Post by Village on 2007-01-25
Thanks for that, I changed the write permissions and now I trying to install my server stuff (just to try out, before I put it on my websites).

Thanks for the quick response and sorry for looking for the wrong solution. Still I've got to learn.

If only some of my other questions were as easy to sort out. 

Village

---

