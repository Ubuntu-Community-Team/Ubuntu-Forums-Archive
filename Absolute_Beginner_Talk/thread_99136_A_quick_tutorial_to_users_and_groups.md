---
title: "A quick tutorial to users and groups"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-05
Hello everyone

I am looking for a quick way to understand the idea of users and groups. In a nutshell, what are groups? 

I logged into my Ubuntu file server as root from my Windows box on the network and moved all my data from the Windows machine to the Ubuntu server through SSH. Therefore all the data is "owned" by root. 

I then realized my mistake, and created a user called data. Then I moved all the data that I copied into the /root from Windows into /home/data. 

Now how do I make delta the owner of all the files (we are talking lots of files and nested directories, hence something recursive is needed.) ?

Basically my Ubuntu machine is my file / web server and I will be accessing it from outside my home network as well. I would prefer logging in as data to be able to access my files. 

Thanks !

PS: Don't forget the groups part.

---

### Post by ChrisTheGeek on 2005-12-07
The best guide I've found to explain users and group permissions is at 

[http://www.linux-mag.com](http://www.linux-mag.com)

And is titled: Sharing Files (Carefully) 

You will need to register (free) in order to read the article, but it should answer all your questions.

In addition, there is plenty of documentation online and already on your computer.  Try viewing the man page for chmod, chown, and chgrp.

Chris.

---

### Post by ChrisTheGeek on 2005-12-07
The best guide I've found to explain users and group permissions is at 

[http://www.linux-mag.com](http://www.linux-mag.com)

And is titled: Sharing Files (Carefully) 

You will need to register (free) in order to read the article, but it should answer all your questions.

In addition, there is plenty of documentation online and already on your computer.  Try viewing the man page for chmod, chown, and chgrp.

Chris.

---

