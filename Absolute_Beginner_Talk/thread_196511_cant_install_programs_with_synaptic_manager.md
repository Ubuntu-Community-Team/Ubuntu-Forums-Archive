---
title: "cant install programs with synaptic manager"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-06-14
When i mark stuff for installation with synaptic package manager and apply changes a message box is displayed saying [COLOR="SeaGreen"]downloading 1 of 5 [/COLOR]or whatever etc.. but it always times out and the packages never get installed.
do i need to configure something for this method of softwaer installation to work?

---

### Post by taurus on 2006-06-14
There is an option in the downloading window that you can click to see which package synaptic is trying to download and from what site!  It could be the site is down right now.  Otherwise, you can always install it from a terminal using apt-get...
```

sudo apt-get install <package_name>

```

---

### Post by meniscus on 2006-06-14
I did but im getting this error?


[COLOR="Red"]meniscus@ubuntu:~$ sudo apt-get install libcurl
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
meniscus@ubuntu:~$
[/COLOR]

Do you know what this process might be?

---

### Post by not_yet on 2006-06-14
looks like you have something else running as root

thats why you are getting the "can't get a lock"

do you have the terminal open as root?

---

### Post by meniscus on 2006-06-14
oops! yes thats it...thanks

---

