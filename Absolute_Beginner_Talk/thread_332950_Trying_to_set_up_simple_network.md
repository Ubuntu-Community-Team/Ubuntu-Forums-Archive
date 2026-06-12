---
title: "Trying to set up simple network"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tj.milligan on 2007-01-06
Hello all,

I need help setting up a network.

First things first, I'd like to use nfs between my notebook and my desktop. The problem is, I'm used to *Workgroups* in  that "other" OS. How do I simply make it so both computers are on the same "workgroup", or equivalent, on Edgy?

---

### Post by tj.milligan on 2007-01-06
Any ideas...?

---

### Post by riven0 on 2007-01-06
I'm assuming internet is working fine? So then you'll probably want Samba. 

[How-To set up Samba]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/")

---

### Post by tj.milligan on 2007-01-06
Thanks, riven0, but I'm missing a step before I try my hand at samba--or so I think. I'm not even sure how to change my computer name, or its workgroup. Please help this super networking newb!!

---

### Post by PilotJLR on 2007-01-06
Names and workgroups are WIndows (SMB / SAmba) concepts... ignore that entirely if you want to use NFS.

To install the nfs server:
```

sudo apt-get install nfs-kernel-server

```

Then add entries in /etc/exports for the directories you want to share, as shown here:
[http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup](http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup)

Then mount the share on the client side, as shown here:
[http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mounting_remote_dirs](http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mounting_remote_dirs)

---

### Post by tj.milligan on 2007-01-06
Great! Thanks for your help, PilotJLR. I will try this immediately and post my results.

BTW, I will need to set up samba eventually for my last "computer" (WinXp under vmware). But I will look at
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)
and other guides before I ask any questions. I've managed to get samba working in another *nix, so I'm optimistic.

---

### Post by tj.milligan on 2007-01-06
> **PilotJLR said:**
> Names and workgroups are WIndows (SMB / SAmba) concepts... ignore that entirely if you want to use NFS.

To install the nfs server:
```

sudo apt-get install nfs-kernel-server

```

Then add entries in /etc/exports for the directories you want to share, as shown here:
[http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup](http://nfs.sourceforge.net/nfs-howto/ar01s03.html#config_server_setup)

Then mount the share on the client side, as shown here:
[http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mounting_remote_dirs](http://nfs.sourceforge.net/nfs-howto/ar01s04.html#mounting_remote_dirs)

So I have nfs-kernel-server installed on master computer and not on notebook. On master, my /etc/exports reads as follows:

/media/audio/ 192.168.1.3(ro)

(192.168.1.3 is IP address of slave computer as given by ifconfig. 192.168.1.2 is master IP address)

On slave computer, I made a /mnt/audioshare/ folder, and
sudo mount 192.168.1.2:/media/audio/Audio /mnt/audioshare/
gives the following error:
mount: 192.168.1.2:/media/audio failed, reason given by server: Permission denied

What am I doing wrong?? Is that not my IP?? HELLLLLPPPPPP! BTW, slave host name=nixbook; master host name=ubuntu, but I'm not sure how to use these with nfs.. For instance, master's /etc/exports with the line /media/audio/ nixbook(ro) and slave command sudo mount ubuntu:/media/audio /mnt/audioshare/ don't work in place of IP names. I'd rather use host names since IPs are "dynamically" assigned according to which computer is turned on first..

[B]EDIT: got it working after RESTARTING master computer. Thought restarts were for "other" OSes... oh well. Still have question about nfs, or more specifically IPs:

How do I use some sort of alias or computer name (ubuntu's computer's "host name") in place of IP address? My IP address changes according to which computers are started first.[/B]

---

### Post by tj.milligan on 2007-01-06
ip problem solved in router config! assigned static ips to various computers, then add
<IP> <alias>
to /etc/hosts.

---

### Post by PilotJLR on 2007-01-07
Glad it's working for you.

And you're right... restarts ARE for other OS's. The only times you have to reboot in linux is to change kernel, HAL, or dbus.

The changed you made to /etc/exports did not take effect because nfs was already running! Instead of rebooting, just ask it to reload the config file.
```

sudo /etc/init.d/nfs-kernel-server reload

```

---

### Post by msimon1960 on 2007-01-15
I haven't met anyone in these forums that ever got SAMBA to work -- I think it's a myth that it works at all.

simple networking and linux don't go together -- 6 weeks and counting and I've never been able to set up a stable share to a common directory.

I live in hope someday....

---

### Post by msimon1960 on 2007-01-15
Ive had plenty of restarts in Ubuntu -- probably more than a complete linux expert but it's common to have to start and stop services.  Great in theory except...\

Who knows when you are running a service?  It's not like the system tells you the difference between a configuration change that requires a service restart.

For example -- wasted a lot of experimental time before I found out you have to stop the SAMBA service, make your changes, and then restart the SAMBA service.  There is no system prompting that this is necessary.

My advice -- reboot and you're at least 50% sure your configuration changes have taken place (although there are exceptions to this as well).

Matt.

---

### Post by PilotJLR on 2007-01-15
> **msimon1960 said:**
> I haven't met anyone in these forums that ever got SAMBA to work -- I think it's a myth that it works at all.

simple networking and linux don't go together -- 6 weeks and counting and I've never been able to set up a stable share to a common directory.

I live in hope someday....

I know you're not serious, but really... Samba is extremely common and works great.

---

