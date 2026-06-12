---
title: "Kick User Off Box"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by th3gh05t on 2006-03-30
Hi, 

If there is a remote user logged onto your computer, how do you boot them off?

---

### Post by kairu0 on 2006-03-30
Run 'ps ax' from the console to find the bash session of this user. Kill it with "kill -9 <pid number>".

---

### Post by localzuk on 2006-03-30
You could kill the process they are logged in with - so if it an ssh user, ```
sudo /etc/init.d/sshd stop
```

would do the trick.

---

### Post by th3gh05t on 2006-03-30
[QUOTE=kairu0]Run 'ps ax' from the console to find the bash session of this user. Kill it with "kill -9 <pid number>".[/QUOTE]

Thanks! This worked!

It is usefull information to know~!

---

### Post by hw-tph on 2006-03-31
[QUOTE=localzuk]You could kill the process they are logged in with - so if it an ssh user, ```
sudo /etc/init.d/sshd stop
```

would do the trick.[/QUOTE]

No, it wouldn't. ssh spawns a new process for each user that logs in. Stopping the ssh daemon will only make it impossible to log in remotely. Users who already are logged on are not affected.

Killing the parent process is the key. You can use a bash command to find out what processes a users has:
```
ps aux | grep ${USER} | awk '{print $2 " " $11}' | sort -gr
```
...would print the process with the lowest PID at the bottom. Chances are it is the login shell or the x-session-manager for that user. Kill it and the user is kicked off the system. Replace ${USER} with the login name of the user of course.



Håkan

---

### Post by localzuk on 2006-04-01
ah, ok... my bad. Should have known that seems how I update sshd remotely on my servers :)

---

### Post by professor_chaos on 2006-04-01
If I might ask, why are you doing this? I mean, letting a user login and then all of a sudden, killing there process? Are you booting them for administrative purposes? Just curious?

---

