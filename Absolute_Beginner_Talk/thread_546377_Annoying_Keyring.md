---
title: "Annoying Keyring"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-09-08
I don't care if this was asked before, but how do you stop that annoying keying from popping up when you login to ask for the password to enable your wireless network connection that's been WEP enabled.???  

  Thanks for the wonderful people who can help me and who are all part of this wonderful open source utopia.

---

### Post by overdrank on 2007-09-08
> **Xorg.conF said:**
> I don't care if this was asked before, but how do you stop that annoying keying from popping up when you login to ask for the password to enable your wireless network connection that's been WEP enabled.???  

  Thanks for the wonderful people who can help me and who are all part of this wonderful open source utopia.

Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=535363&highlight=how+to+disable+keyring](http://ubuntuforums.org/showthread.php?t=535363&highlight=how+to+disable+keyring)

---

### Post by Xorg.conF on 2007-09-08
Thx for the link, seems a lot of work for just a simple thing like this.

---

### Post by lisati on 2007-09-08
> **overdrank said:**
> Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=535363&highlight=how+to+disable+keyring](http://ubuntuforums.org/showthread.php?t=535363&highlight=how+to+disable+keyring)

After further research on my bookmarks I'd suggest the following links (which worked on my machine) - much quicker to do both, which take about 1 minute (not counting system restart)

[http://ubuntuforums.org/showpost.php?p=2776663&postcount=1](http://ubuntuforums.org/showpost.php?p=2776663&postcount=1)
[http://ubuntuforums.org/showpost.php?p=2776673&postcount=2](http://ubuntuforums.org/showpost.php?p=2776673&postcount=2)

---

### Post by dwhitney67 on 2007-09-08
If you do not mind typing your password one more time, I think the solution is to delete the keyring file in your gnome settings.  Once you login again (to the wifi router), the file will be recreated and then hopefully it will be the last time you have to type your password again.

To delete the file, run this command:

$ rm -f ~/.gnome2/keyrings/default.keyring

P.S.  I have never had to do this with my Ubuntu distro, but I did have to with my Fedora Core 5 distro... which also uses Gnome.

---

### Post by Xorg.conF on 2007-09-08
thx that did the job, but it takes a noticeable amount of time longer to login, but i guess I'll to deal with it.

---

### Post by dwhitney67 on 2007-09-08
The "longer time" could have been something else delaying your connection, or maybe just the file being created.  I do not think you will experience the delay again.

---

