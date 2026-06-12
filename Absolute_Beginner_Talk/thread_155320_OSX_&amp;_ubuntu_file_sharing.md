---
title: "OSX &amp; ubuntu file sharing"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-04-04
Hi,

i just got file sharing going b/t my osx10.3.9 box and my ubuntu box.  here's what i did.  it was easy.

**disclaimer**
i'm a noob and just got this to work so thought i'd share it with my fellow noobs.  if there is something insecure, bad, immoral, reproachable, or generally distasteful with this method, please advise.
****


**in osx**:  

go to System Preferences > Sharing, then click the "Remote Login" checkbox.

now you should see, at the bottom of the window, an address to login with.  it'll start with "ssh" then your username on the mac, then the "@" symbol, followed by a bunch of numbers (your ip address).  write this down.  it'll look something like this: "ssh joejoe@192.100.624.44".  write the login address down.



**now go to your ubuntu pc:**

click Places > Connect to Server

Service type: select "SSH"
Server: <your login address from the mac>

click connect.

now you should see a little orange disk icon on your desktop (on your ubuntu pc) showing all of your mac files.  you should be able to drag and drop between the computers.

---

### Post by htinn on 2006-04-04
I would probably set up an FTP server on Ubuntu:

[http://doc.gwos.org/index.php/FTP_Server](http://doc.gwos.org/index.php/FTP_Server)

---

### Post by johnnymac on 2006-04-04
Look up how to setup samba server and share a specific directory on you linux box...then from the your mac should have no problems getting to the folder your sharing.

Try this...

[http://help.ubuntu.com/starterguide/C/ch07.html#sect-samba-server](http://help.ubuntu.com/starterguide/C/ch07.html#sect-samba-server)

---

### Post by takayuki on 2006-04-04
thanks for the replies htinn and johnnymac.  i got it going and edited my original post with the instructions.  is my method correct?  it's working great.

---

