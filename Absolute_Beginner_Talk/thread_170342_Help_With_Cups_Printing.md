---
title: "Help With Cups Printing"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by macqst on 2006-05-04
Hello Everyone,

I hope I am posting this in the correct area. I couldn't find a strictly Xubuntu forum. Please excuse me if this isn't in the correct place.

I am very new to Linux. I have played around with the various distros and have found that I most like using Xubuntu.  Everything installed easily but I can't seem to get cups to work. I have been unable to find clear documentation for implementing. I have gotten as far [administration pages@cups] when it asks for password. I enter my root password/user name as requested and it keeps asking me again. I guess it is implying that I am using a wrong password? I am using my correct one. Are there any easy instructions posted anywhere? Googling found me no sucess. Thanks in advance....

HP Photosmart 2610 [ I found that HP2600 works on previous distros]
Sony Vaio 
Xubuntu [latest build]

PS. I wish I would have done this earlier. Really cool stuff.:D

---

### Post by Haegin on 2006-05-04
Yeah - it sucks - the admin pages (localhost:631) are disabled by default on ubuntu. To re-enable them enter the following in a terminal:
```

sudo nano /etc/groups

```
Then add the following line to the end of the file
```

shadow:x:42:cupsys

```
Then press CTRL and O to save (press y when it asks) then CTRL and X to quit nano (useful lil text editor).
Now at the terminal enter:
```

sudo /etc/init.d/cupsys restart

```
Then at the terminal again:
```

sudo passwd cupsys

```
And enter a password for the user "cupsys".
Then enter
```

lppasswd

```
And set the password (use the same password as you did for the previous command)
Next try logging in to the printer pages ([http://localhost:631](http://localhost:631)) as cupsys with the password you set.

Tell me if this works - I have a feeling it may need some modification...

---

### Post by macqst on 2006-05-04
[QUOTE=Human Prototype]Yeah - it sucks - the admin pages (localhost:631) are disabled by default on ubuntu. To re-enable them enter the following in a terminal:
```

sudo nano /etc/groups

```
Then add the following line to the end of the file
```

shadow:x:42:cupsys

```
Then press CTRL and O to save (press y when it asks) then CTRL and X to quit nano (useful lil text editor).
Now at the terminal enter:
```

sudo /etc/init.d/cupsys restart

```
Then at the terminal again:
```

sudo passwd cupsys

```
And enter a password for the user "cupsys".
Then enter
```

lppasswd

```
And set the password (use the same password as you did for the previous command)
Next try logging in to the printer pages ([http://localhost:631](http://localhost:631)) as cupsys with the password you set.

Tell me if this works - I have a feeling it may need some modification...[/QUOTE]

Thanks for responding..

after entering "lppasswd"

I get: 

"lppasswd: user "macqst" and group "lp" do not exist.
lppasswd: Password file not updated!


***I also noticed when I opened "/etc/groups" there was nothing else in the file. I downloaded the latest version of Xubuntu and used cups as is. Do you have to configure something else first ?

BTW...I checked out your site. Very nice. 

Thanks again. The kindness of people that use Linux is very cool.

---

### Post by skippy81 on 2006-05-04
You can get in another way, which is simpler but not the best from a security perspective:-

1) You need to edit /etc/cups/cupsd.conf file. Find the line "RunAsUser Yes" and change it to "RunAsUser No".  You can edit the file quickly by opening a terminal and typing > RunAsUser No

2) Next you need to set the root password.  Make sure you use something complicated like fisH957eGg388 :p.  To do this use a terminal again:

> sudo passwd root

3) Now when you access [http://localhost:631/admin]("http://localhost:631/admin") you can enter a username of "root" and a password of what you set the *root* password to.

I think it's good to have the root password set up at some point, just dont get into the habit of logging in with it every day.

---

