---
title: "tcp and network question"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-26
I am on a unencrpted wireless network with serveral others
what does the printout below mean
i think 32770 32771are port numbers 
localhost is me? 127.0.0.1?


reg@sw~$ sudo netstat --tcp -lp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN     6851/hpiod
tcp        0      0 localhost.localdo:32771 *:*                     LISTEN     6891/python
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     6820/cupsd
tcp6       0      0 *:ssh                   *:*                     LISTEN     7137/sshd


xstation:smile: :smile:

---

### Post by shof2k on 2005-12-26
If I've read the man pages correctly (typing "man netstat" into a terminal), the the services are on port 32770 listening for any incoming connections on port 6851 for the hpiod program etc.

Yes 127.0.0.1 is the system default for localhost (ie...your computer)

I really woudn't recommend unencrypted wireless networks unless your comfortable with the world and thier dog recording every site and password that you send.

Hope that helps...

---

### Post by bscbrit on 2005-12-26
As shof2k said, this seems quite normal.

Various services are 'listening' for data - this is entirely normal and usual.

hpoid - is a Hewlett Packard driver.  Have you installed an HP printer?  I guess so.
cupsd - is your printer daemon waiting for you to send something for printing.
sshd - is your ssh daemon.  [I should have said secure shell daemon - telling you that ssh is ssh wasn't terribly useful - sorry]
python - well I assume that you have a daemon related to the language python(?!) or some other piece of software that calls itself python.  I can't imagine how the language python could really be involved but, hey, there are loads of things that I don't understand....

However, there is nothing here to cause concern and IT DOES NOT mean that anyone is listening to your wireless network.  They might be - but you will not know unless they start using your network for their own purposes.  Hence, why shof2k strongly recommended that you do not continue to run your network insecurely.  I can only put my own support behind his suggestion.

---

### Post by bscbrit on 2005-12-26
shof2k - you were close but not quite spot on.  I think that the 6851 is the PID of the hpoid program, which is listening on port 32770.  

But I guess that's what you really meant to say :D  :D  :D

---

### Post by shof2k on 2005-12-27
Opps, fat fingers on my part.  You're spot on with the PID.

Again....only use an encrypted network if your're comfortable with the consequences.

---

### Post by fordfan753 on 2005-12-27
[QUOTE=bscbrit]
python - well I assume that you have a daemon related to the language python(?!) or some other piece of software that calls itself python.  I can't imagine how the language python could really be involved but, hey, there are loads of things that I don't understand....
[/QUOTE]

Python could be something like the bittorrent GUI...

---

### Post by bscbrit on 2005-12-27
fordfan753 - thanks for that.  Your sig also applies to me, and I'm much older.  I really should  try harder...... :D

---

