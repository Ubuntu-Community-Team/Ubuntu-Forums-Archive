---
title: "Mounting a share with two words in its name"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Trinitrogen Oxide on 2007-01-02
I have a couple shares on my windows 2003 server that I need to access from my new Ubuntu machine, so I can watch/listen to the files on them. It wasn't working to navigate to them (run -> smb://computername, then click the files). From what I understand, I need to mount the shares to my machine. Im looking at the guide for it on the Ubuntu guide, but I've ran into a problem.

One of the share names has two words (Music Video). To create the directory under media I 

sudo mkdir /media/Music\ Videos

which seems to work, but I want it to mount everytime I boot, and the guide has me do that by adding an entry to fstab but that doesn't bode well with fstab, when I try to reload it it tells me theres an error on line 11, presumably where I added the entry. What now?

---

### Post by Trinitrogen Oxide on 2007-01-03
I realize that the shortest answer would be to change the name of the share on the windows machine, but then I'd have to change other things (scripts, etc) so It'd be nice to find a solution in ubuntu

---

### Post by bartbes on 2007-01-03
isn't it possible to change > /media/Music\ Videos in ```

"/media/Music Videos"
``` (note the quotation marks)

---

### Post by Trinitrogen Oxide on 2007-01-03
> **bartbes said:**
> isn't it possible to change  in ```

"/media/Music Videos"
``` (note the quotation marks)

in fstab? I'll give it a try...

---

### Post by Trinitrogen Oxide on 2007-01-03
Heres the entry I put in
```

"//192.168.1.102/Music Videos" "/media/Music Videos" smbfs credentials=/root/.smbcredentials	0	0

```

And heres the error I got
```

trinitrogen@Xenon:~/NewsbinPro$ sudo mount -a
[mntent]: line 11 in /etc/fstab is bad

```

---

### Post by petersjm on 2007-01-03
I don't know much about this kind of thing, but would substituting the space with %20 work? i.e. "/media/Music%20Videos"

%20 is a character code for a space, but might not work in this instance... Can't hurt to try it in fstab?

---

