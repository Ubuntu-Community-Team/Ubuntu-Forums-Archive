---
title: "Virtual Server and Ubuntu and VM Additions"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by lex3001 on 2007-02-11
I am using MS Virtual Server 2005 R2 and have just installed Ubuntu 6.06 Server as a guest OS.

I would like to install MS Virtual Additions for Linux, which I have installed on the host -- so I have mounted the ISO as a drive on the guest machine. In other words, at this point, Ubuntu should think there is a CD in the drive which has VM Additions on it.

I couldn't see any cd files anywhere -- "ls /media/cdrom" provides no ouput. So I hunted around and found the VM Additions readme which assumed I already mounted and found the cdrom. Then I found this link which gave me hint of hope: [http://staff.ywammadison.org/davidg/feed/](http://staff.ywammadison.org/davidg/feed/) but the mount command did not work, yes I used sudo and it compled about the wrong format of something-or-other.

So I cobbled this together from several internet searches and it seemed to actually mount:

sudo mkdir /p /dos
sudo mount -t iso9660 /dev/cdrom /dos

Then I could ls /dos and see several files that looked like what I was hoping for. With
ls -al /dos
I now see the contents of the iso.
But if I try to run the install script or even just copy the files to another location I get Input/Ouput error. During some of my other attempts I got something along the lines of Buffer I/O error also.

Any idea what I am doing wrong? Better yet, any idea on how to get this to work?

Thanks!

---

### Post by skids48 on 2008-03-19
The VM Additions for Linux are only for Red Hat and Suse. They don't work on Ubuntu.

---

### Post by lex3001 on 2008-04-07
Fine, but I should still be able to mount an ISO, regardless of what the content is.

---

