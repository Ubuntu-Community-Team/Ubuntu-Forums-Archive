---
title: "problems with UPDATE to Firefox 1.50"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-15
A previous Thread suggested using URL  to update Firefox 1.50  

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
	
Default Re: How to install Firefox
Install guide for Firefox 1.5 : [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
1.5 is not in the repositoriies.

Backup your profile with:
```
cp -R ~/.mozilla ~/.mozilla.backup.1500
```


Close Firefox, give your user (yourself) file ownership: sudo chown -R ${USER}:${USER} /opt/firefox Start Firefox normally and update (Help -> Check for updates...) Once the update is completed, close Firefox and than restore ownership to root: sudo chown -R root:root /opt/firefox Again, do NOT browse other sites while firefox has these elevated permissions, that is without changing back the ownership of /opt/firefox over to root. Such a practice is not safe.

When I try to change ownership I get error message.

UPDATE CODE LOOKS sooooo simple

I must be doing something wrong but I do not know what it is.

---

### Post by kent41 on 2006-02-15
The previous reply would not let me show this error.
 WHY ?

kent@n01:~$ sudo chown -R ${USER}:${USER} /opt/firefox
chown: cannot access `/opt/firefox': No such file or directory

---

### Post by kent41 on 2006-02-16
************* Good news ***********************

   I have installed Firefox Ver.  1.5.0 and all seems to work ok except I have to use a terminal to start  Firefox now.

Is there some way to provide a button to start Fire fox like I had with the old version.\\:D/ 

 Firefox 1.5 seems very fast now. 

thanks for any help you could provide.

---

### Post by bartbes on 2006-02-16
if the executable in /opt/firefox is called firefox (which is most likely) do:
```

cd /opt/firefox
sudo ln firefox /usr/bin/firefox

```
and change your starter (you can do that with o.a. smeg) to firefox (now it's mozilla-firefox)

---

### Post by kent41 on 2006-02-16
> 
if the executable in /opt/firefox is called firefox (which is most likely) do:
Code:

```
cd /opt/firefox 
sudo ln firefox /usr/bin/firefox
```

and change your starter (you can do that with o.a. smeg) to firefox (now it's mozilla-firefox)

I tried this but I got this error.

[B]ln: creating hard link `/user/bin/firefox' to `firefox': No such file or directory
[/B]
I am so new I do not know what an executable looks like.  
Also what is o.a. smeg ?
What does firefox exe look like ?
Help
Thanks.

---

### Post by kent41 on 2006-02-16
If I use a terminal session and just type in Firefox the browser starts.
How do I create a button on the top tool bar of Ubuntu. There was such a button for the last version of Firefox


I tried the code below again and this time the error message said file already exist.
Code:
```

cd /opt/firefox 
sudo ln firefox /usr/bin/firefox

```


Thanks for any help

---

### Post by bluevoodoo1 on 2006-02-16
[QUOTE=kent41]If I use a terminal session and just type in Firefox the browser starts.
How do I create a button on the top tool bar of Ubuntu. There was such a button for the last version of Firefox


I tried the code below again and this time the error message said file already exist.
Code:
```

cd /opt/firefox 
sudo ln firefox /usr/bin/firefox

```

Thanks for any help[/QUOTE]

You're asking how to make a launcher from the toolbar correct? Right click on the toolbar > add to panel  then application launcher (and find it from your menus) or select custom application launcher and write "firefox" as command. Leave type as Application. From there you can change the name/comment/icon to whatever you like.

---

### Post by kent41 on 2006-02-16
\\:D/ \\:D/ 
\\:D/ 

\\:D/     Problem solved

 Great instructions on how to get Firefox on the tool bar.

Is is so nice to have the world as a knowledge base to solve Ubuntu challenges.

Thank you  for helping a noob.

---

