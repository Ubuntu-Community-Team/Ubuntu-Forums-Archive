---
title: "I get this error message on updates."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-03-19
I get this error every time I install updates and or software can anyone tell me why, and what I can do to correct it. 

[IMG]http://i7.tinypic.com/2lvef5s.png[/IMG]

[IMG]http://i3.tinypic.com/2q8zxup.png[/IMG]

And this is the first time I have seen this one.

[IMG]http://i12.tinypic.com/2j5kt3s.png[/IMG]

Anyone know whats going on here?

---

### Post by etank on 2007-03-19
For the first error try running ```
sudo chown havp /var/run/havp
```

For the second error run the following commands
```
 wget http://www.getautomatix.com/keys/automatix2.key
```
then
```
 gpg --import automatix2.key
```
next
```
gpg --export --armor E23C5FC3 | sudo apt-key add -
```
finally
```
 sudo apt-get update
```

I would not recommend automatix though personally. Automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to !install a fresh copy of Ubuntu.

---

### Post by Repent on 2007-03-20
Thank you it looks like they all worked accept the first one it gave me this.

joe203@joe203-desktop:~$ sudo chown havp /var/run/havp
chown: cannot access `/var/run/havp': No such file or directory

Now what should I do?

---

### Post by zvacet on 2007-03-20
gpg --keyserver hkp://subkeys.pgp.net --recv-keys CC919A31E23C5FC3
gpg --export --armor CC919A31E23C5FC3 | sudo apt-key add -

---

### Post by Repent on 2007-03-20
Like I said on my last post the first one still gives me an error.

joe203@joe203-desktop:~$ sudo chown havp /var/run/havp
chown: cannot access `/var/run/havp': No such file or directory.

But it shows up in the Synaptic PM as being installed, So I try to delete it and get this.

[IMG]http://i10.tinypic.com/4caeavt.png[/IMG]

[IMG]http://i5.tinypic.com/40f9o3m.png[/IMG]

Can someone help me with this?

---

### Post by Repent on 2007-03-21
Is there no one that can help me?

---

### Post by rosswmcgee on 2007-03-21
I get this msg. 
W: Failed to fetch [http://www.getautomatix.com/apt/dist...0edgy_i386.deb](http://www.getautomatix.com/apt/dist...0edgy_i386.deb)
503 Service Temporarily Unavailable

I keep getting this msg. on the update and the update will not go away?


It seems that their server is down and this may or may not be the problem. 

Am I right here or is there some thing I should do to get this automatix update to install.

What should I do?
:confused:

---

### Post by belikralj on 2007-03-21
As far as I see you don't have the directory /var/run/havp
and it's looking for something there, if you are trying to uninstall it's not there and it can't get the relavent uninstall information and if you are trying to install you don't have the permition to create that directory if it is missing. As far as I see this havp thing, either reinstall it from synaptic (System -> Administration -> Synaptic Package Manager) go to search and type in havp. If it is green rightclick on it and click "mark for reinstalation" or if it isn't click "mark for instalation". Then if you don't want it uninstall it (maybie you can uninstall it from synaptic too)

Hope this helps

---

### Post by belikralj on 2007-03-21
Oh and I forgot, if you don't have permitions you can change them from nautilus by giving it administrator rights. Type this in the command prompt to get nautilus as admin

sudo nautilus

then you can go to that folder, righclick on it and then go to properties, once open you can change the permitions for read write execute, but I don't know if changing them for that folder will adversly effect your system, someone else should halp us with that question

sorry I couldn't halp more :(

---

### Post by bapoumba on 2007-03-21
> **rosswmcgee said:**
> I get this msg. 
W: Failed to fetch [http://www.getautomatix.com/apt/dist...0edgy_i386.deb](http://www.getautomatix.com/apt/dist...0edgy_i386.deb)
503 Service Temporarily Unavailable

I keep getting this msg. on the update and the update will not go away?


It seems that their server is down and this may or may not be the problem. 

Am I right here or is there some thing I should do to get this automatix update to install.

What should I do?
:confused:
Please see the update in this thread:
[http://ubuntuforums.org/showthread.php?t=368839]("http://ubuntuforums.org/showthread.php?t=368839")

---

### Post by dracomordag on 2007-03-21
> **belikralj said:**
> Oh and I forgot, if you don't have permitions you can change them from nautilus by giving it administrator rights. Type this in the command prompt to get nautilus as admin

sudo nautilus

then you can go to that folder, righclick on it and then go to properties, once open you can change the permitions for read write execute,
you learn something new every day!

---

### Post by Repent on 2007-03-21
> As far as I see you don't have the directory /var/run/havp

But if you look at the picture you can see it was installed according to  the Synaptic Package Manager.

---

### Post by Repent on 2007-03-21
Is this what I should receive as a response using ( sudo nautilus )?


joe203@joe203-desktop:~$  sudo nautilus

(nautilus:22862): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

---

### Post by Repent on 2007-03-28
I get this error whenever I install the updates or when I use add and remove programs. 
Is there anyone that knows what's going on here?

---

