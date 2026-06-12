---
title: "FTP speeds"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by dellinger on 2007-06-10
Hi, I would greatly appreciate any pointers or thoughts here.

I am attempting to transfer several GB of data from one machine to another on my local net. On the "destination" machine I have a Proftpd FTP server set up Ubuntu Fiesty, and enabled it to allow uploads. On the "source" machine I'm running Kubuntu Fiesty and can upload the files via Konqueror. Unfortunately the source machine is laptop, so I don't think I can just pull out the hard drive and temporarily mount it on the destination PC and move over the files (right?).

Both machines are directly connected (i.e., wired) to my router. Over the past couple hours, I have only been able to sustain a transfer speed of around 35-40 KB/s, which would take me at least a few days to transfer all my files. Not cool.

My first guess would be that the router is causing of the slow speeds. However, I can get decent speeds from outside servers (>1 MB/s) from time to time, and would only expect better for internal transfers. I shouldn't have to worry about port forwarding since I'm using the internal IP address for the FTP server. There's hardly any other traffic going on the network, and the router isn't one of the cheap ones. 

Could the Proftpd server just be a little on the slow side (I'm specifically using GPROFTPD)? Could it be Konqueror? Is NFS typically faster than FTP? Or do you think it's the router? Also, note I set up the FTP server on the destination, not the source. It seems backwards now, but once I get the data to the destination, my plan is to keep the FTP server running so I access my data on other machines (just not all at once :)

Both the NFS and direct PC-PC options would require research on my part first, so any thoughts on the best path would surely save me some time. Thanks!

---

### Post by yabbadabbadont on 2007-06-11
Adapters that let you connect a laptop harddrive to a standard IDE cable are pretty cheap (just a few dollars).  That would be the fastest way to get the data over there.  If you have a DVD burner in your laptop, or an external one you can beg/steal/borrow, you could burn DVD's of the data to be moved.  (Plus then you would have a backup :D)

---

### Post by dellinger on 2007-06-11
Ah, I was unaware such adapters existed. Thanks, I'll look into that tomorrow. Unfortunately, only the destination PC has the DVD burner :(

Since I plan to keep the FTP server up and running after all this, I am still a bit concerned about the slow transfer speeds. If anyone has any thoughts, I'd love to hear them.

---

### Post by croto on 2007-06-11
Hi,

what router do you have? So if understand correctly, you have one ftp server running on, say 192.168.1.100, and the client on 192.168.1.101 and you ftp the server like: ftp 192.168.1.100, am I right?

Just to test the network (assuming your hosts are 192.168.1.100 and 192.168.1.101, you can change it to whatever you have), try the following:

In one host (192.168.1.100), type:
```

nc -l -p 9000 > testoutput

```

This will wait for a connection on port 9000 and send the output to the file testoutput. On the other host (192.168.1.101), type
```

nc 192.168.1.100 9000 < file

```
where file is any file you want to transfer. Choose something around 1Mb for test purposes. After it sends, the nc running on 192.168.1.100 should exit and the file testoutput should have received the file "file". Is it so slow as ftp?

---

