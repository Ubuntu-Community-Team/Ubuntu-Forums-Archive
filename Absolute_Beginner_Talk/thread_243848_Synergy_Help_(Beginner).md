---
title: "Synergy Help (Beginner)"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by measure on 2006-08-25
I installed the package from synaptic package manager. How do I run it? I'm sure that once I know how to run it I'll be able to to the rest, I'm just not familiar with Ubuntu like I am with Windows.

I also read that I have to make a .conf file, can someone shed some light on this for me.

Thank you

---

### Post by measure on 2006-08-25
bump

---

### Post by measure on 2006-08-26
"a client with name "ubuntu2" is not in the map"

Okay well I got it to work, sortof.

I get that error message when I try to connect. I don't get it!

---

### Post by NetworkGuy on 2006-08-26
From what I can tell with a quick look,

There are two programs synergyc for client and synergys for server

There is a man page you can probably get to by using ```
man synergy
```
There is also some documentation in /usr/share/doc/synergy

This should get you started..

---

### Post by k9brand on 2006-08-26
I just got it working today.  Basically you have to have it installed on both computers.  One will be the server and one will be the client.  

I set up the synergy.conf file using the example file located at /usr/share/doc/synergy/examples/synergy.conf

For the names, I used my windows box name and my ubuntu name (whatever is after the @ symbol when you are using the terminal).

I used Ubuntu as the server.  After I saved the conf file, I started the server by typing:
> sudo synergys

Then on my windows machine I connected to my Ubuntu's IP address (which you can find out by typing > ifconfig

After that it just worked.  If you want, I can post my .conf file

---

### Post by NetworkGuy on 2006-08-26
i personally don't need it, but it might be good for someone else in the community that may run into a similar issue.

---

### Post by measure on 2006-08-28
I got it to work. Thanks!

You should see my setup now! It's amazing!

---

