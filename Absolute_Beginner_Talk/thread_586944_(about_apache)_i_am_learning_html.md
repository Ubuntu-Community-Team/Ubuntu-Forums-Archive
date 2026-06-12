---
title: "(about apache) i am learning html"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-10-22
before installing Linux i used to use iis in windows for viewing my files in window i used to type [http://localhost/filename.html](http://localhost/filename.html). in linux i could do the same (after installing LAMP). but i could not create a .html file in /var/www/ it gives an error access denied.
i am using LAMP to just see (in my browser) web pages i created. and do not want to publish it to the net.

---

### Post by KCPokes on 2007-10-22
Su to root, or do a sudo, to grant write permissions for the /var/www directory.  As it is all local, I'd just do a "sudo chmod -R 777 /var/www".  That will grant write permission to anyone on the machine.  If you are concerned about someone overwriting it, you could tune those permissions to something more secure.  For local web development I don't worry about it much.

---

### Post by rahul_bhise on 2007-10-22
i also want to know that would other people on the internet could see my web pages and change it at their will

---

### Post by KCPokes on 2007-10-22
That is a multipart question.  Could other people on the internet see it?  That depends on your setup at home.  Is your machine set up on a private network, separated by the use of a router, for example?  If so, then no, not unless you specifically opened up port 80 and forwarded traffic to your server.  

If they could see your pages, because you had set it up as such, then it would require your server to be compromised in order for someone to change your pages.  This gets down to security and taking the proper precautions to ensure your server is up to being exposed to outside traffic.  Maintaining a server is a two-fold job; getting a server up and running is nothing, but ensuring that it stays up and is secure is the bigger of the tasks.

---

### Post by rahul_bhise on 2007-10-22
> **KCPokes said:**
>  "sudo chmod -R 777 /var/www"

it is not working the owner of the folder is still the root

---

### Post by KCPokes on 2007-10-22
> **rahul_bhise said:**
> it is not working the owner of the folder is still the root

The owner can still be root, but with the 777 you've allowed anyone to write to that folder.  If you'd rather change the ownership of the directory, issue a "sudo chown -R <youruserid> /var/www"

---

### Post by kostkon on 2007-10-22
If you don't want to mess with the permissions of the */var/www* folder, you can activate the *usedirs* module in *Apache*:
```
sudo a2enmod userdir
```

Restart *Apache*:
```
sudo /etc/init.d/apache2 restart
```

and then create a folder named *public_html* in your home folder and put your files there. Then, you will be able to access them, for example, like this
```
http://localhost/~yourusername/index.html
```

---

