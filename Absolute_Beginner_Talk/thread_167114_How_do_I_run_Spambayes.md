---
title: "How do I run Spambayes?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Sarisar on 2006-04-27
OK so it's a noob question (it's my first week on Ubuntu).  I played around with Spambayes on ... another operating system... and that worked fine.  But I have _no_ clue how to do it on Ubuntu.

So I've downloaded the package and it's installed.  Now how to I actually RUN spambayes.  I want it to grab my email off the server (it's a gmail account) and then let me grab it using Opera (yeah I know I'm a weirdo, but the email bit of opera).  I could do this fine in Windows but I'm lost in Linux.

Presumably I want to set it up as a Daemon to auto run, and I found http://spambayes.sourceforge.net/unix.html that talks about it but it says run sb_server.py which a search didn't turn up on my machine.

OK so I don't really NEED to run spambayes as gmail does a damn good job on it's own but I would like to set up an email server for the families emails at some point and filter all the spam out before they read it.

Thanks in advance.

---

### Post by Sarisar on 2006-04-30
Anyone have any ideas?  Anyone?

Hello? *scrunches up eyes and looks around* Anyone else here?

---

### Post by cwaldbieser on 2006-04-30
[QUOTE=Sarisar]Anyone have any ideas?  Anyone?

Hello? *scrunches up eyes and looks around* Anyone else here?[/QUOTE]
How did you install the software?  Through apt-get / synaptic, or did you just download the source?

---

### Post by Sarisar on 2006-04-30
Synaptic package manager under spambayes (just did a 'find' for it).

Having said that was playing around with something else and realised when I searched I didn't have the 'show hidden files' and managed to find (in a different directory then the docs mention) the files.  Think I have it running.  At least I can find the config website on my PC.

Now to just get things talking to each other.

I am always amazed how often one problem can be solves when trying to do something completely unrelated!

---

### Post by Sarisar on 2006-05-03
OK I'm going to be rather narcissitic (however that is spelt) and reply to myself.

I had terrible trouble trying to get Spambayes to work - kept getting an error about can't bind not enough rights, and if I ran sudo /usr/bin/sb_server.py then it said in use.

Anyway I found an ini file in my home directory bayescustomize.ini that stated ports to connect to and I hadn't changed from 25 and 110 and that was what the problem was - change that file and it works.

Now all I need is some email to check it all works :P

---

