---
title: "Abolish sudo password"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by paul6 on 2006-11-22
Hey all,

I remember reading a thread, where you could go into a config file somewhere and make it so *sudo* and *gksudo* don't prompt you for a password.

If anyone could post this solution again, that would be great! I really don't care if it's a security risk, I'm just sick and tired of Fluxbox asking for my password so I can shutdown.

Thanks,
Paul

Edit: Nevermind, I think I found what I need:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29)

---

### Post by jr.gotti on 2006-11-22
I know that you said you wish to ignore the security risks...but it really is rather foolish to do that. All it will take is someone to gain access to your system and do a "cd / && sudo rm -r *" and you're screwed. you may want to reconsider.

---

### Post by adam.tropics on 2006-11-22
To solve it for shutting down, but keeping sudo for all else,

```
sudo visudo
```
 
password, then it will open nano. add to the file

```
User_Alias USERS = adam
Cmnd_Alias SHUTDOWN = /sbin/shutdown
USERS ALL = NOPASSWD: SHUTDOWN
```
 
replace 'adam' with you user name.

Save it <ctrl>o ,good to go, you can create a panel launcher to restart using
```

sudo shutdown -r now
```
 
or shutdown using
```

sudo shutdown -h now
```

or just enter that from a terminal, either way, you won't be asked for a password.

---

