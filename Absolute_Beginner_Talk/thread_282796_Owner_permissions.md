---
title: "Owner permissions"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-10-23
When I try to edit a file and then save it, I get a message sayign that I don't have permission to do so, because I am not owner...or something similar. How can I fix this so I can make any changes I want?

Thanks :)

---

### Post by Ben Sprinkle on 2006-10-23
```

sudo su
gedit

```
Instead of gedit, use whatever program your using.

---

### Post by Jussi Kukkonen on 2006-10-23
Depends on the file... If it's a system file or a file that is "rightfully" owned by another user, you should use sudo (or gksudo for graphical apps) to run the editor:
```
sudo nano <filename>
```
If the file should be yours but for some reason it isn't, do
```
sudo chown <username>:<username> <filename>
```

---

### Post by spamzilla on 2006-10-23
Well I am the only user of my laptop so if there a way to make me the owner?

I'll try sudo chown <username>:<username> <filename>

Thanks guys :)

---

### Post by spamzilla on 2006-10-23
Hmm I am trying to edit the source.list file. In terminal I typed

sudo chown matt:matt source.list

And I get this response

bash: username: No such file or directory

What am I doing wrong?

---

### Post by CatKiller on 2006-10-23
Don't do that. A lot of system files need very specific owner and permissions. If you keep trying to change the owner of files that should be owned by root, you'll soon find out how quick an Ubuntu reinstall is.

Use sudo when you edit the file.

That is all.

---

### Post by jwdvd on 2006-10-23
is matt your actual username, also, did you "sudo su" first?

i would...

sudo su with your matt account password
browse to /etc/apt
vi sources.list

you will get access to the file as you are in as sudo.

---

### Post by monktbd on 2006-10-23
> **spamzilla said:**
> What am I doing wrong?

well you wrote the filename wrong and actually it was a good thing to do.
as CatKiller already mentioned you should NEVER change the permissions on files outside your home directory and your data partitions unless you very well know what you are doing. 
you can even break your system by doing so (for some files).

if you want to have an easy way of editing root owned files then try to install some nautilus scripts (search for that here on the forums). they will let you open a file from nautilus from the context menu with root rights (after entering the password of course).
or stick to the not much more time consuming 
> gksudo gedit /etc/apt/sources.list
from the command line :).

---

### Post by spamzilla on 2006-10-23
jwdvd: Yeah matt is my account username. Ok I'll try that, thanks a lot :)

monktbd: Oh ok thanks for the command line!!

---

### Post by Ben Sprinkle on 2006-10-23
> **synectics said:**
> ```

sudo su
gedit

```
Instead of gedit, use whatever program your using.

Just do:
```

sudo gedit /pathtofile
```
Is all.

---

### Post by bulldog on 2006-10-23
Don't use gedit you should use gksudo and for all graphical applications.

If you don't do that and use sudo,there will be a day you can't login anymore.

---

### Post by Ben Sprinkle on 2006-10-23
gksudo?
Why will there be a day where I can't login anymore only using sudo. I have been doing that since last october, that's a year. I have never had any problems like that. When new updates are out I dist-upgrade. :)

---

### Post by CatKiller on 2006-10-23
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Ben Sprinkle on 2006-10-23
Thanks.

---

