---
title: "[SOLVED] help in shell scripts"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by cemlouis on 2008-03-27
I am trying to make a shell script which backups my web data on the comp. I did some basics of the shell scripts from the tutorials on the net. Anyway I have a line like below:

ssh -p 22 root@255.244...... this surely needs a password and I have to enter by hand everytime so how can I make the script to enter the password automatically? Is there a way?

Thank you,

---

### Post by markekeller on 2008-03-27
This is just a wacky idea (not sure if it will work), but you could try adding:

```
echo whateveryourpasswordis
```

right after the line you posted above.  A *better* solution, though, would be to run your script as root - then you won't have to enter your password for each thing.  Just type

```
sudo ./whateveryyourscriptiscalled.sh
```

in the shell, from the directory your script is in.

---

### Post by lswest on 2008-03-27
actually, the above method only would work (well, the second bit, about a script) if the web server you're connecting to has no password enabled, as the program would prompt for the root password of the web server.  There may be a way to input the password in the ssh command, but I'm not 100% sure and i have  no linux handy atm.  You can read up on it with ```
man ssh
```.  Good luck!

---

### Post by hyper_ch on 2008-03-27
you could exchange ssh keys and authorize with them:  [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

### Post by opscure on 2008-03-27
You can use Expect...  See:
[http://expect.nist.gov/](http://expect.nist.gov/)

example:

[http://bash.cyberciti.biz/security/sshlogin.exp.php](http://bash.cyberciti.biz/security/sshlogin.exp.php)

---

### Post by cemlouis on 2008-03-27
> **opscure said:**
> You can use Expect...  See:
[http://expect.nist.gov/](http://expect.nist.gov/)

example:

[http://bash.cyberciti.biz/security/sshlogin.exp.php](http://bash.cyberciti.biz/security/sshlogin.exp.php)

Thank you probably expect will do the job...

---

### Post by opscure on 2008-03-27
no problem

---

