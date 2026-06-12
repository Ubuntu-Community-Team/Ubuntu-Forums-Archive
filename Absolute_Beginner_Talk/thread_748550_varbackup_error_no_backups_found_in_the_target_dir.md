---
title: "/var/backup error: no backups found in the target directory"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by mlnease on 2008-04-07
Hello All,

I've been trying to use sbackup but have been receiving the above error message (error: no backups found in the target directory) each time I've attempted to restore, even though the backups are visible in /var/backup if I navigate there.  

I hope this is the correct forum.  I've searched for and found similar problems on line but most are several years old and none exactly like this one.  Any assistance would be greatly appreciated.

OS  			    Ubuntu 6.06
kernel  	           2.6.15-51-686
GNOME version	  2.14.3 - Ubuntu (2006-07-31)
Xorg version  	      7.0.0
CPU			    Intel(R) Pentium(R) 4 CPU 2.80GHz

Here is the terminal output from sbackup/config, if it's of any use:

W: Unknown or incomplete directory format at:  /var/backup/2008-04-06_13.25.16.513063.ubuntu.ful
I: Securing permissions at:  /var/backup/2008-04-06_13.24.43.737888.ubuntu.ful
W: Unknown or incomplete directory format at:  /var/backup/2008-04-06_13.24.43.737888.ubuntu.ful
I: Securing permissions at:  /var/backup/2008-04-06_11.35.10.148395.ubuntu.ful
W: Unknown or incomplete directory format at:  /var/backup/2008-04-06_11.35.10.148395.ubuntu.ful
I: Securing permissions at:  /var/backup/2008-04-06_10.30.03.194252.ubuntu.ful
W: Unknown or incomplete directory format at:  /var/backup/2008-04-06_10.30.03.194252.ubuntu.ful
I: Securing permissions at:  /var/backup/2008-04-05_17.56.06.126684.ubuntu.ful
W: Unknown or incomplete directory format at:  /var/backup/2008-04-05_17.56.06.126684.ubuntu.ful
I: Securing permissions at:  /var/backup/2008-04-05_17.36.54.526487.ubuntu.ful
W: Unknown or incomplete directory format at:  /var/backup/2008-04-05_17.36.54.526487.ubuntu.ful
I: Securing permissions at:  /var/backup/2008-04-05_11.01.12.028975.ubuntu.ful
W: Unknown or incomplete directory format at:  /var/backup/2008-04-05_11.01.12.028975.ubuntu.ful
I: Securing permissions at:  /var/backup/2008-04-04_20.11.11.748306.ubuntu.ful
W: Unknown or incomplete directory format at:  /var/backup/2008-04-04_20.11.11.748306.ubuntu.ful

Thanks In Advance,

mike

---

### Post by renfrew on 2008-04-14
what results do you get for 'ls -al /var/backup' from the terminal?

it looks like whatever user you're using to do the backups doesn't have read priviliedges for the files and/or for /var/backup itself ...

---

### Post by mlnease on 2008-04-14
> **renfrew said:**
> what results do you get for 'ls -al /var/backup' from the terminal?

it looks like whatever user you're using to do the backups doesn't have read priviliedges for the files and/or for /var/backup itself ...

Thanks very much, Renfrew--I'm afraid I'm away from my Ubuntu box for a couple of weeks.  I made sure of my privileges for files in question but won't be able to get terminal output for 'ls -al /var/backup' until I return.  I'll get back to you then, thanks again very much for the response.

mike

---

### Post by sostenible on 2008-04-24
I had a similar problem when attempting to restore my sbackup copies (done under Ubuntu 7.10) after making a clean install of Ubuntu 8.04.

I solved the problem entering the command line, going to my backup directory and typing the following:

sudo chmod 777 *.inc

sudo chmod 777 *.ful

I then tried again with sbackup restore and found out that it would detect all my backup copies.

I first installed the latest .ful and then repeated with each .inc starting from the day after the .ful I had restored.

I hope it also works for you!!

---

### Post by mlnease on 2008-04-25
Hi S,

Thanks for this.  I'm away from my Ubuntu box for a few more days and will have another look when I return.

Thanks Again,

mike

---

### Post by mlnease on 2008-05-03
Thanks Again, Renfrew,

The only output I get from "ls -al /var/backup" is
"> "

I have discovered, though, that if I look in root Nautilus I can see all my backup files.  So I think you're probably right about a permissions problem.  I'll repost if I'm able to figure it out.

mike

---

### Post by mlnease on 2008-05-03
> **sostenible said:**
> I had a similar problem when attempting to restore my sbackup copies (done under Ubuntu 7.10) after making a clean install of Ubuntu 8.04.

I solved the problem entering the command line, going to my backup directory and typing the following:

sudo chmod 777 *.inc

sudo chmod 777 *.ful

I then tried again with sbackup restore and found out that it would detect all my backup copies.

I first installed the latest .ful and then repeated with each .inc starting from the day after the .ful I had restored.

I hope it also works for you!!

Hello Again,

In a root terminal I cd'd to /var/backup and entered: 

sudo chmod 777 *.inc

I received the following error message:

chmod: cannot access `*.inc': No such file or directory

Have I taken your code too literally?

mike

---

### Post by mlnease on 2008-05-10
Thanks Again Renfrew and Sostenible,

I was able to resolve my problem by opening /var/backup with gksudo nautilus and changing owner, group and allowing 'write' and 'execute' permissions.  Simple Backup/Restore works fine now.

mike

---

