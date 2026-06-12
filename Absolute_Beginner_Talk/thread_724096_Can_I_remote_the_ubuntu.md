---
title: "Can I remote the ubuntu ?"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by My_Ausweis on 2008-03-14
Dear All

Can I remote ubuntu from outside ? if yes, what program should I install in ubuntu ?


Thx

L.M

---

### Post by (((X))) on 2008-03-14
tightvncserver
or vnc4-server
vnc-server is also an option.
then you need a client to connect to server.
I can recomend ultravnc for windows.

---

### Post by njparton on 2008-03-14
You can enable remote desktop via the administration menu (can't remember precisely where at the mo) and then install an X client in windows (if that's where you'll be connecting from). I can recommend Xming as a client.

---

### Post by (((X))) on 2008-03-14
> **njparton said:**
> You can enable remote desktop via the administration menu (can't remember precisely where at the mo) and then install an X client in windows (if that's where you'll be connecting from). I can recommend Xming as a client.

This is where remote desktop is located
[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

---

### Post by njparton on 2008-03-14
> **(((X))) said:**
> This is where remote desktop is located
[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

Thanks, I'm not in front of ubuntu at the mo...:)

---

### Post by Emerzen on 2008-03-14
I've found NoMachine to be the best remote solution, and it uses SSH to tunnel the connection so it's more secure to than VNC.  Google NoMachine for the website.  It's proprietary but free for Linux users.  It has free clients that work well in Linux or Windows.

---

### Post by njparton on 2008-03-14
> **Emerzen said:**
> I've found NoMachine to be the best remote solution, and it uses SSH to tunnel the connection so it's more secure to than VNC.  Google NoMachine for the website.  It's proprietary but free for Linux users.  It has free clients that work well in Linux or Windows.

That's not necessary for a secure LAN, gnome has a built in server (I think it's called vino).  Just enable it as described above and away you go.

---

### Post by hyper_ch on 2008-03-14
you can install the openssh server and connect with a terminal to it

---

### Post by GoCool on 2008-03-14
> **(((X))) said:**
> This is where remote desktop is located
[http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

Hi... the link shows me a blank page.:(

---

