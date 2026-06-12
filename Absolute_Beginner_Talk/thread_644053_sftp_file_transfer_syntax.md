---
title: "sftp file transfer syntax?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by mollyhardin on 2007-12-18
Hi there,

I am trying to connect to sftp.ning.com with the terminal.

I can connect just fine, I want to upload a file full of grapics and don't know how to reference them.

I tried put $/Graphics/* (which I am assuming is completely incorrect) -- Can anyone help me with the correct syntax?

Cheers,

M

---

### Post by p_quarles on 2007-12-18
The main commands to know are:
put  -- upload (you know this one, obviously)
get -- download
cd  -- same as in bash
lcd -- cd on the *local* machine (i.e, the one you logged in from)
ls  -- same as bash
lls -- list files in the local directory

So, in your example, it would be something like this:
```
sftp sftp.ning.com
lcd Graphics
lls  <--- to make sure you're where you think you are
put *
```If this ever gets too burdensome, you can always use Filezilla, which fully supports the sftp protocol.

EDIT: also, if you need to make a new destination directory on the server, the command is just like in bash: mkdir.

---

### Post by hyper_ch on 2007-12-18
also if you don't know further, you can have a quick look at the man pages. They normally have some exmaples:

```

man scp

```

---

### Post by bodhi.zazen on 2007-12-18
You can also try gftp, a gui front end for ftp.

I find it a little easier and more reliable then Fire ftp (the firefox extension).

---

### Post by hyper_ch on 2007-12-18
or with sshfs you could mount the remote folder locally...

---

