---
title: "[SOLVED] SUDO isn't working. I can't do Administrator stuff."
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by chrispche on 2007-11-03
SUDO Won't work if I type it I get:

sudo: unable to lookup ubuntu via gethostbyname()

I can't organise my user's in users and groups. I can't access synaptic. 

PLEASE HELP. I don't want to go through installing and downloading everything again.

There must be simple fix for this?

Anyone? I would appreciate a swift response.

Thanks.

---

### Post by teutori on 2007-11-03
Maybe this thread can give you the answer [http://ubuntuforums.org/showthread.php?t=188337](http://ubuntuforums.org/showthread.php?t=188337)

---

### Post by JAPrufrock on 2007-11-03
To reinstall sudo you can use synaptic or apt-get.  Of couse normally you can't use either without sudo.  Maybe you could try logging in as root. If you do that, you don't need to use sudo to open synaptic.  To log in as root see [ this link]("http://209.85.165.104/search?q=cache:ZKJCEgkYO7oJ:www.arsgeek.com/%3Fp%3D688+ubuntu+log+into+root+terminal&hl=en&ct=clnk&cd=5").

Oh yeah, I forgot: It seems like you're using Dapper, so I don't remember if you can use the applications menu to log in as root.  In Gutsy you can log in as root by going to and clicking  "Applications/System tools/Root terminal"

---

### Post by chrispche on 2007-11-03
I tried from recovery mode. nano ect/hosts entered 127.0.0.1 localhost.localdomain localhost ubuntu

Saved that and no changed. Still can't access SUDO.

---

### Post by qpieus on 2007-11-03
one time I accidentally removed myself from the admin group and that caused problems similar to yours (although I don't remember the "gethostbyname()" error).

To see what groups you are in, open up a terminal window and type```
groups
``` and post the results here. We're looking to see if you are in the admin group.

---

### Post by chrispche on 2007-11-03
Solved thank for the help everyone.

I edited hosts and added 127.0.0.1 localhost.localdomain localhost ubuntu

---

### Post by steve.horsley on 2007-11-03
Edit: Withdrawn cos you've already fixed it. That's what happens if you get distracted and take an hour to answer a post, I suppose.

---

