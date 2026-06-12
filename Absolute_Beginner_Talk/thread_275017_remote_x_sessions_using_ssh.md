---
title: "remote x sessions using ssh"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-10-10
I have a question regarding x sessions being tunneled through ssh connections. My question is if it's only possible to use this with both the client and the server running an x server or is it possible to run the remote x session only on the server. An example would be if I could log into my linux box from a windows box. Would it be possible to run the remote x session?

I know you can use vnc to do the same thing but im just curious to know if its possible using ssh.

---

### Post by ewl1217 on 2006-10-10
You could use the SSH tunneling you're thinking of by using Cygwin/X on the Windows computer, but that is fairly complicated. You could just do what I do and tunnel a VNC connection over SSH, so you get the security of SSH and the ease-of-use of VNC. If you're interested in that, just let me know, and I'll walk you through it.

---

### Post by snakyjake on 2006-10-10
> You could use the SSH tunneling you're thinking of by using Cygwin/X on the Windows computer, but that is fairly complicated. You could just do what I do and tunnel a VNC connection over SSH, so you get the security of SSH and the ease-of-use of VNC. If you're interested in that, just let me know, and I'll walk you through it.

I'm interested too.  That would be great if you could provide a HOWTO.  :-)

Thanks

---

