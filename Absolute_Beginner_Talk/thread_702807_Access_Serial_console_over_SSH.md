---
title: "Access Serial console over SSH"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by dualE5335 on 2008-02-20
Hi All-
Is it possible to SSH into a box, then (from within that SSH session) view the output of a serial console on another box.

Would look something like this
me<==ssh==>box1<==serial==>box2

I'd like the ability to read output and issue commands to both boxes.

Am I dreaming here?

( I was able to find a post that would get me half-way to where I'd like to be [http://ubuntuforums.org/showthread.php?t=688631](http://ubuntuforums.org/showthread.php?t=688631) But this is read only )

Thanks

(if it matters box1 is an nslu2 w/ SlugOS and box2 is Ubuntu Server 7.04)

---

### Post by neurostu on 2008-02-20
when you ssh into box1 it is essentially like you are sitting on a terminal on box 1 so anything you can do on box1 you can do when you ssh into box1. So if you can setup a seriel connection from box1 to box2 then you can setup the connection when you ssh into box1.  If you need some sort of gui then just add the -X to the end of your ssh command and you can then open applications that require a gui like firefox.

---

### Post by dualE5335 on 2008-02-21
I have been able to initiate another SSH connection to box2 over ethernet without problem.
me<==ssh==>box1<==ssh==>box2 

But I'm looking to use the serial console instead of SSH.  Why you might ask, well let me tell ya.  I'm not a fan of interfering with the check-disk every 30 mounts (or whatever the default is).  So occasionally the box will check-disk, but it takes tens of minutes to scan, and since SSHd doesn't load until the scan is complete, to me it looks like the box is hung.  With the serial console I can see the status of the scan, and  know that the box isn't hung (which makes me happy).

Is there a way to initiate a serial console session from within an existing SSH/terminal session?

---

### Post by dualE5335 on 2008-03-17
To answer my own question:

Command line serial console applications:

minicom <-the one i used
microcom
picocom

Looks something like this:
me<==ssh==>box1<==Minicom/serial==>box2

If anyone running an NSLU2(slugOS) is looking for minicom, it's in the repositories use dpkg/ipkg

---

### Post by kevdog on 2008-03-17
What's a serial connection?  What connector do you use for this connection?

---

### Post by dualE5335 on 2008-03-18
> **kevdog said:**
> What's a serial connection?  What connector do you use for this connection?

Serial is a legacy connection found on many server motherboards.

The connector is RS-232 DB9

I use a serial to USB adapter [http://www.amazon.com/Keyspan-Speed-Serial-Adapter-USA-19HS/dp/B0000VYJRY/](http://www.amazon.com/Keyspan-Speed-Serial-Adapter-USA-19HS/dp/B0000VYJRY/)

To connect to an NSLU2 [http://www.amazon.com/Linksys-Storage-Link-Drives-NSLU2/dp/B0001FSCZO](http://www.amazon.com/Linksys-Storage-Link-Drives-NSLU2/dp/B0001FSCZO) to my ubuntu server.

The NSLU2 has low power consumption, and near zero noise, the server has high power consumption and high noise, both are in a bedroom.

The server is powered off when not serving/number crunching.  The NSLU2 initiates Wake-On-Lan (WOL) when the server is needed, the serial connection is to watch the server startup messages and provide a console if needed.

---

