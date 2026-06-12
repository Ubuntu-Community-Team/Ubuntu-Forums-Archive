---
title: "How to fix this? Need help, thanks"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by yakitori3 on 2006-07-26
* starting samba daemons...		{fail}
invoke -rc.d: initscript samba, action "start" failed.
dpkg: error processing samba ( --configure):E: samba: subprocess post-installation script returned error exit status 1

---

### Post by yakitori3 on 2006-07-26
This happened after an update - upgrade

---

### Post by JoWilly on 2006-07-26
Try to reinstall samba.

(use synaptic)

---

### Post by yakitori3 on 2006-07-26
I tryed and got this error message:

subprocess post-installation script returned error exit status 1

---

### Post by yakitori3 on 2006-07-26
This is the whole message when I do an apt-get update and upgrade???
I cannot use Easyubuntu because of this error message.
Please any ideas.


Setting up samba (3.0.22-1ubuntu3.1) ...
 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by JoWilly on 2006-07-26
Try to remove samba with synaptic ?

---

### Post by yakitori3 on 2006-07-27
thanks JoWilly a lot
That did the trick.
I hope I can get Samba working later on without the error message
Thanks agtain

---

