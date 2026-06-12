---
title: "How to remote observe an Ubuntu Feisty desktop?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2007-09-01
I live 160 km from my father, and I would like to observe his desktop on my screen,
so that I can teach him how to play Freeciv.

For now, I don't need anything but the ability to silently observe his screen.
He and I can talk by phone.

(I am aware that Freeciv is available on Windows, and that I could use Windows XP Remote Control for this, or any number of Windows-based third-party apps for remote observation, but I would like to keep it Ubuntu to Ubuntu as Freeciv runs much better on native Linux.)

Thanks to anyone for any guidance!

---

### Post by splintercellguy on 2007-09-01
VNC? Though probably a bit slow. You could make screen capture videos with XVidCap, not sure of the quality.

---

### Post by wormser on 2007-09-01
Everything you need is built into Ubuntu.  I recommend that it is tunneled with ssh.  We will start with what needs to be done on the remote end.

System> Preferences> Remote Desktop.  Check allow other users to view your desktop.  Choose other options like ask for confirmation and require a password if you want.

Since we are going to tunnel our connection with ssh you need to set up an account on the remote machine.  System> Administration> User and Groups.

Now we need to open a port on the router's firewall.  Since we are using ssh open port 22.  A guide for your router can be found [here]("http://portforward.com/english/routers/port_forwarding/routerindex.htm").

On your side open a terminal.  Applications> Accessories> Terminal.

```
ssh -L 5900:localhost:5900 username@remoteIP.com
```

Applications> Internet> Terminal Server Client.  Under computer use localhost:5900, Protocol VNC, user name and passord if set up.  Click connect and there you go.

---

### Post by wormser on 2007-09-01
> **splintercellguy said:**
> VNC? Though probably a bit slow. You could make screen capture videos with XVidCap, not sure of the quality.

You are right about VNC being slow.  There is another option with [NX]("http://www.nomachine.com/download-package.php?Prod_Id=1").  It is suppose to be faster and encrypted so there is no need for ssh.  Here is a [link]("http://www.nomachine.com/installation.php") for set up directions.

Update:

If you decide to use FreeNX then follow this [guide]("http://ubuntuforums.org/showthread.php?t=467219").

---

### Post by Average_Joe on 2007-09-02
> **wormser said:**
> wormser wrote:

A guide for your router can be found at:
[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)




wormser:
Thank you for your assistance.  I'm going to be giving your instructions a shot!
I wanted to write here for the benefit of others who may find this thread, and correct 
the link (I corrected it above, in this quote post)
for the router guides.  That is also very useful.

(In your post above, the link as initially hyperlinked has extra characters leading
to a 404 error page or whatever.)

Again, thanks!!

---

