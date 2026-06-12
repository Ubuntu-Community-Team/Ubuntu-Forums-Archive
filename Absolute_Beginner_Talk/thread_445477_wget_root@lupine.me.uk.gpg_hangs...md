---
title: "wget root@lupine.me.uk.gpg hangs.."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by warpedreality on 2007-05-15
I'm gettign this error when i'm trying to run

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add - 
```

```

shahfazal@fazalt60p:~$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
Password:--20:51:21--  http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
           => `-'
Resolving ubuntu.beryl-project.org... 195.114.19.35, 208.113.193.9, 80.77.247.17, ...
Connecting to ubuntu.beryl-project.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/octet-stream]

100%[====================================>] 2,415         --.--K/s             

20:51:22 (127.82 MB/s) - `-' saved [2415/2415]

```

The terminal just sits there forever.. after the '-' saved.. and nothign else.. 

when I run 

```
sudo apt-get upgrades
```

I get this error

```

Reading package lists... Done
W: GPG error: http://ubuntu.beryl-project.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems

```

I'm able to browse the internet fine and everything..

---

### Post by mitch.c on 2007-05-16
What happens if you try this in two steps...

```
$ wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg

$ sudo apt-key add  root@lupine.me.uk.gpg
```

-- 
Mitch

---

