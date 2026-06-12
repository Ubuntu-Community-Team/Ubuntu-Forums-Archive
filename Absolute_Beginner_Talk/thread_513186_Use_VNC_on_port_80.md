---
title: "Use VNC on port 80"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2007-07-30
Hi
How can i use vnc over port 80? i would like to make vnc listen on 80 if it is possible.
Thanks
wehttamb

---

### Post by DBStevens on 2007-07-30
* VNC uses port 5900 by default
    * Specifying a different port:
          o Server: vncserver -rfbport port-number-to-use
          o Client: vncviewer serverIP:port-number-to-use 
      Note that if you use a port number less than 100 it will add 5900 to the number. Thus to use a port number less than 100 use a negative number. i.e. to specify port 80: vncviewer serverIP:-5820 

According to: [http://www.yolinux.com/TUTORIALS/VNC.html](http://www.yolinux.com/TUTORIALS/VNC.html)

---

