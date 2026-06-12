---
title: "How do I execute the Faster-Dapper script?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by plague27 on 2006-08-07
I got faster-dapper, a script which automatically configures ubuntu to run a little faster, and cannot figure out how to run it. It is saved as so....

/home/usr/desktop/faster-dapper.sh

How do I execute the script?

It seems that the really, really basic questions are really hard to find answers to. I have searched to no avail.

---

### Post by AirRaven on 2006-08-07
You can do it in GNOME by right clicking on it, going to Properties->Permissions, then setting it to be executable. 

Alternatively, try just going into the terminal and running this:

```
.//home/usr/desktop/faster-dapper.sh
```

---

### Post by greybirds on 2006-08-07
What AirRaven said :)

If you do it in a terminal, you have to do the GNOME bit first or set it to be executable first with this command:

```
chmod +x /home/usr/desktop/faster-dapper.sh
```

Also, if you're into terminals, execute it with:

```
/home/usr/desktop/faster-dapper.sh
```

---

### Post by raja on 2006-08-13
> **plague27 said:**
> I got faster-dapper, a script which automatically configures ubuntu to run a little faster, and cannot figure out how to run it. It is saved as so....

/home/usr/desktop/faster-dapper.sh

How do I execute the script?



faster-dapper is a shell script that need you to be sudo to execute. That means typing
```
 cd /home/usr/desktop
sudo ./faster-dapper.sh
```
It is also better to look at the script before you run it. There are portions to comment out if you are using a laptop or if you need dial up etc. You can do that for example with
```
gedit /home/usr/desktop/faster-dapper.sh
```
Hope that helps !

---

