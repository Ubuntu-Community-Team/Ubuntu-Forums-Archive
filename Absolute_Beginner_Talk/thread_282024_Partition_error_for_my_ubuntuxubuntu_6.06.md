---
title: "Partition error for my ubuntu/xubuntu 6.06"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-22
Hello, I have 4 partitions on my notebook, Partition 1 is 35GB of Windows Xp, Partition 2 is 14GB of ubuntu/xubuntu 6.06 LTS, Partition 3 is 10GB of xubuntu 6.10 edgy, and Partition 4 is 1GB linux swap.

My windows xp is working good, and my xubuntu 6.10 is working incredibly good. But my dapper ubuntu/xubuntu is not letting me log in and giving me a strange error message when I try to log in after the grub screen and boot up.

It is saying this in the log in the screen after I login and use password:

user's $ HOME/ .dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writtable by others.

then:

Your home directory is listed as: '/me/me' but it doesn't appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use the failsafe system.

Then when I try press ok (after selecting failsafe gnome during log in), it says:

/etc/gdm/PreSession/Default:Registering your session with wtmp and vtmp :running:usr/bin/sessions

-a -w /var/log/wtmp/ -u /var/run/utmp/ -x"/var/run/utmp -x "/var/lib/gdm/:O.Xservers "-h" " -| " :O"me"

then it says this after proceeding:

view details (~/.xsession-errors file)

(gnome-sessions:4761): libgnomevfs-Warning**:Unable to create ~/.gnome2 directory: no such file or directory

could not create per-user gnome configuration directory `/home/me/.gnome2/`:no such file or directory

***I don't really know what any of this means since I'm so new to linux/ubuntu/xubuntu.

Also, I don't want to mess up either of my working partitions of edgy 6.10 and Xp, so if I have to erase it and fix the partition's free space with gparted (if that is possible), then please explain on how to do that also.

Thanks,
-c.

---

### Post by podunk on 2006-10-22
Now would be a very good time to back up any important personal data.

I had that the first 2 times I tried to set up Samba, I tried to change permissions for my home folder in my /etc/samba/smb.conf file and it didn't work. :-) The first time I reinstalled from scratch, the second time I had a back up to restore which fixed everything.

I'm sure there is a way to change the permissions back with out going through all that - but everything I did made things worse it seemed so I just overwrote everything.

If you decide to reinstall the very easiest way to format your drives is to <blush!> boot into XP, click My Computer>System Settings>Administration>Disk Management and use the tool there to delete your Ubuntu partition.

Then when you install Ubuntu it will ask you where to install tell it to use the largest free space.

---

### Post by crimesaucer on 2006-10-22
Well, I just did three fresh installs in a row (Xp,6.06,6.10) so I have everything backed up already, I just might want to erase the partition 2, just because I like the way edgy is better and it's working really good.

I wonder if installing edgy did that to my dapper, because it was working good before the 3rd install. I had some problems with the edgy install because I did it with an upgrade of the kernel from dapper and had to configure it without the gui because of an xinit error. 

But now the edgy is so much nicer and faster than my dapper was, and I wouldn't want to mess it up, so can I just erase the 6.06 dapper in gparted and then add the free space to my 6.10 edgy?

---

