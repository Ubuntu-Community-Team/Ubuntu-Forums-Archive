---
title: "HellaNZB problem! Not downloading anything!"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by vjstar on 2007-06-29
Hi,

Ive installed hellanzb 0.13-2 on my ubuntu desktop and I can't get it to download anything... I edited the config file with my server info, I placed a .nzb file in .queue dir, load up the program (*hellanzb.py* I have also tried *sudo hellanzb.py*)

It shows the nzb correctly... but it does not download anything! the ETA in yellow stays to 0.00 forever!

Can someone help me please?
Thanks

---

### Post by roastdawgg on 2007-06-29
this means that HellaNZB is not connecting to your news server. Download one of the GUI Newsreaders like Pan, plug in all of your connection information and test that the connection works. After that post your config file [sanitized of your username and password of course] and I can try to help you out some more.

---

### Post by vjstar on 2007-07-02
> 
vj@vj-desktop:~$ hellanzb 

hellanzb v0.13 (config = /usr/etc/hellanzb.conf, C yenc module)
Exiting: FatalError'>: hellanzb does not have write access to the Hellanzb.STATE_XML_FILE file



What should I do?

---

### Post by vjstar on 2007-07-03
Anyone?

---

### Post by roastdawgg on 2007-07-04
open a terminal, and type:

```
sudo gedit /usr/etc/hellanzb.conf
``` 

scroll down about 20 or so lines and check where you have configured HellaNZB to locate itself. The line will look like: 

```
Hellanzb.PREFIX_DIR = '/media/download/hellanzb/'
```

Make sure you have this set to a drive/location that you have write access to.  To check this simply open another terminal session and type

```
ls -l /path/that/you/found/in/the/file
```

and check what the permissions are for that path. if you are still stuck copy and paste the results of each step here and I can try to see if i can help you out some more.

---

### Post by vjstar on 2007-07-04
> drwxr-xr-x 9 vj   vj       4096 2007-07-03 16:47 nzb


All files/folders have those permissions.

---

### Post by vjstar on 2007-07-06
So... can you help me?

---

