---
title: "xampp help"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by grezer on 2007-06-27
Hello all I am very new with Ubuntu and I am having some issues getting xampp working, I have setup xampp on a windows system with out any issues but I am getting a error when I try and set it up with Ubuntu Server 6.10. I try and unzip it to /opt file that xampps instructions state " sudo tar xamp-linux-1.6.2.tar.gx -C /opt and then I get this error


tar: xampp-linux-1.6.2.tar.gz: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 

I have made sure that there is a /opt file but, I am LOST .... HELP 

Thanks Grezer

---

### Post by mlentink on 2007-06-27
Errrr...
Question:
Why didn't you just download the Ubuntu sever-disk and use the install LAMP server option?
Does it all by itself...

---

### Post by xelnaga666 on 2007-06-27
Try changing to the directory with the file in and do a 

```

sudo tar xvfz xampp-linux-1.6.2.tar.gz -C /opt

```

EXACTLY LIKE THAT.

It should just unpack out to /opt/lampp

you can then start the services by issuing a

```

sudo /opt/lampp/lampp start

```

Hope this helps.

---

