---
title: "How to allow write access to /var/www?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-09-28
I want to allow myself access on ubuntu (my account), to put files amd folders into /var/www, when i drag and drop files folders into it it comes up with some error saying i dont have access. :(

---

### Post by Average Joe on 2006-09-28
> **Josh1 said:**
> I want to allow myself access on ubuntu (my account), to put files amd folders into /var/www, when i drag and drop files folders into it it comes up with some error saying i dont have access. :(

Try:

```
sudo chmod 777 /var/www
```

That gives everybody read and write access to that folder. For safety reasons it is not really recommended though, especially where you are running a real server.

It is probably better to do:

```
gksudo nautilus
```

And drag and drop the files you want in /var/www (as root).

---

### Post by Josh1 on 2006-09-28
```
gksudo nautilus
```
Did it for me, thank you very much :D.

---

### Post by LookTJ on 2006-09-28
> **Josh1 said:**
> ```
gksudo nautilus
```
Did it for me, thank you very much :D.

but be very careful with that, if you delete some important files you'll install ubuntu again

Have fun.

~Taylor

---

### Post by indytim on 2006-09-28
The approach I used was to grant myself ownership of /var/www . I used:

```
$ sudo chown <userid> /var/www
$ sudo chgrp <userid> /var/www
```

I think this is a safer approach rather than opening the directory to the world.

Hope this helps.

IndyTim

---

### Post by Average Joe on 2006-09-28
Indytim, I totally agree.

Personally, I changed to RootDirectory of my Apache server to a directory in my own home directory. I since only run the server only for development purposes as localhost, I find that more convenient.

---

### Post by Ayman on 2006-09-28
If the userdir module for apache is enabled (which seems the case for Dapper), create a directory called public_html in your home, and apache will serve its files at:
http://localhost/~yourusername

---

### Post by f1sh3r on 2006-10-31
> **indytim said:**
> The approach I used was to grant myself ownership of /var/www . I used:

```
$ sudo chown <userid> /var/www
$ sudo chgrp <userid> /var/www
```

I think this is a safer approach rather than opening the directory to the world.

Hope this helps.

IndyTim

i did this, but i keep getting 

```

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/f1sh3r/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

whats the deal. i want to be able to drop files in here. i want apache to spit them out. this is angering me.

---

