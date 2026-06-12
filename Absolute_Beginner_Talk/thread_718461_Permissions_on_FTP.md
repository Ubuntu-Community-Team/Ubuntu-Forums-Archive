---
title: "Permissions on FTP"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2008-03-08
I'm starting a website, but it's with my friend. It's run off my Ubuntu 7.10 box using Apache. But I want him to be able to download files, upload files, and edit files in that directory. I was thinking set up an FTP Server. Only problem is it's a /var/www directory. Short version of questions...how can I set permissions so he will be able to access the directory without opening my website to anyone with a basic knowledge of linux who happens across it?

Edit: I  just realized... If I'm running the FTP server off my login, will it be registered as me making the changes if my friend uses the FTP? If that's the case...I won't need to change permissions. Just let me know.

---

### Post by .nedberg on 2008-03-08
If he logs in with your username and password it will be just like you did it and files will get whatever permission you would get locally.

---

### Post by TekMuzik on 2008-03-08
Well..I'm going to set his own username & password on the FTP server. But the FTP server will be running while signed in to my username and password. So it will see any actions performed on FTP as performed by my username right?

---

### Post by .nedberg on 2008-03-08
OK, I misunderstood you then.

If you run vsftpd it can use virtual users. These are users who are mapped to a local user account, but different name and password. You might try that if it doesn't work the way you want it to.

---

