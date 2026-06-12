---
title: "NFS - Network File Sharing"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-09
Hi,

I am trying to network 2 computers, both running ubuntu 6.06. They are connected via a shared router.

NFS - Network File Sharing seems to be the default sharing method but nothing I have read makes much sense.

I want one computer to have access to another computer. 

I need a step by step guide to set up a server and a step by step guide to set up a client.

Thanks.

---

### Post by IYY on 2006-06-09
I followed these instructions and everything worked well:

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

---

### Post by aragorn2909 on 2006-06-10
Or [this]("http://nfs.sourceforge.net/nfs-howto/") one

---

### Post by u.b.u.n.t.u on 2006-06-10
Thank you IYY. I now have my two ubuntu boxes networked.

* for anyone doing a search, here are some notes based on IYY's link.

There are 3 stages.

1.  Download the software on both machines, server and client.
2. Set up the server.
3. Set up the client.

* Set up the server.
[path location to what is being shared] [IP of client][permissions]
"/home/czar/tmp 192.168.1.1/24(rw,no_root_squash,async)"

* Set up the client.
You need to make a directory that will access the server.
[mount IP of server : path location of what is being shared] ~/[mount in this directory]
"sudo mount 192.168.1.2:/media/hdc5/music ~/music"

* Three things to remember.
The server needs the client IP.
The client needs the server IP.
Make sure the server firewall allows the client IP access.

---

### Post by IYY on 2006-06-10
Also, don't forget that if you want it automatically mounted, just add this line to /etc/fstab:

```
192.168.0.1:/somelocation  /mnt/mountpoint    nfs          rw            0    0
```

Where 192.168.0.1 is replaced with the server's IP, /somelocation is replaced with the share's location, and /mnt/mountpoint is the mountpoint on the local machine.

---

### Post by u.b.u.n.t.u on 2006-06-15
I finally had time to troubleshoot the line code for fstab. It should be as follows:

```
192.168.0.1:/somelocation  /fullpathto/mountpoint   nfs   rw  0   0
```

NOTES

server side line code explained
192.168.01 = ip of the server (the box with the data you want to access)
somelocation = path to the folder containing the server data you wish to access

client side line code explained
fullpathto/mountpoint = path to the folder that will open to see the server data

Important
You need to reboot for the changes to take effect.

---

### Post by CameronCalver on 2006-06-16
woudnt ssh be alot easyer

---

### Post by Dubbayoo on 2006-06-26
[QUOTE=CameronCalver]woudnt ssh be alot easyer[/QUOTE]

as a file server replacement? Yeah, that'd be no.

---

### Post by IYY on 2006-06-26
> You need to reboot for the changes to take effect.

Or just

```
sudo mount /fullpathto/mountpoint
```

---

### Post by syncdram on 2008-02-25
Hi mabey somebody can help.  I have 3 computers all running ubuntu. All 3 networked. From this computer i can access my other shares. When im on the other computers to access the shares on this computer i can see the shares but when i open them i get a error message downloads cannot be opened perhaps this was deleted. Every thing is configured using samba. Can anyone help. This problem just popped up.:guitar:

---

### Post by rolandixor on 2008-06-11
So, let me get this straight, I can use Samba for sharing on two ubuntu systems? cause it won't work for me so far!

---

### Post by Genecks on 2008-07-02
For those playing with NFS and various filesystem, here is some knowledge.

I've been looking more into NFS, and it appears to have problems with NTFS and other filesystems (TMPFS/AUSFS). 
It seems to work well when it comes to EXT2/EXT3, but for some others it can be a problem.
I don't think the way NFS sees the live-cd filesystem as EXT2/EXT3.

[http://nfs.sourceforge.net/#faq_c6](http://nfs.sourceforge.net/#faq_c6)

There might be a way to hack all of that by creating a virtual filesystem, but I wouldn't know off hand.

If you keep getting permission denied, then read the FAQ and the howto at sourceforge.
I suspect the above link will lead you farther.

In terms of NTFS, there is a person named "Vladmir" around here that wrote a workaround. The tutorial may be in Spanish, but such things can be translated with online tools, such as babelfish. That thread seems fairly recent, about a month recent.

I suggest using something like Debian-Live if you can't get these things sorted out right away.
I haven't tried Debian-Live, but I suspect Debian has this FUSE/NTFS thing figured out.

---

