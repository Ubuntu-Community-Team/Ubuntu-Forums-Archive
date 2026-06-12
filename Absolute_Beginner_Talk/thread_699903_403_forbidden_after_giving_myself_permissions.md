---
title: "403 forbidden after giving myself permissions"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Kuroda_Shun on 2008-02-17
oops, didn't actually mean to post this,, just reading other "like mine" questions".
But since I did. I am trying to install phpbb2, I downloaded it but couldn't extract it to my var/www/ so I read around to find out how to write to it. I dropped the phpbb2 folder in the /var/www folder and went to it from my laptop. now  I get a 403 error page. Please help me?

---

### Post by mattismyname on 2008-02-17
You should probably give more details.

But check the parent directories.

---

### Post by Origin415 on 2008-02-17
Make sure you have executable permissions on the folders, otherwise apache can't open them.

---

### Post by Kuroda_Shun on 2008-02-17
ok. What are the proper commands and what should I save it as? Im sorry, I am an absolute beginner but I am learning. Look, I apologize for being ignorant to linux.

---

### Post by Origin415 on 2008-02-17
Sorry, I should have included the commands in my first post :[

Use the command

```
sudo chmod -R a+x */path/to/site's/root*
```

If that doesn't work, then post the output of

```
ls -l */path/to/root*
```

---

### Post by Kuroda_Shun on 2008-02-17
Thank you... I will do it right away.

---

### Post by Kuroda_Shun on 2008-02-17
still getting 403 forbidden from my laptop.
```
total 12
d--x--x--x  2 dallas root   4096 2008-02-17 21:13 apache2-default
---x--x--x  1 dallas dallas 1457 2006-07-26 12:50 index.html
d--x--x--x 12 dallas dallas 4096 2008-02-10 11:21 phpBB2

```

---

### Post by Kuroda_Shun on 2008-02-17
now my folder has an x on it and it's red???

---

### Post by Cappy on 2008-02-17
Use 
```
chmod 755 -R /var/www
```

I assume you have already used ```
sudo chown $USER:$USER -R /var/www
```

---

### Post by Kuroda_Shun on 2008-02-17
THANK YOU!!!!!!!!! So much... I was felling like I took two steps back... 
Can I ask more questions? like was that the right place to extract the phpbb software? I don't think I installed it right.

---

### Post by Cappy on 2008-02-17
phpbb2 requires a database.

Come to think of it you can just use the ubuntu phpbb2 package.

A guess is
```
sudo apt-get install mysql-server
```

and then
```
sudo apt-get install phpbb2-conf-mysql
```


There is the ```
sudo apt-get install phpbb2
``` package too. I don't know if you would need that since you already downloaded phpbb2.

I don't have any other ideas. There is probably a tutorial somewhere on the forums for dapper if you search on it.

---

### Post by Kuroda_Shun on 2008-02-19
Thank you. but I am having to start all over.. I think I hosed up the lamp install. :(

---

