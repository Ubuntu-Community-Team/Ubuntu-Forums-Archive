---
title: "known_hosts workaround / help"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-09-28
Hi,

My router is set to forward SSH requests for port 22 to my main Ubuntu Server, and SSH requests for port 3000 to my Mac.  Can get at files on both computers securely this way when I am raveling.  And this system works well on my laptop (can log into to either system with the same public IP address) but on Ubuntu (which is obviously more clever and a lot safer) I get a complaint that the "known_hosts" don't match and it won't let me connect.

I suspect this is because the IDs of the two computers are different, but Linux is seeing the IP address as being the same and throwing a red flag.  Any way to let both machines be on the known hosts list with the same IP ?

Thanks,
DAmon

---

### Post by llamakc on 2006-09-28
In your home directory is a hidden directory, ~/.ssh

When you see that error message it should spit out which "line" is offending.

cd ~/.ssh/

gedit known_hosts

and remove the line. This happens if you move around alot.

---

### Post by llamakc on 2006-09-28
To clarify, the error you get is on your traveling machine, correct? That would be where you want to edit ~/.ssh/known_hosts

---

### Post by thornomad on 2006-09-28
Yea ... the error comes from the laptop ... it does spit out an error ...

Hmm: so, basically, just delete the item each time I switch machines?  I can do that ... was looking for a fix that took one less step ... but that is okay.  Can remove the whole file too ...

Thanks,

---

### Post by llamakc on 2006-09-28
I think if you start using keys you won't have that problem.

On your laptop do this:

ssh-keygen -t dsa

It will prompt for a passphrase. You should use one. I don't, but nobody else uses my computer either.

Next, on laptop do:

scp ~/.ssh/id_dsa.pub I.P.Or.NameofHome:~/CATME

Next, logon via ssh with your password to computer at home that I called above NameofHome.

On that home computer, do:

cat CATME >> .ssh/authorized_keys2

rm CATME

logoff.

Try logging in again. The passphrase doesn't have to be your system password, and as I mentioned I don't even use one. The next time you login from laptop to home, you'll get either the prompt for the passphrase or nothing, and be in.

---

### Post by thornomad on 2006-09-28
Hey thanks for that quick tutorial ... but I am already using the SSH-Key ... it still throws the error.

I think it is because I have one host address:

myname.mydynamichost.com

And two different machines accessed through ports:

machine one = port 22 (default)
machine two = port 3000

So, this way I can chose to either log in to either machine.  On my local network, the keys work great, no problems (I used each machines IP address).  But when I am accessing ssh via:

```
$ ssh -e none -l myusername -p 3000 myname.mydynamichost.com
```

Then it seems Ubuntu is reading the known_hosts entry for the port 22 machine (which was access first).  If I delete known hosts, then access the port 3000 machine, then try the port 22 machine, the same problem occurs.  All with keys.  I didn't know if there was a way to have two known_hosts entries for machines at the same address (Though different port).

Maybe not ?

D

---

### Post by llamakc on 2006-09-28
What about tunneling from linux to the Mac?

---

### Post by thornomad on 2006-09-28
> **llamakc said:**
> What about tunneling from linux to the Mac?

OOOH!!  Now that sounds new and interesting ... tell me you have a link or two that can lead me in **that** direction!?

Thanks!

---

### Post by llamakc on 2006-09-28
I lost the page and can't find it.

Maybe this can help?

[http://www.thomasmarquart.net/tunnel.html](http://www.thomasmarquart.net/tunnel.html)

I'll search my history.

[http://www.rzg.mpg.de/networking/tunnelling.html](http://www.rzg.mpg.de/networking/tunnelling.html)

---

### Post by thornomad on 2006-09-28
Thank you!  I will look into that ... seems fairly straight forward.

Appreciate your help.

D

---

