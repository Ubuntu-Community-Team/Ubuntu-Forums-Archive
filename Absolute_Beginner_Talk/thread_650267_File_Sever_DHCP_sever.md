---
title: "File Sever DHCP sever"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Devastator9 on 2007-12-26
Okay folks here is what I want to do if someone could just point me in the right direction.
I have a 3ghz chip with a gig of ram that I want to use for this.
I would have 1 hard drive 80 gig for Operating system 2 500 gig drives for software raid 1 system.
All I need it to do is store file from windows machines and sever as gateway for internet.
Do I need to install LAMP or is there another way that may be a little easier. I have read some post from the help doc. but seemed more system than I need. 
I am planning on using 7.10 server.

Any help is help.

---

### Post by Cypher on 2007-12-26
An ideal situation is for you to use your Linux machine as a File server and perhaps Web server. So you'd want something like the following:
```

<CABLE MODEM> --> <ROUTER>
                     |
                     |-> Linux File Server
                     |--> Other PC
                     |---> Any other PCs

```

The <ROUTER> would be your firewall and DHCP server. You will want to install SAMBA on the Linux File server and you can mount that on the PC and save files to it. Should you choose/want to run a Web server, you can configure Apache on the File server and set the <ROUTER> to forward requests to port 80 or any other private port to the Linux server.

---

### Post by Devastator9 on 2007-12-26
Cypher
Thanks thats what I'll work on setting up. 
It will be a few days before I start this project.

---

