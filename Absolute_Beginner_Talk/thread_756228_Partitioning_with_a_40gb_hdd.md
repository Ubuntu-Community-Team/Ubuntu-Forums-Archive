---
title: "Partitioning with a 40gb hdd"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by SigmaHog on 2008-04-15
I have no room on my hdd because I have almost over 8gb of just songs on my hdd, I can get it to partition about 6 gb but it crashed for some reason... also i'm using the live cd, i dunno if that matters

my partitions look like this

Partition        Filesystem   Size            Used         Unused    Flags
/dev/sda1     - fat16        - 39.19MiB  -7.48 MiB  - 31.71MiB
/dev/sda2     - ntfs          - 31.17GiB  -23.58GiB  - 7.59GiB   boot
/dev/sda3     - fat32        - 4.64GiB    - 3.57GiB   - 1.07GiB
unallocated   -unallocated- 7.84MiB       ---               ---

could anyone tell me what this means and how I need to go about partitioning so I can get about 6GB for Ubuntu install, i'll mess around with it later to transfer all the songs over and make it bigger but for now I just want to install.

---

### Post by Joeb454 on 2008-04-15
You won't need to transfer all the songs over unless you want to go 100% linux :)

And have you tried partitioning the drive from within Windows? Sometimes it helps because it'll moan due to unmovable system files if you do it from a Live CD

---

### Post by tvtech on 2008-04-15
ok first things first if your running windows XP  you need to do a little house keeping.  

I started my foray into ubuntu on a 30gb hitachi travelstar

right click your my computer and go to properties.  
inside the dialog go to advanced>performance>settings>advanced>virtual memory>change 

and turn it to zero  

then under the same properties dialog box go to system restore and turn monitoring off for your windows drives.  Then reboot. and defrag until you can defrag no more.  this will free up a lot of space and move most of the files to a more desirable location. then you can go back to installing ubuntu.  or ..... go to [gparted]("http://gparted.sourceforge.net/livecd.php") download the live cd and manage your partitioning with this.  it's the same program ubuntu uses but it's a different front end.  I like it a lot better.  and it's a live cd YAY  if ubuntu won't do it for you try this it should make things go a little better.  after you've set up your partitions for both /  and swap your free to have fun with installing ubuntu!

---

### Post by SigmaHog on 2008-04-15
I tryed to partition my hd with swissknife v3 and it's telling me I can't partition because the drive contains windows systems files (duh) and won't let me partition because of security reasons... eff bill gates, i wanna partition my hd!!!!

---

