---
title: "sbackup problem"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by rmstone1s on 2007-09-13
I'm trying to setup sbackup to backup several directories to a web server...

So i use my ftp string:

[ftp://myusername@rmstone.net:mypassword@rmstone.net/backup/](ftp://myusername@rmstone.net:mypassword@rmstone.net/backup/)

And to no avail... i click test and it says the selected destination is not writable with current permissions.  The backup cannot be written there.

Whats going on here?

A couple things
1. I do put in my real username and password into the string in place of myusername and mypassword but for obviously reasons left them out here :)

2. yes my username for ftp is "something@rmstone.net".. is that causing a bug because of the extra @ sign?

3. if i take the string i use and put it into firefox, it immediately logs into ftp and takes me to the backup directory. So i think i have everything correct.

Any ideas?

---

### Post by CaptainInsaneO on 2007-09-13
ftp is a protocol and I don't think sbackup supports protocols like that.

You could try mounting it as a network drive and give your user account write permissions to it and then try pointing sbackup to the mount. I've never seen this kind of set up (with an ftp server) for sbackup so I'm throwing stuff out there to stimulate your creativity. :razz:

---

### Post by rmstone1s on 2007-09-13
Actually sbackup specifically says that it does support SSH and FTP...

---

### Post by Bothered on 2007-09-13
Have you tried putting in an extra @? As in:

[ftp://usename](ftp://usename)[including @]: password@address

---

### Post by CaptainInsaneO on 2007-09-13
> **rmstone1s said:**
> Actually sbackup specifically says that it does support SSH and FTP...

Right you are! I wasn't sitting at my Ubuntu box when I wrote that so I wasn't completely sure, but I see it now.

---

### Post by rmstone1s on 2007-09-16
> **Bothered said:**
> Have you tried putting in an extra @? As in:

[ftp://usename](ftp://usename)[including @]: password@address

Yes I did try it with the @ sign... thats my full username and the only way i can get logged in... i actually tried using another ftp account that doesnt have the @ and no luck there either... has anyone actually made the ftp support for sbackup work?

---

### Post by Bothered on 2007-09-16
I don't think you understood. I think sbackup might want there to be an @ between the username and the address. i.e. in your case:

[ftp://myusername@rmstone.net:mypassw](ftp://myusername@rmstone.net:mypassw)...**@**ne.net/backup/

---

### Post by rmstone1s on 2007-09-16
I don't think I'm getting it... it doesnt help that the forum is cutting up the URLs... but what i used is:

ftp://  myusername (AT) rmstone.net : mypassword (AT) rmstone.net /backup/

So I'm using two @s, where else do you want me to try putting one?

---

### Post by CaptainInsaneO on 2007-09-16
Try this:

```
ftp://your-username:your-password@rmstone.net/backup/
```

---

### Post by rmstone1s on 2007-09-16
Ok we're not getting anywhere here... that IS what i'm using...

My username is:    [email]my-username@rmstone.net[/email]  (my server assigns usernames with the @rmstone.net in it... so thats my FULL username)

Ie to login i would put in:
username: [email]my-user@rmstone.net[/email]
pass: my-pass

So to do

ftp:// your-username : your-password @ rmstone.net /backup

it is

ftp:// [email]my-username@rmstone.net[/email] : my-password @ rmstone.net /backup

Which is what I'm trying and what i put in my original post...

I appreciate the help but I think we're all confusing each other :)

---

### Post by CaptainInsaneO on 2007-09-16
```
ftp://my-username@rmstone.net:my-password@rmstone.net/backup
```

is not a valid ftp string.

One more thing that might be the problem: if rmstone.net is actually the web server you're trying to backup to, that domain has expired.

---

### Post by rmstone1s on 2007-09-17
Well when i take that string and throw it into my browser I get connected to my ftp box... 

How do I create a valid ftp string for that server then?  

Thanks for heads up on the domain, must not have it set to auto renew....

---

### Post by CaptainInsaneO on 2007-09-17
Have you tried what I said earlier?

```
ftp://login:password@rmstone.net/backup/
```

and are you still able to get into that server? If it's expired you might not be authorized on it anymore...

---

### Post by rmstone1s on 2007-09-17
Yes I tried that... i just said that i tried that... am I missing something here?  I have tried putting my username and password into that string... my username is: 'something@rmstone.net'  and thats what I'm putting in, thats what I said I was putting in in the first post and thats what i've said all along... i'm using the username:password@server.net format.

I know it wont work now that the domain expired but that happened yesterday so that wasnt the problem before.

---

### Post by CaptainInsaneO on 2007-09-17
I have no idea then.

---

### Post by Bothered on 2007-09-17
I see, I had misunderstood. I am also at a loss now :confused:

The only other thing I can think of is to check /etc/sbackup.conf to make sure the GUI is saving the target correctly.

---

### Post by keptang on 2007-10-22
> **Bothered said:**
> I see, I had misunderstood. I am also at a loss now :confused:

The only other thing I can think of is to check /etc/sbackup.conf to make sure the GUI is saving the target correctly.

Did you get this to work?

I just tried it and the following works for me:
[ftp://username:password@ftp.ftphost.com/mybackupdir/](ftp://username:password@ftp.ftphost.com/mybackupdir/)

---

