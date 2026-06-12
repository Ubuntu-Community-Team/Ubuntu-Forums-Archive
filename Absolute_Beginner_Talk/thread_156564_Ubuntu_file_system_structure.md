---
title: "Ubuntu file system structure"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by frio on 2006-04-07
Can anyone point me to a post or document that explains the file system structure in Ubuntu linux? I have been trying to grasp all the concepts, functions, and locations of different files/folders and am slowly learning but it sure would be nice if there were some type of reference document I could use. The more specific the better but anything at this point would be helpful.

Thanks in advance.

---

### Post by benfinkel on 2006-04-07
I would also love to read a short summary of this.

Maybe something that just gave a brief overview of what the different naes are meant to be, like etc, usr, bin, src, etc...

Some of them I know, but some are a little more cryptic.

On the other hand I'm a Buffalo Bills fan, so I won't be able to associate with you anymore ;) 

-Ben

---

### Post by pbaehr on 2006-04-07
There is this:

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by benfinkel on 2006-04-07
Thanks Pb,

That's a good place to start!

-Ben

---

### Post by pbaehr on 2006-04-07
My pleasure.

There is also this article:
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

It goes into a little more detail.

---

### Post by frio on 2006-04-08
Thanks for the links! Should be a big help.

---

### Post by jrib on 2006-04-08
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html) is good too

---

### Post by 5-HT on 2006-04-08
Here's a brief overview from the Wiki (not as detailed as some of the links above).

[Ubuntu Wiki: Filesystem Tree Overview]("https://wiki.ubuntu.com/LinuxFilesystemTreeOverview")

---

### Post by frio on 2006-04-08
I've found this:
[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-fhs]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s-fhs")
in the /etc/init.d/readme
Not quite the perfect quick reference but it does get into the workings of init.d and rcX.d folders which is what I am most interested in and confused about.

I am thinking that these may be the key to allowing a VNC connection without having to be logged into Unbuntu first. Maybe having xinetd start on bootup instead of at log in. Maybe this thinking is way off but, hey, I am a newbie.

thanks for all the help guys...

---

