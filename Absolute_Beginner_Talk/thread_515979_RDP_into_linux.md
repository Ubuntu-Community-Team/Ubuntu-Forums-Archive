---
title: "RDP into linux"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-08-02
I can RDP into a windows box from Ubuntu. I can remote desktop a Ubuntu machine from Ubuntu.

Can I remote desktop (control) from Ubuntu to Windows? Can I RDP from Windows into an Ubuntu box? What would I need to install and/or configure to make this happen if it is possible. Keep in mind I am still a newbie to Linux.

Warm Regards,

Joe Hildreth

---

### Post by zeekay on 2007-08-02
I use **x11vnc** server to remote control my ubuntu from anywhere. The only thing you'll need to do it, is a  vnc client. Though it's not the best alternative, fulfill my needs.

---

### Post by fastpakr on 2007-08-02
> **wjhildreth said:**
> I can RDP into a windows box from Ubuntu. I can remote desktop a Ubuntu machine from Ubuntu.

Can I remote desktop (control) from Ubuntu to Windows? Can I RDP from Windows into an Ubuntu box? What would I need to install and/or configure to make this happen if it is possible. Keep in mind I am still a newbie to Linux.

Warm Regards,

Joe Hildreth
I'm a little confused by the way you phrased that, but basically...
The easiest way to remote to a Windows box is using the built in Remote Desktop Connection software to initiate an RDP or VNC session.
The easiest way to get from a Linux or Windows box INTO an Ubuntu box is to activate the Remote Connection options to create a VNC server.

---

### Post by bodhi.zazen on 2007-08-02
> **wjhildreth said:**
> I can RDP into a windows box from Ubuntu. I can remote desktop a Ubuntu machine from Ubuntu.

Can I remote desktop (control) from Ubuntu to Windows? Can I RDP from Windows into an Ubuntu box? What would I need to install and/or configure to make this happen if it is possible. Keep in mind I am still a newbie to Linux.

Warm Regards,

Joe Hildreth

Yes, you can RDP into a window box from Ubuntu.

[http://easylinux.wordpress.com/2006/04/21/connecting-to-windows-from-ubuntu/](http://easylinux.wordpress.com/2006/04/21/connecting-to-windows-from-ubuntu/)


It is under terminal server client.


For security it is best to use vnc and if you  are outside of your LAN , tunnel over ssh.

I like to ssh Ubuntu-to-Ubuntu, you can -Y to forward X ...

GDM: [http://doc.gwos.org/index.php/VNC_GDM](http://doc.gwos.org/index.php/VNC_GDM)

	Remote X: [http://ubuntuforums.org/showthread.php?t=279069](http://ubuntuforums.org/showthread.php?t=279069)

	Over SSH : [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

	Reverse VNC : Remote access:
		[http://www.ubuntuforums.org/showthread.php?t=299489](http://www.ubuntuforums.org/showthread.php?t=299489)

SSH: [http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

---

### Post by wjhildreth on 2007-08-02
In my limited experience. This is what I believe I can do.

I am able to use the RDP client in Ubuntu to do a remote logon in Windows. I am not able to do any remote control (taking over the desktop) from ubuntu to a windows machine.

I am able to take over the desktop in Ubuntu from another Ubuntu machine (move the mouse launch applications etc.) But I do not know how to do a remote login from Ubuntu to Ubuntu.

I just don't know how to exaplain it better. How do I set up a vnc server and where do I go for information?

Regards,

Joe

---

### Post by wjhildreth on 2007-08-02
Sorry, I posted before seeing all your post. I will check out the links. Thanks.

Joe

---

