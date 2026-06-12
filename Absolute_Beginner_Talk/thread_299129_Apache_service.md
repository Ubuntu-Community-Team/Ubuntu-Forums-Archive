---
title: "Apache service"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by tgone on 2006-11-13
Hello,

I would like to start Apache automatically when Ubuntu loads. I checked the services section under system > administration > services, but there's no entry for Apache. Can someone tell me how to add this service to the list?

Thanks!

---

### Post by Gerard Barberi on 2006-11-13
Apache should already be running by default after boot.  reboot and type 'ps -e' in a terminal and you should see processes for your system. Apache should be listed.

If not there , the easiest thing to do is to apt-get BUM.

sudo apt-get install bum

then go to system --> administration and select boot up manager.  check the advanced box at the bottom.  Apache should be listed.  just check the box.

---

### Post by tgone on 2006-11-22
> **Gerard Barberi said:**
> Apache should already be running by default after boot.  reboot and type 'ps -e' in a terminal and you should see processes for your system. Apache should be listed.

If not there , the easiest thing to do is to apt-get BUM.

sudo apt-get install bum

then go to system --> administration and select boot up manager.  check the advanced box at the bottom.  Apache should be listed.  just check the box.

I did this. Apache or httpd is not listed anywhere though...

---

### Post by echo $USER on 2006-11-22
You can always run an nmap scan of 127.0.0.1 to see if port 80 is open and listening.

---

### Post by tgone on 2006-11-22
> **echo $USER said:**
> You can always run an nmap scan of 127.0.0.1 to see if port 80 is open and listening.

I assume port 80 is open and listening because Apache works fine when I start it manually. I'm trying to figure out how to make Apache start automatically. It's not listed under services...

---

### Post by echo $USER on 2006-12-01
> **tgone said:**
> I assume port 80 is open and listening because Apache works fine when I start it manually. I'm trying to figure out how to make Apache start automatically. It's not listed under services...


It won't show up, it does in Fedora.. just not in ubuntu.  Doesn't matter really as long as it runs.

---

### Post by tgone on 2006-12-03
> **echo $USER said:**
> It won't show up, it does in Fedora.. just not in ubuntu.  Doesn't matter really as long as it runs.

but it doesn't run automatically, I have to execute this command: "/etc/init.d/apache2 start"

---

### Post by suoko on 2006-12-19
I guess you're using edgy....

I have this problem too although apache starts automatically at boot.

try to create a simlink in /etc/rc2.d called S91apache2 which links to /etc/init.d/apache2
It should then start automatically at boot.

I guess apache is not showed in gnome-services due to upstart which messed up services.

---

