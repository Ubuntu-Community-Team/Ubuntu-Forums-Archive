---
title: "Can I show contents of FTP server from a web page?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by fyl2u on 2007-05-16
Hi all,

I've set up my Ubuntu machine as an FTP server and also as an HTTP server.

I'd like to design a nice user interface to allow uploading and downloading to and from my FTP folders from a browser window, (so that clients don't have to think, or use 3rd party FTP software to receive files we "send" them).

Essentially, I want to be able to email a link and login details to a client, who can just click the link and be presented with a web page with our corporate logo and login section on it. After logging in, I'd like them to be able to see the contents of the FTP folder (still with our corporate logo and pretty design) and be able to download straight from there.

Can anyone instruct me in how to do this?

Thanks in advance.

I'm only 4 days in, but I'm loving Ubuntu more and more each day.

---

### Post by Rinzwind on 2007-05-16
Apache is a webserver. In combination with MySQL and PHP and excellent method to setup a dynamic webserver.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by fyl2u on 2007-05-16
> **Rinzwind said:**
> Apache is a webserver. In combination with MySQL and PHP and excellent method to setup a dynamic webserver.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Yup, I'm using apache2 already, and I've also got vsftpd set up.

Both servers are working over my intranet, but I need to know how the best way to ensure ease of download for the recipient.

We've recently found out that our clients can't use FTP client software and need a browser-based solution where they...
1. click a link, 
2. log in,
3. see the files/folders, 
4. click the files/folders, 
5. receive the files/folders on their machine.

I've got as far as that, but I need to make it look more attractive than just your standard "ftp folder view" that you get by directing a browser to the ftp folder by typing the "ftp://[numbers]" address in.

I've got a feeling I'd have to do this from a web-page, which I *can *code myself but I don't know how to show the files/folders (which will be changing constantly) from the ftp server in the web page.

---

### Post by raghav.dinesh on 2008-07-14
> **fyl2u said:**
> Hi all,

I've set up my Ubuntu machine as an FTP server and also as an HTTP server.

I'd like to design a nice user interface to allow uploading and downloading to and from my FTP folders from a browser window, (so that clients don't have to think, or use 3rd party FTP software to receive files we "send" them).

Essentially, I want to be able to email a link and login details to a client, who can just click the link and be presented with a web page with our corporate logo and login section on it. After logging in, I'd like them to be able to see the contents of the FTP folder (still with our corporate logo and pretty design) and be able to download straight from there.

Can anyone instruct me in how to do this?

Thanks in advance.

I'm only 4 days in, but I'm loving Ubuntu more and more each day.




hi dear,
i am also facing this problem.
if u know the solution please reply me.

---

