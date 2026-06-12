---
title: "How do i use the sudo??"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by linuxfreaks on 2006-06-24
Hello I had a sudo problem and was solved and was something like [this]("http://ubuntuforums.org/showthread.php?t=181102").
I saw the forum and got the answer .


But i saw that i don't have the file called as '*hostname*'.
What should i do to create the file..

---

### Post by lsald on 2006-06-24
The file isn't hostname, its hosts. You can find it in /etc.

---

### Post by linuxfreaks on 2006-06-24
This is what mustard wrote.

> 

While mucking around with your network settings, I would suspect at some stage that you blanked the hostname field and this has affected your /etc/hosts file. It's a common issue that people strike. Without a properly configured hosts file your sudo command will not work. I'll post up a method to fix this problem in a minute when I finish installing my desktop wiki on this new install I'm doing.

-edit-

How to edit the /etc/hosts file (troubleshooting guide)

To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt,
1. Making a backup of misconfigured file
If you really have no idea what you are doing then first make a backup of the file just in case you really muck things up. A misconfigured file is at least a reference you can work from.

Code:
#make a backup
cp /etc/hosts /etc/hosts_backup
2. Editing the misconfigured file
Open up the /etc/hosts file with this command.

Code:
#this will open the hosts file in a command line text editor
nano /etc/hosts 
(To save files in in nano use ctrl + o and to exit from nano use ctrl + x)

The /etc/hosts file normally looks something like this...


Code:
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
What you need to do is to edit the first line so that it contains a hostname for your computer. Mine is called 'slave' as you can see above. You can choose any name you like. The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..


Code:
127.0.0.1       localhost.localdomain   localhost       ubuntu
Additional problems that may be present
An additional issue you might need to look into in some cases, is whether a file exists in the /etc/ folder called 'hostname'. For various reasons, usually related to user intervention, it will sometimes not exist at all, or exists but is a blank file. Normally the /etc/hostname will look like this (using my own host file as an example)..


Code:
slave
If it is absent then you should create a file in /etc/ folder called hostname and edit it to include your chosen hostname.

Command relating to the hostname (I've included this for informational purposes)
An additional command you can look at with regards to hostnames is this command below.

Code:
hostname
#returns the current hostname
hostname <hostname>
#sets the hostname according to the value entered for <hostname>

Here is the forum page 

[http://ubuntuforums.org/showthread.php?t=181102]("http://ubuntuforums.org/showthread.php?t=181102")

Please see the Additional problem present thing.

Now after reading it please tell me how to create a file called as *hostname* in the /etc/ folder. What should i write for that.


I think that this will be solved.. So thanks to all.

---

