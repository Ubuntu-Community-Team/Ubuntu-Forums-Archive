---
title: "Ways to run programs on a server"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by oni5115 on 2007-09-05
I'm wondering what methods exist to run different applications through a server.  What I am trying to do is setup a test webserver, but still be able to edit the files from other computers.  (Since I am not the only one editing them.)

I also want to be able to the ftp program from the server, to upload the websites to the actual live webservers.  I'm curious of the various methods this could be completed on various boxes.  The server is Ubuntu LAMP server dapper drake.  The other boxes are windows XP.  I also have an additional Ubuntu Feisty Fawn computer I could use as well.

I'm still rather new to linux and ubuntu.  I've never really tried to run apps on a server like this, aside from webservers.  So it's a learning process.  Any help getting started is greatly appreciated.

---

### Post by HermanAB on 2007-09-06
One word: SSH

I always run SSH on a non-standard port so my login looks like this:
ssh -X -c blowfish -p 2222 username@servername

and then I can run anything.

Cheers,

H.

---

### Post by oni5115 on 2007-09-06
And you can connect to it with windows as well?  Or do you need some special software?  Are there any good guides?  I'll do some searching of the forums too I guess.  Thanks for a place to start.  =)

---

### Post by hyper_ch on 2007-09-06
You can connect with windows using Putty to get into the terminal: [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Or you can use WinSCP to sort of have a "FTP" File Manager:
[http://www.winscp.com/](http://www.winscp.com/)

For both things you use SSH and you need to assign the special port if you set one...

However I still wonder why do people change the port? Changing it does not provide any security IMHO as normally people will scan the whole port range...

And installing SSH on your server/computer is very easy:

```

sudo apt-get install openssh-server

```

You can then login using your normal system user.

---

