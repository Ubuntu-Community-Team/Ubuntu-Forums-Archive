---
title: "Running out of disk space?!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-12-11
**FYI:** 80GB drive, w/ 9 GB root partition and 63 GB home partition

It all started yesterday evening when I got a warning that disk space was low on my root partition. After I investigated a bit, I found that my backup software had somehow set itself to backup the directory *where it stored the backup files*. So every time it went to back up my files, it archived all the previous backups as well.  :-(  So I deleted all but the most recent backup and changed the settings of my software to fix the problem. However, I am still getting weird errors about low disk space. 

If I right-click on my filesystem and go to Properties, the pie chart shows me that I'm using less than half of my root partition, which is true.

When I tell Disk Usage Analyzer to scan my filesystem, though, it seems like it's counting my home partition as a part of the root partition, and thus acting as if my root partition is full when it isn't. I've cleaned out /var/log and /var/cache a few times, but nothing seems to help.

I don't know what could be happening here, I haven't had a problem like this before.

I can't even save screenshots to attach lol

HALP!

---

### Post by rockinlinux on 2007-12-11
have you tired to "show hidden files", there should be a folder called .trash-something. go in there and see if there are files. if there is than highlight them and do shift+delete to actually delete them.

---

### Post by rockinlinux on 2007-12-11
o and do the show hidden thing in our root partition, right when you click the file system.

---

### Post by hackle577 on 2007-12-11
No, there are no hidden files in /

---

### Post by betes on 2007-12-11
what about just emptying your trash

---

### Post by hackle577 on 2007-12-11
Did it. I think the problem is that Ubuntu is counting my /home partition when it shows me the avaiable memory for the root partition, but it shouldnt, right? They're two seperate things.

---

### Post by SupaSonic on 2007-12-11
try /home/.Trash or /home/.Trash-your_username

---

### Post by hackle577 on 2007-12-11
/home/.Trash is empty

I don't think it's actually a low disk space problem, I think Ubuntu just seems to be acting that way because it's counting my /home partition in with my root partition when it checks available memory. Is there any way to verify or eliminate this theory?

---

### Post by philinux on 2007-12-11
I like the system-monitor view of my disk space. Run it then click on File Systems tab see what that shows up.

---

### Post by SupaSonic on 2007-12-11
Post the output of 'df -h'

---

### Post by rockinlinux on 2007-12-11
> **hackle577 said:**
> No, there are no hidden files in /


sorry i meant in your /home :oops:

---

### Post by hackle577 on 2007-12-11
> **philinux said:**
> I like the system-monitor view of my disk space. Run it then click on File Systems tab see what that shows up.

SysMon shows my filesystem as it really is:

partition  =  used / total (in GB)

/           =  3.4 / 9.2    (39%)
/home  =  7.0 / 63.3  (11%)

---

### Post by rockinlinux on 2007-12-11
hmmm....so i wonder why your getting the error....thats a little strange

---

### Post by hackle577 on 2007-12-11
df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  3.5G  5.3G  40% /
varrun               1008M   84K 1007M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  108K 1007M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              64G  6.9G   54G  12% /home
overflow              1.0M  1.0M     0 100% /tmp

```

---

### Post by SupaSonic on 2007-12-11
Well this doesn't look good. 
overflow              1.0M  1.0M     0 100% /tmp

try cleaning out your /tmp maybe?

---

### Post by hackle577 on 2007-12-11
I saw that and just cleared it out.

---

### Post by philinux on 2007-12-11
I'd do a reboot now and see if the errors stop.

Check also /var/log/message.log when you've rebooted.

---

### Post by SupaSonic on 2007-12-11
Ahem... That's weird. Maybe Gnome/KDE - whichever you're using is going nuts. Try logging out and restarting the x server with Ctr+Alt+Backspace if you haven't done this already.

---

### Post by hackle577 on 2007-12-11
Alright, I rebooted. I was able to log in and get to the desktop, but then this:

"Internal error: Failed to initialize HAL"  :-(

I couldn't connect to the Internet so I'm currently on a Live CD.

---

### Post by rockinlinux on 2007-12-11
thats not good...but i have no idea on what to do. sorry :(

---

### Post by SupaSonic on 2007-12-11
oooh it sucks.

Sorry, I can't help either.

---

