---
title: "using subversion (SVN) server and client"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by ShendZ on 2007-04-01
hi guys,
i am desperate looking for answer of my question.

i need to set up an svn server which i guess i did. i followed this guide [http://www.edreaminghome.com/view_article.php?article_id=50](http://www.edreaminghome.com/view_article.php?article_id=50)

now, i need to know how to access it remotely (being able to make project folder, commit, checkout, etc from other machine)

so far, i can only access my repository trough [http://my_server_hostname/svn](http://my_server_hostname/svn) and of course it is still empty

i tried to issue
svn import <folder i want to import> [http://my_server_hostname/svn](http://my_server_hostname/svn)
but it doesnt work. i am sure it is not the correct way to do it.

basically, i am lost in this subject. please help

thank you

---

### Post by boredandblogging.com on 2007-04-01
maybe this would help: [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

---

### Post by whtet on 2007-04-10
Yes, [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion) the instruction here helps.

What is needed with the [http://www.edreaminghome.com/view_article.php?article_id=50](http://www.edreaminghome.com/view_article.php?article_id=50) is that you need to provide proper access for svn. Here is what I have done.

Create a group called 'subversion'
```
sudo addgroup subversion
```

Add user 'www-data' to 'subversion', like this "subversion:x:1001:www-data"
```
sudo vi /etc/group
```

Go to your subversion repository and change group for all the file and directory
```
sudo chgrp -R subversion .
```

Make sure that the files and directory are group writable
```
sudo chmod -R 775 .
```

I hope this helps.

---

