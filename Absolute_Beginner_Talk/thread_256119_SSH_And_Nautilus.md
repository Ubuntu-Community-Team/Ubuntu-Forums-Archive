---
title: "SSH And Nautilus"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Maverick321 on 2006-09-12
I am having a problem using nautilus and ssh to view files on a remote computer, It does ask for the password but when I enter said password it returns "Nautilus cannot display "ssh://192.168.0.201" Please select another viewer and try again."

I then tryed to use sshfs to mout the file system, it also askes for password and then tells me that remote host disconnected,  is there some setting that i need to change?

I was using Nautilus with ssh a couple of days ago and just stop working last night. I tryed to remove the ssh client and server off of both computers and reinstalled to try to start over but still getting the same errors.

But i can ssh in and login to get a command promt and use scp but useing a gui is much faster.

Is there some kind of setting that i am overlooking or is something broken?

---

### Post by junglepeanut on 2006-09-12
Augh, I knew I shouldn't but I did ran nautilus from inside xfce now I need to reset settings. 

But to give some help to you, I can confirm that nautilus is still able to connect remotely to remote computers.

Is the ip static? Otherwise maybe it reset...nevermind I just saw that it looks like you were connecting to something on your network. hmm, did the router assign it a new address?

I guess the only information I can give you is that it is not broken. Although I am logging into a pc many miles away. Not through local network.

---

### Post by Maverick321 on 2006-09-12
The server is useing a static ip and Nautilus can still browse the samaba shares that I have.  Both the samaba server and the ssh server is on the same computer.

And i dont usually connect from the LAN, ususally from school or girlfriends house, just for a central location for file storage.

---

### Post by steve.horsley on 2006-09-12
Two points:

Before you can use SSH from Nautilus, you must tell SSH that the server you are connecting to is approved. The first time you ever connect, do it through the command line like this:
**ssh username@servername**
and SSH will ask some inane question like "are you sure this is the server you want to talk to", as though you would know if it wasn't! So you answer yes, and then it adds that server's ID to its list of known hosts. After this, Nautilus can connct. You don't see the question ever again. The problem here is that Nautilus can't ask the question if it's First Contact.

I have only ever used "sftp://user@host" from inside nautilus. Maybe "ssh://user@server.host" just isn't the right words.

---

### Post by Maverick321 on 2006-09-13
I have done the connect just using ssh [email]user@server.com[/email] and accepted the key.

I follow the information on this page [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

And It was working for a couple of weeks, but not any more.

---

### Post by junglepeanut on 2006-09-16
If you are connecting to many different computers, I don't know why this happens, but you may experience keys just changing, so that you can not log into one anymore and you get that "YOu are evil and being watched response" lol. 

I have not needed to cli into ssh from Nautilus before, but maybe I just did it with out knowing. 

If you dont mind resetting all your keyes you could just "reset" them all by removing the drectory in your home folder .ssh

```
rm -r .ssh
```

Warning I am very new, and this works for me, so I do not know if this is the recommended method.

Jp

---

### Post by Maverick321 on 2006-09-17
I found out it had to something to do with the paths that were being set on the server when i was loging in, i just corrected the $PATH enviroment variables and problems disappeared.

---

### Post by nyinge on 2006-09-17
> **Maverick321 said:**
> I found out it had to something to do with the paths that were being set on the server when i was loging in, i just corrected the $PATH enviroment variables and problems disappeared.
May I know what you edited specifically in the $PATH?

---

### Post by Maverick321 on 2006-09-17
> **nyinge said:**
> May I know what you edited specifically in the $PATH?

I copied the paths that were being set on my laptop, over to the server. The server only had /bin, maybe more i cant remember.  But i belive the problem was it didnt have a path to /usr/bin/X11.

In any case the current $PATH is set to /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

---

### Post by WorLord on 2007-05-20
> **junglepeanut said:**
> If you dont mind resetting all your keyes you could just "reset" them all by removing the drectory in your home folder .ssh

```
rm -r .ssh
```

Warning I am very new, and this works for me, so I do not know if this is the recommended method.

Actually, I'd recommend *moving* .ssh to .sshold or something, in case you need that data.

At any rate, I did this and Nautilus started to behave again.  So its all good.

---

