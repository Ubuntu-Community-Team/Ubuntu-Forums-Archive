---
title: "FTP problem: expected folders not showing up"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Trindol on 2008-01-07
I am trying to use "connect to server" to connect to my school's FTP and upload files to my webpage. The folder I am looking for is there "www", however the contents of that folder are not what I put in there.

When I look at this folder using windows/IE on a different computer it shows my webpage files. However when I ftp using ubuntu, there are many different folders and files showing up. I think it has to do with the fact that the school uses a UNIX based host? I am seeing unix type folders that I don't see with windows/IE.

It seems as if when I use ubuntu it is not recognizing that I am a "private user", and is only showing me the public folders. However ubuntu does ask for my username and password.

---

### Post by p_quarles on 2008-01-07
Which FTP clients are you using for Windows and Ubuntu, respectively? I ask because it might make sense here to use a client that works on both OSes (Filezilla) and see if it still behaves any differently.

---

### Post by Trindol on 2008-01-07
I did not use any specific program on either OS. I just chose connect to server in ubuntu and in IE I just typed username@address

---

### Post by p_quarles on 2008-01-07
Well, then, try Filezilla with both OSes, and see if you get different results. If you *do*, then the problem is likely with the software you were using. If you get the same results, that points to the problem being with the FTP server.

Filezilla for Windows:
[http://filezilla-project.org/download.php](http://filezilla-project.org/download.php)

Filezilla for Ubuntu:
Open a terminal and type:
```
sudo apt-get install filezilla
```

---

### Post by Trindol on 2008-01-07
I tried using firefox and it worked.

in firefox I typed "ftp://username@server.edu/www" and it asked for my password, and showed me the correct folder.

This also worked in Opera.

But that doesn't work in Nautilus and it seems like it should.

---

### Post by Syndacate on 2008-01-07
I had the same problem, and no, it doesn't work in nautalius.

I overcame the problem by going into Konsole >>

```

sftp user@server.edu

```

Then it'll prompt you for a password, so on and so forth.

"get" to upload
"put" to download

ie.

```

> get index.html

```

Or

```

> put /home/user/Desktop/index.html /var/www/

```

---

### Post by Trindol on 2008-01-07
That worked thank you.

It showed me something interesting though.

"ftp://username@server.edu/www" works in opera and IE and firefox.

however I did a pwd while in the terminal after I logged in and it showed my location as "/users/rit3/g0/username/myusername/www"

So apparently this is the "real" location of my files? When I use this folder in Nautilus it works, so...

---

