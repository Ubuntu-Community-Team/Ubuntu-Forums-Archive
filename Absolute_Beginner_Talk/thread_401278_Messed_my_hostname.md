---
title: "Messed my hostname"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-04-04
I think I've accidentally changed my hostname.
As a result, it looks like Synaptic and automatic updates no longer function

When I do this,

philip@Ubuntu:~$ cat /etc/hostname

I get this.


Ubuntu
philip@Ubuntu:~$

When I do this:-


I get this:-

philip@Ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost Ubuntu
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
philip@Ubuntu:~$
philip@Ubuntu:~$

cat /etc/hosts

I guess I altered something whilst trying to get my network working.......which it does now, well, except the last time I tried printing on a shared printer, it didn't.

I can see that Some 'Ubuntu' references have a capitol and some don't.

How do I mend this?

Phil

---

### Post by Bachstelze on 2007-04-04
```
sudo nano /etc/hosts
```

edit the 'ubuntu' to 'Ubuntu'.

---

### Post by groeswenphil on 2007-04-04
Dear me,
Didn't work, got this.

philip@Ubuntu:~$ sudo nano /etc/hosts
sudo: unable to lookup Ubuntu via gethostbyname()
philip@Ubuntu:~$

---

### Post by Bachstelze on 2007-04-04
You'll need to do that in recovery mode then.

---

### Post by groeswenphil on 2007-04-04
Just looked in the index of my copy of Ubuntu-Linux for non-geeks and it goes straight from Rael Player to Red Hat, with no mention of recovery mode in between.

So...........what's the spell for recovery mode?

Phil

---

### Post by Bachstelze on 2007-04-04
Reboot your Ubuntu. You should see the GRUB menu, which should look like [this](http://img150.imageshack.us/img150/1682/grub4kt.jpg). Choose "recovery mode" and after a while, you'll get a root promt, than you can do what I told you earlier (without sudo).

---

### Post by groeswenphil on 2007-04-04
Wow!

What a lot of words whizzing past my eyes.

Right, I did that, and it appeared to do what I wanted it to...........but still no Synaptic and still not able to get the Ubuntu updates to load for me.

I wasn't sure of what to do after I'd changed the U to u

I think I did shift and x, but then I lost concentration.

I'm getting really confused with this........perhaps I should have changed the Ubuntu with an upper case U to a lower case?

Could you just tell me what to do in recovery mode after I've changed the u?

I'm going out for a while now, so if I don't get back to you soon, don't think I've totally killed it.

Thanks for your help,
Phil

---

### Post by groeswenphil on 2007-04-04
Getting nowhere.

I can get to the part that I need in safe mode and appear to be able to make the changes. I'm trying all combinations of capitals and small Us, but whenever I get back to the terminal, I get this.

philip@Ubuntu:~$ sudo nano /etc/hosts
sudo: unable to lookup Ubuntu via gethostbyname()
philip@Ubuntu:~$


I feel awfully brave working in safe mode....it's nothing like Windows safe mode is it.

You know, after I make the changes, ctrl x appears to make the changes stick, but I can't find out how to get out of safe mode without turning the computer off by holding the button for five seconds.

Thanks,
Phil

---

### Post by Maestro23 on 2007-04-04
> **groeswenphil said:**
> Getting nowhere.

I can get to the part that I need in safe mode and appear to be able to make the changes. I'm trying all combinations of capitals and small Us, but whenever I get back to the terminal, I get this.

philip@Ubuntu:~$ sudo nano /etc/hosts
sudo: unable to lookup Ubuntu via gethostbyname()
philip@Ubuntu:~$


I feel awfully brave working in safe mode....it's nothing like Windows safe mode is it.

You know, after I make the changes, ctrl x appears to make the changes stick, but I can't find out how to get out of safe mode without turning the computer off by holding the button for five seconds.

Thanks,
Phil

If you are using nano to edit your files.  The proper sequence is:

> Ctrl O (Writes/Saves the file)

then

Ctrl X (Exits the program).


---

### Post by kerry_s on 2007-04-04
Have you tried rebooting yet?

---

