---
title: "Computer name"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by epb on 2007-05-08
Hi

During installation of ubuntu on my new computer I entered a name for the computer... Now I've realised that it is a stupid name and that I would like to change it. Is this possible without re-installing Ubuntu?

---

### Post by LaurelLynn on 2007-05-08
Try:

$  sudo  gedit   /etc/hostname

The only entry in the file is the hostname, just change it to whatever you want. It will take effect when you reboot.

---

### Post by justleen on 2007-05-08
System > Administraton > Network 

On the General tab (on top of my head), you'll find your host name, you can change it here as well (again, in effect after reboot)

---

### Post by LaurelLynn on 2007-05-08
Good point!

---

### Post by Skrynesaver on 2007-05-08
Changing it in the Network settings also looks after editing your /etc/hosts file for you and probably a few others I've forgotten;)

---

### Post by Carlos Santiago on 2007-05-08
You just have to type 'hostname NewComputerName'. 
But as you have to do it with administration rights, you have to execute the command with 'sudo'. 
So, on a console type:
```

sudo hostname NewComputerName

```

---

### Post by epb on 2007-05-08
Ok thanks a lot guys

---

### Post by dimbulb1024 on 2007-05-08
Came across this thread and decided to change my computer name.

Followed justleen's idea first and rebooted. No change.

Then followed Carlos' idea, same result.

Finally, did the sudo gedit and opened up the hostname file. It is blank. Do you just put in whatever name you want or is there some format it must be in?

---

### Post by epb on 2007-05-08
> **Carlos Santiago said:**
> You just have to type 'hostname NewComputerName'. 
But as you have to do it with administration rights, you have to execute the command with 'sudo'. 
So, on a console type:
```

sudo hostname NewComputerName

```

By the way, I haven't tried this myself yet but are you sure this is the right command? I'm also using OS X (build on Unix in case you didn't know) and I've tried the 'hostname' command there.. But it seems like this command is displaying the host on the network!? That is, in OS X - not ubuntu (but I think this is kinda the same?)!

---

### Post by LaurelLynn on 2007-05-08
This is the values for mine are:
```

catastrophe:~$ cat /etc/hostname
catastrophe
catastrophe:~$ cat /etc/hosts
127.0.0.1 localhost catastrophe
192.168.0.10 catastrophe
.
.
.

```

That is because I use static IP addresses. With DHCP assigned addresses I believe you should not edit /etc/hosts (you don't know the address yet). The hostsadm package should take care of it.

The man page for "hostname" states that it is a command to show **or** set the hostname.  Without arguments it only displays the current name.

```

The   host   name   is   usually   set   once   at  system  startup  in
       /etc/rc.d/rc.inet1 or /etc/init.d/boot (normally by  reading  the  con&#8208;
       tents of a file which contains the host name, e.g.  /etc/hostname).

```

So editting /etc/hostname will propogate through unless you are running another package that overrides it at startup.

---

