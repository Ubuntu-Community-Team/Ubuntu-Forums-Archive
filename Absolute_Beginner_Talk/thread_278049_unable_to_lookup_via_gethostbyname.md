---
title: "unable to lookup via gethostbyname"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by buntolith on 2006-10-15
Hi,

I can not kdesu anymore. 

When I try to run "kdesu adept updater" in Run Command I get the following error message:

"Su returned with an error"

When I try to run "sudo aptitude update" in Konsole I get the following error message:

"sudo: unable to lookup myname-laptop via gethostbyname()"

](*,) 

I use Kubuntu Dapper Drake

Can anyone help me on this one?

---

### Post by CatKiller on 2006-10-16
Have you been messing with your hosts file?

---

### Post by dannyboy79 on 2006-10-16
yep, i did this to. you must have deleted the loopback line from your hosts file. now your computer doesn't know it's own name so it can't do sudo things. i had to boot to a live cd, then do sudo gedit /etc/hosts and change it back to whatever it was before. luckilyt i had made a backup before I messed with it, so i was able to boot to a live cd, then do 
mc /etc/hosts-backup /etc/hosts which will overwrite the bad hosts file with the one that I had backed up. it has to look similar to this:
127.0.0.1 localhost
127.0.1.1 UBUNTU (NOTE: the "UBUNTU" should be the name of your machine when you first installed dapper)
192.168.0.3 UBUNTU
192.168.0.2 WINXP
192.168.0.4 XUBUNTU
192.168.0.5 XBOX1 

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

As you can see I have also added all my other machines as well as it's own ip address since in my smb.conf file I have name resolution being hosts win bcast or something like that. I am not at home so I am not sure.

---

### Post by Iowan on 2006-10-16
I've done the same thing by changing the hostname.  In my case, booting to Rescue mode somehow got the name conflict resolved without changing anything. (A simple reboot might have accomplished the same thing.)

---

### Post by buntolith on 2006-10-16
Hi,

I haven't solved the problem yet but with your help it should be no problemo. This is the status right now.

I have not been playing around with the hosts file - not deliberately anyway. But the file have been damaged somehow and I don't know how?

I tried to boot in safe mode but it didn't solve the problem unfortunately. I don't have a live cd right here either but I do have a Windows partition with FS-Drive installed so I can reach the hosts file without the root permission. This is what I can read in the /etc/hosts file with notepad:

# The following lines are desirable for IPv6 capable hosts

And that's all so there is something strange here. I don't have a backup file either but I will get one for sure. Can anyone help me with what I should write in the hosts file to restore it. I have 6 partitions on my harddrive:

hda1 = windows xp professional
hda2 = ubuntu 6.01
hda3 = kubuntu 6.01
hda4 = logical partition
hda5 = /home
hda6 = swap

By the way, is it wise to do any modifications with notepad in windows?

Thanks a lot for your help...

---

### Post by buntolith on 2006-10-16
One more thing. 

Maybe I could copy /etc/hosts from my ubuntu partition into my kubuntu partition because that hosts file seems to be allright. This is what it says:

127.0.0.1	localhost
127.0.1.1	johan-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Any wise words before I go ahead?

---

### Post by Iowan on 2006-10-16
My opinion (for what it's worth) is that you'd be better off copying an existing **/etc/hosts** file than building one from a Windows box.  Perhaps Ubuntu has gotten around it - but the format used to be different (cr/lf vs cr) between Windows and Linux.

---

### Post by buntolith on 2006-10-16
I started up Windows XP and copied /etc/hosts from my ubuntu partition into my kubuntu partition. I had no problems to reboot Kubuntu and I could get root access again with kdesu. 

Windows XP, Ubuntu and Kubuntu working in perfect harmony. Beautiful...

Thanks for your help...

---

### Post by badwizard on 2008-02-16
I ran into this exact problem right after installing a **completely fresh** version of Kubuntu: whenever I attempted to use the sudo command, or tried to su command change something, i either got the following issues:

sudo ...
sudo: cant lookup  via gethostbyname()

After reading the above posts, I investigated /etc/hostname and /etc/hosts and made two observations:
1. The sudo error message above returned a "" as my computers name.
2. Both hostname and hosts called my computer, which i *thought* i had named **cmslaptop** as "-cmslaptop". 
3. All other parts of host and hostname were exactly the same as the above users files.

So i rebooted in recovery mode as root, made backups of hosts and hostname, and continuted to tinker with the files until results were hit on.

I found that removing the hypen ("-") from my laptop's name cleared up all the issues with sudo. I have no idea why this worked, but it was indeed the only change that allowed me to use root priveleges.

---

