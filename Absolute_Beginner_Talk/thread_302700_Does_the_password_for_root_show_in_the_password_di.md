---
title: "Does the password for root show in the password dialog?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by encompass on 2006-11-19
Our server may have been hacked and we are trying to find the computer that may have been hacked.  I have decided to start looking to see if someone activated my root account or something from my ssh connection.
When I look at this...
[[IMG]http://img101.imageshack.us/img101/381/screenshotrx4.th.png[/IMG]](http://img101.imageshack.us/my.php?image=screenshotrx4.png)
I wonder if this means I have a root password and someone has set it.  Is there a good way to check if my root has received a password?
Thanks for the advice.
It's doesn't look like it has one set to me... but I still want to know how to check for sure.

---

### Post by Lynoure on 2006-11-19
If you do   ```
sudo less /etc/shadow
```   the passwordless line for root looks like this:

```
root:*:13264:0:99999:7:::
```

Notice the asterisk?
When root has a password, the asterisk is replaced with a bunch of characters.

However, root not having a password set does not mean for sure that your computer is not broken into. The attacker might use just some other way to got his code run as a root. At least install   chkrootkit   and run it to check if any rootkits are found installed on your computer.  And look at the logs at /var/log  to see if there is anything weird. (If you are not used of reading the logs, many things can look weird, I know.)

---

### Post by encompass on 2006-11-19
I get... 
jason@tabby:~$ sudo cat /etc/shadow | grep root
root:!:13452:0:99999:7:::
jason@tabby:~$ 
and I first did check the logs... got a guy trying to hack me... but that is not unusual.  My passwords and user names are all uncommon and hard to guess. you know... like this... SreDm324d3DuF. I don't think he would get it quickly... and it changes every 2 months or so.

---

### Post by Lynoure on 2006-11-19
What you got is good too.

Passwords are not the only way to break into the machine. What made you think it was broken into in the first place?

Did you run chkrootkit already? If you have already disconnected the server from the network, you can get the .deb file from the web with another computer than then do ```
sudo dpkg --install filename
```

[http://www.cs.cmu.edu/~help/security/unix_linux_breakins.html](http://www.cs.cmu.edu/~help/security/unix_linux_breakins.html) has some instructions of what do you about a broken-into computer.

---

### Post by encompass on 2006-11-23
I had to help persuade that I was not hacked.  The company I work for, there webserver was hacked and they wanted to see if it came from me.  Everything looks good here... ends up it was the mistake of someone else on the team.  They got jipped for a Man in the middle attack.  Things are ok here.  The defaced the site... but we had a quick and handy backup and all information was changed.

---

