---
title: "Remote file access and upload"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by dualityim on 2007-12-02
I'm trying to remotely access and upload files to my ubuntu computer from a windows computer across the internet. What's the best way to do this? I have openssh server, vnc, and samba file sharing enabled on my ubuntu system, but I'm not sure what tool to use on the windows end to access the file system. And for any particular tool, is there any ports that I need to forward on the router that the ubuntu system is hiding behind?

---

### Post by scrooge_74 on 2007-12-02
you can use something like putty plus a tunnel for your samba

[http://b-l-w.de/sambassh_en.php](http://b-l-w.de/sambassh_en.php)

---

### Post by Dr Small on 2007-12-02
> **scrooge_74 said:**
> you can use something like putty plus a tunnel for your samba

[http://b-l-w.de/sambassh_en.php](http://b-l-w.de/sambassh_en.php)
Cool. I didn't know you could do that :)

---

### Post by dualityim on 2007-12-02
That's pretty cool. Reading that article, this caught my eye too:

"You can of course work with an SSH-console (for Windows e.g. Putty) an transfer files via SCP or SFTP."

I'm trying to do this with Putty on my windows machine but it seems once I establish the ssh connection, I only have access to the remote system, not the local system. Is it possible to transfer files using the ssh console from Putty?

---

