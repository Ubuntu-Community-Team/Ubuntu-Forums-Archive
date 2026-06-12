---
title: "Unable to mount Linux network drive with SAMBA"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-05-17
OK, I have successfully installed SAMBA on a PC running Ubuntu, I can ping it by name, and by IP by running "ping 192.168.1.4" or "ping Webserver", both work, however, when I right click on My Computer, on the Windows PC, and click Mount Network Drive, and type "\\webserver\home\myname" or "\\192.168.1.4\home\myname" they both come back saying that "The network path Webserver\home\myname" cannot be found, anyone have advice/a solution?

---

### Post by panzer77 on 2007-05-17
Maybe I don't understand but the drive should all ready be mounted on ubuntu.  Can you access the drive on ubuntu?  Maybe your are trying to map the drive?

---

### Post by Peter1234123 on 2007-05-17
Err. yes, I am trying to map it, wrong choice of words :P

---

### Post by panzer77 on 2007-05-17
Can you see the ubuntu box when you explore your network in windows?

---

### Post by Peter1234123 on 2007-05-17
When I go into Windows file browser, and type \\webserver or \\192.168.1.4, or explore computers on network, I see "Webserver Server (Samba, Ubuntu) (webserver)" and when I click on it, all I see is "Printers and faxes"

---

### Post by panzer77 on 2007-05-17
Try setting up a folder on the ubuntu box or use the existing folder you want to share.  Right click on the folder and go to share folder.  You may also want to check your permissions, you can find that under properties.  Did you setup samba from the command line or use gsambad to configure?

---

### Post by Peter1234123 on 2007-05-17
Command line, through PUTTY

---

### Post by panzer77 on 2007-05-17
gsambad is a pretty handy tool.  It may be useful in troubleshooting.  The GUI tool has tab for shares, plus you can look at your confile.  You will need to run it as root after you get it installed.

---

### Post by Peter1234123 on 2007-05-17
Got it working, had to share the folder, thanks for your help :D.

---

### Post by qpieus on 2007-05-17
After samba is installed you have to also set up samba to share a directory on the network. Have you done that? If not, that's why your windows pc cannot see the linux pc.
This thread may be helpful to you, the person had the same problem you are seeing:
[http://ubuntuforums.org/showthread.php?t=432075](http://ubuntuforums.org/showthread.php?t=432075)

---

### Post by qpieus on 2007-05-17
hah, i see we were responding at the same time but you beat me to it. I see you got it figured out.

---

