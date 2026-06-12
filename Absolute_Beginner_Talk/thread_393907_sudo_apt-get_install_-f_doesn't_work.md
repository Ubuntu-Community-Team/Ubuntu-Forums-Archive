---
title: "sudo apt-get install -f doesn't work"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by wog on 2007-03-26
Updates today, but one package is listed as being broken.

"sudo apt-get install -f" returns this error message:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 13189:
 invalid package name (
E: Sub-process /usr/bin/dpkg returned an error code (2)

"dpkg --configure -a" produces the error message:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 13189:
 invalid package name (

I tried using the 'broken' filter in Synaptic and it refuses to show me the list.
apt-get seems to reference something called xmessage.

What do I do next?

---

### Post by adam s on 2007-03-26
It may be worth trying :

sudo dpkg --configure -a

This rebuilds all the package dependencies (I think)

I do not know if it will work - but it is where I would start.

Adam.

---

### Post by wog on 2007-03-27
I tried "sudo dpkg --configure -a".

I got this error message:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 13189:
invalid package name (
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any other ideas of what I should do?

---

### Post by aysiu on 2007-03-27
Try this: ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo aptitude update
```

---

### Post by wog on 2007-03-27
The mv command line worked perfectly.
Then I tried the next line:

james@linux-box:/usr/share/doc$ sudo aptitude update
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

What next?

---

### Post by msak007 on 2007-03-27
The output tells you which line in that file it doesn't like, but chances are it could've corrupted more than one line so rather than deleting lines, the best bet is what aysiu already recommended and move / delete the corrupt file. But you still need a dpkg status file to do anything. You've already moved the corrupted file to a .old file, but you should also have a file in that directory called **status-old **(note the dash, this is different than the file you just backed up)**.** dpkg saves a backup of the file before it does anything, so that should be a good file. Try

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```and then try to update / upgrade.

---

### Post by az on 2007-03-27
> **wog said:**
> The mv command line worked perfectly.
Then I tried the next line:

james@linux-box:/usr/share/doc$ sudo aptitude update
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

What next?

You can try 

sudo dpkg clear-avail


Quote:
--clear-avail 


dpkg will clear the available packages file of all information when given this option. There are times when the current file has been corrupted or otherwise broken in some fashion. This can happen for a number of reasons. 

The most common reason is that it has gotten updated from a "broken" Packages file. In extreme cases, changes to the file format have resulted in files that failed to work with the old version of dpkg. This requires that the new version be installed before the file can be fixed. Cleaning out this file allows the upgrade to go forward. Once completed the available file can again be updated with the new Packages format and the installation may progress unhindered. Executing the command: 

dpkg --clear-avail

---

### Post by zvacet on 2007-03-27
**synaptic>edit>fix broken packages**

---

### Post by jdpipe on 2007-03-27
I had this problem too; the solution was to replace 'status' with 'status-old', as mentioned by msak007. Thanks all!

---

### Post by wog on 2007-04-11
This is another example of something that fixed the problem, tho I haven't the faintest clue why.

I replaced status with status.old, and then it just seemed to work again.

But this doesn't make any sense to me, since all I did was rename status to status.old, and then copy it back. Did anything actually change, or is this an example of waving a rubber chicken over the problem until the problem solved itself?

---

