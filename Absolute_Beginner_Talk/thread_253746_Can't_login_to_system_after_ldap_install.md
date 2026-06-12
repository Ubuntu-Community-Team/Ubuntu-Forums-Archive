---
title: "Can't login to system after ldap install"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by [S|G] on 2006-09-08
I have recently tried to install LDAP at my system using the following command:
```

apt-get install ldap-utils libiodbc2 libldap-2.2-7 libnss-ldap libpam-ldap nscd slapd

```

I couldn't get it to work and removed it using apt-get remove --purge [packages that were installed], but when I changed to another terminal I couldn't login anymore.

I'm still logged in, but whenever I try to sudo I get this:
```

diego@SnowGust:~/Downloads$ sudo ls
sudo: unable to lookup SnowGust via gethostbyname()
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts

```
I didn't even get prompted for the password, it shows up like that immediately. When I go to a terminal and try to login (as any user at all) I get this:
```

SnowGust login: diego
permission denied

Snowgust login: root
permission denied

```

Also, I am already logged in as root in a terminal, and when I try to change the root's password I get this:
```

root@SnowGust:/# passwd
passwd : Permission denied

```

Have I completly screwed up my system? How can I fix this? :confused: 

Thanks!

---

### Post by backu on 2006-09-10
I have the same exact problem, however, I decided to reboot my system after it started happening, with all the LDAP support still in place. During bootup (in recovery mode), I did notice that the nss_ldap could not connect to the ldap server.. I've since reinstalled my system until I find out what the heck happened.

---

### Post by Najand on 2006-09-10
It seems you have root privilege. Check it out you have your hostname (I assume SnowGust) in both files: 
/etc/hosts
/etc/hostname
Then run this command:
```
#hostname SnowGust
```
And see if your problem is solved or not.

---

### Post by [S|G] on 2006-09-10
Hello, and thanks for the replies.

I couldnt get it to work even after checking the hostnames, so I went ahead and reinstalled my whole system. Now I have installed it on another box, with a fresh install of Dapper, and strangely it didn't happen again.

Although now I still can't get kerberos to work properly (syntax error in profile relation while retrieving configuration parameters), although it's another problem (unrelated?) that I'll soon be starting another thread about if I can't google it.

---

