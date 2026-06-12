---
title: "Need an FTP client, and gFTP doesn't seem to be there."
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Kodiak3000 on 2006-08-08
I've tried "sudo apt-get install gftp" and I get 

"Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gftp"

:confused: 

I found out where I can download it, but I've downloaded all four versions available for deb and I get an error each time that says the dependency is not satisfyable.

Can anybody help? 

[-o< 

Thanks!

---

### Post by timhaughton on 2006-08-08
Hi, gftp is available. It might not be in the Main repository - have you enabled the others?

If not have a look here...

[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

Post back if you still have problems.

Cheers,

Tim

---

### Post by ciscosurfer on 2006-08-08
Enable your universe repository and then try again (all dependencies  will be met)```
sudo aptitude update && sudo aptitude install gftp
```

---

### Post by dmizer on 2006-08-08
if it's only a client you need, how about using nautilus?

click places > connect to server > enter ftp server information and shezam you're in.

---

### Post by Kodiak3000 on 2006-08-09
Tim,
What others?  urmph.  I'm new here, can you tell?

I took CiscoSurfer's advice an gFTP is there now, but I don't really understand what just happened...

Cheers

---

### Post by ciscosurfer on 2006-08-09
Kodiak3000, you enabled your universe repo, you updated your repo list by issuing an aptitude update, and then you downloaded gFTP through the universe repo that now sits happily in your repo list located at /etc/apt/sources.list ;)

Cheerio!

---

### Post by DJiNN on 2006-08-12
> **dmizer said:**
> if it's only a client you need, how about using nautilus?

click places > connect to server > enter ftp server information and shezam you're in.

Hey, dmizer..... thanks for that heads up..... been having trouble with gFtp & never even thought of using Nautilus..... just tried it & "Bang".... works great! :)  I know how i'll be doing ftp transfers from now on. 

DJiNN

---

