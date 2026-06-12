---
title: "unauthenticated Aegis"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by chrisb.40 on 2007-08-29
I was updating Aegis via root, a series of command lines appeared  taking me through an instalation process, they appeared to be from Aegis.  The command lines were terminated on the basis that the source was not authenticated.

Is this just a glitch?

Is it best practise to re-install Ub 7.04?

Or AM I PARANOID???

regards 

Chrisb

---

### Post by schorsch on 2007-08-29
What is "Aegis" and where did you get it from?

---

### Post by chrisb.40 on 2007-08-29
Add/Remove Programs  - Open Source Programs

---

### Post by chrisb.40 on 2007-08-29
Apologies, to clarify it's an anti virus program from Add/Remove Applications.

---

### Post by schorsch on 2007-08-30
I just installed Aegis via Add/Remove and had no problems. I updated it via the GUI as I have no idea how to update it via CLI and had no problems, too .... except that my virus definition file seems to be 434 days old !? Weird ... 
BTW: Why do you want to install a virus scanner? You do not need it when using linux especially when it is only an on demand and not an online scanner. Well, this opinion could start a flame war ... :-)
Please take a look [here]("http://www.psychocats.net/ubuntu/security#firewallantivirus") regarding security when running linux.
Sorry, I am not able to reproduce your problem .....

---

### Post by splintercellguy on 2007-08-30
Did you mess with your repos recently? Perhaps the GPG key list is corrupt?

---

### Post by chrisb.40 on 2007-08-30
Repos are main, universe, restricted, multiverse & source code has a - in the box.  3rd party software - medibuntu, updates include pre released feisty supported.  Authentication - [email]ftpmaster@ubuntu.com[/email]; [email]cdimage@ubuntu.com[/email] & [email]adminlists@medibuntu.org[/email].

Followed a thread in Sticky threads re medibuntu.

Virus scanner needed to protect colleagues who use windows.  Clam av seems to have a no of bugs which make it unreliable

Main concern re this thread is the vulnerability in using Root.  Don't normally use command lines via root, if that's the right expression, but the Aegis program will not update unless via root it seems.  Have done this a few times before without any problems, following threads in the forum.

This time the process was different with a series of questions re installion of update package, and yes/no responses.  Stupidly followed this process until it was stopped with a message about "unauthenticated" source.

regards

---

