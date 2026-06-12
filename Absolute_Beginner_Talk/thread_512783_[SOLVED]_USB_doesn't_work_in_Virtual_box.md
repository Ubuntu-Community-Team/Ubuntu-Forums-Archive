---
title: "[SOLVED] USB doesn't work in Virtual box"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-29
I was getting an error the other day, but now my USB device simply doesn't show up in the Devices list in Virtualbox.  Is there a trick to this?

---

### Post by DonBucknall on 2007-07-29
Hello,

Have you got the open source version or commercial version?

They are both free but the only thing about the open source version is that usb is not supported.

Hope this helped you.

Don

---

### Post by kc5hwb on 2007-07-29
Interesting, I didn't know there were 2 versions.  How do you tell which is which?

I just looked at the site and I think that I have the Commercial Edition.  It is listed under the Binaries section of this page...
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by DonBucknall on 2007-07-29
I'm fairly new to ubuntu so I'm not really experienced but that was one thing I knew.
I installed virtual box following this url:

[http://ubuntu-forums.org/showthread.php?t=340113&highlight=howto+virtual+box]("http://ubuntu-forums.org/showthread.php?t=340113&highlight=howto+virtual+box")

It worked for me.

I'm sorry I can't help you much further.

Don

p.s. If it isn't to much hassle you might consider a reinstall of virtualbox?

---

### Post by purplearcanist on 2007-07-30
Whenever I click on the settings tab on virtualbox, I get this error:


Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND).The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: Host
Interface: IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: IMachine {0332de0e-ce75-461f-8c6f-0fa42616404a}

and I don't see the usb tab.

Can someone please help get the usb working?

---

### Post by felicity on 2007-07-30
Hi,

I was able to get USB working in VirtualBox by editing this file:

/etc/udev/rules.d/40-permissions.rules

and changing the line for usb devices from 0664 into 0666

I got this information from [this]("http://ubuntuforums.org/showthread.php?t=341740&page=3") post, which might be of further assistance to you.

---

### Post by kc5hwb on 2007-07-30
i could reinstall..... but I would rather try and find some way to fix this one.  As a last resort, I will reinstall.  

Anyone else have an idea on how to get USB to work in Virtualbox?

---

### Post by bodhi.zazen on 2007-07-30
LOL

Yes : [http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices](http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices)

---

### Post by purplearcanist on 2007-07-30
I got the usb thing to show up.  Thanks.:)

---

### Post by bodhi.zazen on 2007-07-30
Threads merged ... Same question ...

---

### Post by kc5hwb on 2007-07-30
> **felicity said:**
> Hi,

I was able to get USB working in VirtualBox by editing this file:

/etc/udev/rules.d/40-permissions.rules

and changing the line for usb devices from 0664 into 0666

I got this information from [this]("http://ubuntuforums.org/showthread.php?t=341740&page=3") post, which might be of further assistance to you.

This worked great, thanks.

---

