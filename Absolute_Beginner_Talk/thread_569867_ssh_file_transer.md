---
title: "ssh file transer"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by chrisb_duck on 2007-10-07
Hello, 
I have setup an ssh connection from my ubuntu computer here to a different linux computer elsewhere and it is awesome.

What I would like to do now is to be able to transfer files between the two computers through the command line only, via the ssh connection. Is this possible?

Please be explicit as possible with explanations!
Thanks!

---

### Post by Malibu Illusion on 2007-10-07
You need to use scp.

Example, to send a file to a remote server via SSH:

```
scp /path/to/file/to/send user@host.com:destination/directory
```

To retrieve one from a remote location:

```
scp user@host.com:source/directory/file ~/local/path
```

---

### Post by rharris on 2007-10-07
Good info at the following link:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Cheers..........

Rob

---

### Post by HermanAB on 2007-10-07
The trick is 'scp' as pointed out above.

However, you should not underestimate the incredible power of the GUI when using Konqueror (the file browser that comes with Kubuntu).  With Konqueror, you can type "fish://server/share" and then you can drag and drop files around.  

Fish uses ssh and scp underneath and works amazingly well.  You can even split the Konqueror screen and do "ftp://" or "smb://" in another window, then drag and drop files between different servers!

Cheers,

H.

---

