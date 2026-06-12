---
title: "Include password when using Sudo."
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by torx on 2006-06-22
So i want to use my T610 to remotely shutdown my computer, by making the computer execute "sudo shutdown now". But since i am required to physically type in a password when using sudo, i can't do that yet. 

Are there any parameters i can use in order to pass the password to sudo? So i won't have the prompt asking me for password.

---

### Post by n00b@linux on 2006-06-22
[quote=torx]So i want to use my T610 to remotely shutdown my computer, by making the computer execute "sudo shutdown now". But since i am required to physically type in a password when using sudo, i can't do that yet. 
 
Are there any parameters i can use in order to pass the password to sudo? So i won't have the prompt asking me for password.[/quote]
 
I don't know if this works, but is it not possible to append your code using '|' (pipe)?
 
For example, if your password was 'subliminable' the code would be:
 
sudo shutdown now | subliminable
 
Again, I don't know if it works, but surely it's worth a shot.

---

### Post by mtron on 2006-06-22
that's very insecure! 

i would not do it if you're connected to the net. really think twice, and than another time before you decide of enabeling this.

Anyway: [http://ubuntuguide.org/wiki/Dapper#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29](http://ubuntuguide.org/wiki/Dapper#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29)

the shutdown commands are
Usage:    shutdown [-akrhHPfnc] [-t secs] time [warning message]
                  -a:      use /etc/shutdown.allow
                  -k:      don't really shutdown, only warn.
                  -r:      reboot after shutdown.
                  -h:      halt after shutdown.
                  -P:      halt action is to turn off power.
                  -H:      halt action is to just halt.
                  -f:      do a 'fast' reboot (skip fsck).
                  -F:      Force fsck on reboot.
                  -n:      do not go through "init" but go down real fast.
                  -c:      cancel a running shutdown.
                  -t secs: delay between warning and kill signal.
                  ** the "time" argument is mandatory! (try "now") **

---

