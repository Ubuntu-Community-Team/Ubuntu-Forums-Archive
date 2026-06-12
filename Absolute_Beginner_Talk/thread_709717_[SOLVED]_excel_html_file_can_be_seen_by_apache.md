---
title: "[SOLVED] excel html file can be seen by apache?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Tambor on 2008-02-27
Hello, I'm also a new ubuntu/linux user and I'd like to put an excel file in HTML format accessible to my work group. I try to do it by apache2 but I only see "It works" and when I bring the index.html to www folder.
Is it possible, see an excel file (html format) using apache?

Thanks,

Tambor.

---

### Post by chris.a.barker on 2008-02-27
The only real thing to pay attention to is that you use the file extension .html and not .htm. By default MS Excel adds the .htm extension. By default apache is not directly set up to serve this file type. Place your file in /var/www/ then navigate to [http://localhost/filename.html](http://localhost/filename.html) and you should be good. Hope this helps.

---

### Post by Tambor on 2008-02-27
That's what I did, I changed the extension to html and using chmod I let it only read/write and it still doesn't appear in my localhost.
It works is ok...

---

### Post by chris.a.barker on 2008-02-27
So is it good or not? I don't quite follow you.

---

### Post by Tambor on 2008-02-27
When I type [http://localhost/filename.html](http://localhost/filename.html) this message appears:
**Forbidden**
You don't have permission to access /filename.html on this server
What could be?
Thanks!

---

### Post by Tambor on 2008-02-27
Sorry, I 'd like to say that "It works" (default message) appear when I type conect to my [http://localhost](http://localhost) . But when I try [http://localhost/filename.html](http://localhost/filename.html) , the Forbidden message appears.
Any idea?
Thanks.

---

### Post by nhandler on 2008-02-27
I'm not an expert on permissions, but a chmod 777 filename.html should get rid of the error. Someone who has more experience might be able to suggest a better permission setting. 777 is not secure. It enables everyone to read/write/execute the file, but it will make it viewable in apache.

---

### Post by Whiffle on 2008-02-27
It depends on the permissions of the file.  You could try chmod 777 on the file, and that would give permissions to anyone/everyone.  I don't know what the permissions should be though.

---

### Post by Tambor on 2008-02-27
Hello, thank all of you. I got the permissions using:
sudo chmod -R +rw *
Thanks again,
Tambor.

---

### Post by nhandler on 2008-02-27
> **Tambor said:**
> Hello, thank all of you. I got the permissions using:
sudo chmod -R +rw *
Thanks again,
Tambor.

Just a few notes and explanations (for anyone reading this thread at a later date)...

Unless the files are owned by root, you don't need to use "sudo".

chmod is used to change the permissions of a file

The -R tells it to be recursive. This means that it will change the permission of files inside subfolders of the the directory specifies at the end of the command.

+rw means give everyone (user,group,other) read and write privileges. The numerical equivalent would be chmod 666.

The * at the end is a wild card. It matches everything in the current directory.

---

