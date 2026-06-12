---
title: "it wont install"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Terrapin77 on 2006-07-01
I tried to install a version metasploit framework but it wont let me. I tried the following:  

sudo xvzf framework-2.6-snapshot.tar.gz 
                         and also
$ tar -xvzf framework-2.6-snapshot.tar.gz

For some reason it will not work.  Any ideas as to why?

I already read [How to install ***_Anything***_ in Ubuntu](http://monkeyblog.org/ubuntu/installing/)  and the methods there didn't work either.     #-o

---

### Post by jorn on 2006-07-01
Try to rightklick the file and choose extract. I can't remember the sudocommand.

---

### Post by Terrapin77 on 2006-07-01
I do not know how to do it that way.  I clicked extract and know I am lost.

---

### Post by macdo on 2006-07-01
```
sudo tar -xvvzf framework-2.6-snapshot.tar.gz /home/user/framework
```
where /home/user/framework is a previously created directory.

---

### Post by Terrapin77 on 2006-07-01
tar: framework-2.6-snapshot.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /home/user/framework: Not found in archive
tar: Error exit delayed from previous error

I need to go back to windows but I do not have an installation disk

---

### Post by Terrapin77 on 2006-07-01
Ok I got it to extract using terminal (I think).  It is still not installed.  I am stuck here now.

---

### Post by jorn on 2006-07-01
If you download the file to your Desktop, rightclick, extract here, there come up adirectory called framework-2.6.
Leftclick it an the filebrowser opens. Here you open the uderdirectory called docs. Here is a userguide.pdf that might help you. A bit difficult in my point of view.
Make sure acroread installed.

---

### Post by Terrapin77 on 2006-07-01
THe userguide doesn't help.  I have it extracted but do not know where to go from there.  I need to install it and put it in a sub directory called ./framework-2.6 ...  I do not know how ot do that.

---

### Post by 3rdalbum on 2006-07-01
I don't know what it is you're trying to install, but the subdirectory will be called "framework-2.6", not "./framework-2.6".

Do you really need it installed right now? If you wait a little while to get familiar with the operating system and the way it works, in a few months time you'll be an absolute whizz at installing software.

---

### Post by macdo on 2006-07-01
It's extracted, right? 
So open the file called INSTALL (or README), and post the contents.

---

