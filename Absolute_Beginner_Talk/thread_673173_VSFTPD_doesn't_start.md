---
title: "VSFTPD doesn't start"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by WNxCryptic on 2008-01-20
I've installed vsftpd using

```
sudo aptitude install vsftpd
```

After I reboot the server, I can login via SSH, but:

```
ftp localhost/code]

Returns "connect: connection refused"

[code]/etc/init.d/vsftpd restart
```

Does not give any error messages, it simply returns to the normal terminal prompt.

So there is no ftp service running..help?

---

### Post by doddo on 2008-01-29
Hello! Have u configured vsftpd to accept connections to localhost? default is off

in vsftpd.conf:
```

# Uncomment this to allow local users to log in.
local_enable=YES

```

Is the process running?

```

ps -ef | grep vsftp

```

EDIT:
That uncommenting stuff (in vsftpd.conf) is not applicable in this case cause it's only regarding the local users (e.g those in /etc/passwd)

instead preform the other command and also check if you have a service running at the said port like
```

netstat -anp| grep ^tcp.*LISTEN

```
or preferrably
```
nmap -sT localhost
```

To figure out if the service is runnign

---

