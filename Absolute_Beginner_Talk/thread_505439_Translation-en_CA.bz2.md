---
title: "Translation-en_CA.bz2"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Malechai on 2007-07-20
Hello.. I'm hoping someone can help me with this.  This is my first time with Linux.  The install and everything has gone pretty smooth and I'm impressed!

Anyways my issue is this - upon attempting to update the system with "Update Manager", I get a "Could not download all repository indexes" message with the following in it:

> [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Error reading from server - read (104 Connection reset by peer)
[http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2:) Error reading from server - read (104 Connection reset by peer)
[http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_CA.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_CA.bz2:) Error reading from server - read (104 Connection reset by peer)
[http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Error reading from server - read (104 Connection reset by peer)
[http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_CA.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_CA.bz2:) Error reading from server - read (104 Connection reset by peer)
[http://ca.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) Error reading from server - read (104 Connection reset by peer)
[http://ca.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_CA.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_CA.bz2:) Error reading from server - read (104 Connection reset by peer)
[http://ca.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_CA.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_CA.bz2:) Error reading from server - read (104 Connection reset by peer)

I've tried searching on this forum and found 2 other threads mentioning this same file but they're a little old and the offered solutions (change to main server, etc) in those threads didn't fix the problem.  I've tried manually browsing to those directories with Firefox and that "Translation-en_CA.bz2" doesn't appear to exist.

Is this file important?  There were a ton of updates for Ubuntu that Update Manager still grabbed successfully and updated but this dialog comes up every time Update Manager is run and its annoying.  Is there some way to tell it to ignore trying to grab this file?

Also, another question now that I think about it....

When running Update Manager and giving it permission to install the updates it found, another dialog came up with a warning telling me that some of the updates could not be authenticated.  Is that normal?  Seems strange to me that the system update software is giving warnings about the critical updates it says I need?

Thanks for your time!

Ryan

---

### Post by deadgobby on 2007-07-20
If you click on a links or URL  from what you posted you'll get

The requested URL /ubuntu/dists/feisty/Release.gpg: was not found on this server.

Apache/1.3.26 Server at gulus.USherbrooke.ca Port 80

 It is really says it all.

---

### Post by Malechai on 2007-07-20
Hi there, thanks for the reply. Yes I said that it didn't exist in my first post, but that wasn't my question :)

Anyone else? Much appreciated.

---

### Post by deadgobby on 2007-07-20
So to stop it you'll need to edit your sources list 
gksudo gedit /etc/apt/sources.list
 Put two pound symbols before the line or delete it. So example
##[http://ca.archive.ubuntu.com/ubuntu/...y/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/...y/Release.gpg:)
 This will tell the system to ignore the line. After editing the list. Do your up date.
Gobby

---

### Post by Malechai on 2007-07-20
Thanks again for your reply :)

I assume I had to run that command from the terminal?  I did so and the line you said to place 2 ## in front of didn't exist.  I tried adding it to the file but I still receive the error messages.

Also.. any comments regarding the authentication warning dialog?

---

### Post by deadgobby on 2007-07-20
Please post your sources list
 Here is a better reason why too why the link will not work
[http://ca.archive.ubuntu.com/](http://ca.archive.ubuntu.com/)

---

