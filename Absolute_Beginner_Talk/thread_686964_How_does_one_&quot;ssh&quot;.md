---
title: "How does one &quot;ssh&quot;?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-02-03
I hear people say that they access other computers by ssh-ing. I've never done anything like this (even with Windows), so I don't have the slightest idea what it entails.

I have a PC at my parents' house that they are afraid to use because it has Linux. Can someone point me in the direction of a guide on how I can do anything long-distance with that computer? 

I've seen people using Windows remotely access another windows computer. If I could do something like that with this computer, that would be cool.

I don't want the machine to be unused just because it's old, but I simply don't have room in my apartment for any more unnecessary clutter.

---

### Post by nemilar on 2008-02-03
The quick and dirty process:

1.  On the machine you want to access, install the package openssh-server
2.  Forward port 22 in that machine's router (to that machine)
3.  Now you can login with your user/password, over the internet, to that machine with the command

```
ssh user@ipaddress
```

Other things to consider:

[Accessing files remotely via SSHFS]("http://www.techthrob.com/tech/sshfshowto.php")
[Getting a free domain name for your home network]("http://www.techthrob.com/tech/dyndns.php") so you don't have to remember the IP, or if the IP address changes, you can still access it.

---

### Post by nemilar on 2008-02-03
Also, you'd probably want to know that you can use graphical apps via SSH if you want; it might be pretty slow over the internet, though, depending on your connection.

To do this:
after you install openssh-server, there is a configuration file at /etc/ssh/sshd_config
find the line for "X11Forwarding" and make sure it is set to "yes"

Then, when you SSH, use
```
ssh user@destination -X
```

and you can run commands, e.g, "firefox" on the remote machine, and the windows will show up on your local machine.

---

### Post by Dr Small on 2008-02-03
There are a great many threads about this on the forums, but here is an article about it all on the wiki:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

---

