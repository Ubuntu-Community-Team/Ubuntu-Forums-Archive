---
title: "changing permissions?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by andocommando on 2006-09-04
When I try to copy or move a file or folder to directories other than my user folder (using the file browser) I get this,

> Error while copying to "/usr/share/amsn/skins".

You do not have permissions to write to this folder.

This is on the only account, the one I set up with during installation. Thanks for any help.

---

### Post by Paul133 on 2006-09-04
Did you create that folder? IF so, you should have writing permission. But, try ```
 cd /usr/share/amsn 
``` and then ```
 ls -l 
``` and post what comes up in the terminal.

---

### Post by aysiu on 2006-09-04
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Paul133 on 2006-09-04
Aysiu, this is off topic but u can't get PM's so here's my problem:
 
How did you get those links in your sig? I tried with my rudimentary HTML knowledge <A href="http://www.psychocats.net/essays/linuxdesktopmyth">The Linux Desktop Myth</A> but it doesn't seem to work.](*,)

---

### Post by aysiu on 2006-09-04
> **Paul133 said:**
> Aysiu, this is off topic but u can't get PM's so here's my problem:
 
How did you get those links in your sig? I tried with my rudimentary HTML knowledge <A href="http://www.psychocats.net/essays/linuxdesktopmyth">The Linux Desktop Myth</A> but it doesn't seem to work.](*,)
It's not HTML--it's BB code.

Take out the extra spaces in this code: [ u r l = h  t  t p://w ww.psychocats.net/essays/linuxdesktopmyth] The Linux Desktop Myth [ / u r l ]

More info here:
[http://www.bbcode.org/](http://www.bbcode.org/)

---

### Post by grte on 2006-09-05
You don't want to change permissions on /usr/share.

Instead, try appending the command sudo in front of the command you are using, which will give you administrative privileges, allowing you to move the files.

Fr'ex,

sudo mv /home/avatar/moveme /usr/share/movemehere

Alternately, you can use the command
```
gksudo nautilus
``` 
to open the file-browser with administrative privileges, which will allow you to drag and drop whatever you want whereever you want.  Use with caution.

---

### Post by Paul133 on 2006-09-05
Thanks, aysiu. I did the BBcode and it works on, though it doesn't seem to apply retroactively like my avatar did. At any rate, thank you for everything. I feel that you've really helped me while I've been learning how to install Ubuntu, along with other forum members, which is why put your Linux site and essay on the Linux Desktop Myth in my sig.

---

