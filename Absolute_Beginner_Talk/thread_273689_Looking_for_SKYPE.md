---
title: "Looking for SKYPE"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-10-08
I have just installed Ubuntu 6.06.1 LTS from a DVD and thought I might find SKYPE in there somewhere.

Anyway, either I don't know what I'm doing, or I looked in the wrong place but I didn't find it.

I would appreciate it if someone would tell me whether its there and I missed, or should I download the Beta file that is on the SKYPE site?

Thanks.

Lewis.

*****

---

### Post by aysiu on 2006-10-08
Skype is closed source and will *never* be included in a default Ubuntu installation.

To install it, **[enable extra repositories](http://www.psychocats.net/ubuntu/sources)** and then paste this command in [**the terminal**](http://www.psychocats.net/ubuntu/terminal): ```
sudo aptitude update && sudo aptitude install skype
```

---

### Post by L Campbell on 2006-10-09
Hi, thanks for your help.

I looked in Help > Repositories > 4.2. and it shows an option to 'enable' but then which line show I 'enable'?

Kind regards.

Lewis.

*****

---

### Post by george29 on 2006-10-09
Check out the ubuntu guide wiki

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

it has loads of information for people new to ubuntu and explains how to add repostitories and install extra software etc etc.

george

---

### Post by aysiu on 2006-10-09
> **L Campbell said:**
> Hi, thanks for your help.

I looked in Help > Repositories > 4.2. and it shows an option to 'enable' but then which line show I 'enable'?

Kind regards.

Lewis.

*****
Just click the links in my last post.

---

### Post by L Campbell on 2006-10-10
> **aysiu said:**
> Just click the links in my last post.

Thanks for your continued interest.

I pasted this into my terminal(from the enabling Extra Reositories page):-

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

And it returned:-

(gedit:6619): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Also, a ' sources.list ' window appeared.

I'm not sure what to do with the data that is in that window.

Kind regards.

Lewis.

*****

---

### Post by gosh on 2006-10-10
Maybe this is easier for you:

Open Synaptic Package Manager.
Tab Settings->Repositories.
Then click Universe and Multiverse.
Close
Click reload
Search "skype"
Install!

---

### Post by L Campbell on 2006-10-10
> **L Campbell said:**
> Thanks for your continued interest.

I pasted this into my terminal(from the enabling Extra Reositories page):-

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

And it returned:-

(gedit:6619): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Also, a ' sources.list ' window appeared.

I'm not sure what to do with the data that is in that window.

Kind regards.

Lewis.

*****


Oops!!

After re-reading the information I found on your great links, I pasted the recommended information into the ' sources.list ' page.

Should I now be able to find SKYPE?

Kind regards.

---

### Post by Rule on 2006-10-10
if you still cant find skype here is the link to download it from the skype website.

[http://www.skype.com/go/getskype-linux-deb]("http://www.skype.com/go/getskype-linux-deb")

---

### Post by L Campbell on 2006-10-10
[QUOTE=L Campbell;1594355]I have just installed Ubuntu 6.06.1 LTS from a DVD and thought I might find SKYPE in there somewhere.

Anyway, either I don't know what I'm doing, or I looked in the wrong place but I didn't find it.

I would appreciate it if someone would tell me whether its there and I missed, or should I download the Beta file that is on the SKYPE site?

Thanks.

.........................................

I want to thank everyone for their help here.

Although I don't think I could explain clearly to someone just what I did, SKYPE is now up and running, without any quirks, as far as I can tell.

Kind regards.

---

### Post by LookTJ on 2006-10-10
```
sudo aptitude install skype
```

type that in terminal

---

