---
title: "Editing Ubuntu Host File"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by djesse50 on 2006-05-29
I was trying to configure my wireless card, and in the Network setup menu, deleted the host name, which was set to the default 'Ubuntu'. I then re-booted, and after I log on,  I get the message:

"Could not look up Internet address for
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding to the file /ect/hosts.
Log in Anyway or Retry?"

Now, I have two questions. What lines do I need to add, and how do I add it?  I would change it in the Network setup menu, but I cannot access it.

I think i'm running Hoary Hedgehodge with Gnome. My host file looks like this:
127.0.0.1 localhost.localdomain localhost

# The folling lines are desirable for IPv6 capable hosts
::1 1p6-localhost 1p6-loopback
fe00: :0 ip6-localnet
ff00: :0 ip6-mcastprefix
ff02: :1 ip6-allnodes
ff02: :2 ip6-allrouters
ff02: :3 ip6-allhosts

---

### Post by ProjectGod on 2006-05-30
127.0.0.1 localhost.localdomain localhost xxx

xxx is where you put what ever name you wish... everything else is the same.

don't forget to reboot the machine orr.

**sudo /etc/rc.d/init.d/network restart**

i hope this helps!

:D

---

### Post by djesse50 on 2006-05-30
When I try to run anything as root, or type in sudo in the terminal I get the error:

sudo: unable to lookup via gethostbyname()


How do I fix this? I cannot edit the host file, due to not having permissions as root.

---

### Post by djesse50 on 2006-05-30
I know what my host file should look like, but I do not know how to edit it.

---

### Post by Iowan on 2006-05-30
May need to reboot into rescue mode (from GRUB).

---

### Post by ifokkema on 2006-05-30
[QUOTE=djesse50]I know what my host file should look like, but I do not know how to edit it.[/QUOTE]

Also, I think you have to re-add your hostname in /etc/hostname. It's probably a empty file now, but without it, your system does not know it's name, regardless of the /etc/hosts file.

The file just has to have the hostname in it, nothing else.

Hope this helps you out,

Ivo

---

### Post by ProjectGod on 2006-05-30
were you able to use "sudo" before? this may sound stupid but have you enabled the root account?

---

