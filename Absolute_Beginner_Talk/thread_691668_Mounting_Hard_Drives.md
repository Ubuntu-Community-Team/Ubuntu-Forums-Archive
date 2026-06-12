---
title: "Mounting Hard Drives"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by nynoah on 2008-02-08
I have an issue mounting my other slave hard drives.  When I turn my computer on and off I have to remount them every time.  It does not bother me too much......But in order to delete or add files to them, I have to sign in as Gksudo Nautilus.  Is there a better way of mounting them so I do not have to go under root to do that?

---

### Post by Rocket2DMn on 2008-02-08
Can you please post the output of these 2 commands:
```
sudo fdisk -l
cat /etc/fstab
```

If you know which devices are your slaves from the first command, please say so.

---

### Post by nynoah on 2008-02-08
> noah@noah-desktop:~$ sudo fdisk -l
[sudo] password for noah:

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19bd19bc

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161   83  Linux

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24863058

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35729   286993161   83  Linux
/dev/sda2           35730       36481     6040440    5  Extended
/dev/sda5           35730       36481     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69df69df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe084e084

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux
noah@noah-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d55486a5-76e3-4e44-8a40-ad8e93841c50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e85f5095-f4cb-477c-9057-36678debd2a3 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
noah@noah-desktop:~$ 


Ok that is what I get

---

### Post by Rocket2DMn on 2008-02-08
Which devices do you need to mount?  You will need to add entries in fstab for them
```
gksudo gedit /etc/fstab
```
Here is a great guide to mounting in linux - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
If you need further help, please post which devices you need to mount, because there are a lot of them.

---

### Post by taurus on 2008-02-08
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/sdb1   /media/sdb1   ext3   defaults   0   1
/dev/sdc1   /media/sdc1   ext3   defaults   0   1

```
Save it and close down gedit window.  Then, create those two new mount points and mount them.

```
sudo mkdir /media/sdb1 /media/sdc1
sudo mount -a
df -h
```
And if you want to write to them without using sudo/gksudo all the time, then you need to change the ownerships of those two mount points from root to your login name, noah.

```
sudo chown -R noah:noah /media/sdb1
sudo chown -R noah:noah /media/sdc1
ls -la /media
```

---

### Post by nynoah on 2008-02-08
Ok I am going to do that.  But I also noticed that you missed my hdb drive in there.

It was the first one.  I am using your commands and change out the correct items to mount that one too.  Wish me luck.....but this is how I learn.

Let you know how it goes.

Thanks
Noah

---

### Post by Jewfro_Macabbi on 2008-02-08
to mount drives at start up, add a line to your /etc/fstab file

sudo gedit /etc/fstab

add the line for your drives at the bottom

here's an example of mounting a windows drive from my fstab file:

/dev/sda1	/media/Windows	ntfs	noatime,defaults,users,ro,umask=0 0 0

the first part is the drive your mounting - the second part is the mount point - then filesystem type and access rules.

save the changes to fstab and if all goes well your drive will be mounted automatically on reboot.

---

### Post by nynoah on 2008-02-09
Ok I could have typed something wrong.  But here is my situation.  I am on the live cd right now.  Because my Ubuntu is messed up now.  How can I edit my fstab from the live cd so that I can fix what I did.  Right now my ubuntu will not boot at all.  Not in recovery or general kernal. 

Please help

---

### Post by taurus on 2008-02-09
From the LiveCD, do

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/etc/fstab
```

---

### Post by nynoah on 2008-02-09
well I did just what you said.  But my fstab is blank?  I mean...........blank blank

hmmmm

Is there nothing in my fstab or do we need to do it another way?

or do I need to mount that hard drive first?

---

### Post by taurus on 2008-02-09
What's the output of this command?

```
ls -la /mnt/ubuntu/etc/fstab*
```
Make sure you include the [COLOR="Blue"]*[/COLOR] right after the [COLOR="Blue"]b[/COLOR].

---

### Post by nynoah on 2008-02-09
> ubuntu@ubuntu:~$ ls -la /mnt/ubuntu/etc/fstab*
ls: /mnt/ubuntu/etc/fstab*: No such file or directory
ubuntu@ubuntu:~$ 


I am pretty sure that I saved it correctly before.

---

### Post by taurus on 2008-02-09
Can you post these?

```
df -h
ls -la /mnt/ubuntu/etc
```

---

### Post by nynoah on 2008-02-09
> ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1014M   16M  999M   2% /lib/modules/2.6.22-14-generic/volatile
tmpfs                1014M   16M  999M   2% /lib/modules/2.6.22-14-generic/volatile
varrun               1014M   88K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  112K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
tmpfs                1014M   24K 1014M   1% /tmp
/dev/sda1             231G  213G  5.5G  98% /mnt/ubuntu
ubuntu@ubuntu:~$ ls -la /mnt/ubuntu/etc


done

---

### Post by nynoah on 2008-02-09
OK  I think I see the problem it mounted my other hard drive that did not have Ubuntu on it.  To make this easier.  I am going to power off and disconect all drives except my primary that has my ubuntu install.

But I will wait for your ok before I do that.

---

### Post by taurus on 2008-02-09
But isn't Ubuntu on /dev/sda1, according to your /etc/fstab in previous post?

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
[B][COLOR="Blue"]# /dev/sda1
UUID=d55486a5-76e3-4e44-8a40-ad8e93841c50 / ext3 defaults,errors=remount-ro 0 1[/COLOR][/B]
# /dev/sda5
UUID=e85f5095-f4cb-477c-9057-36678debd2a3 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0


---

### Post by nynoah on 2008-02-09
yes it was.......but seems to have mounted the other one instead.

want me to open up the computer and make sure that it is plugged into all the right places.  (not hard to do, the side is off anyways)

---

### Post by taurus on 2008-02-09
It's up to you.  I need to ride my bike home so will be off-line in a few minutes.

---

### Post by nynoah on 2008-02-09
Hmmm well ok.....explain real quick to me what you were planning on doing.  I can take your commands and try to do what you were thinking once I weed it down to one hard drive in there.

---

### Post by Jewfro_Macabbi on 2008-02-09
A blank fstab file would indicate a problem... Are you sure you are opening the right location? gedit opens a blank file if it doesn't exist - ala  typo?

If you fstab really is blank - is there a backup? /etc/fstab~?

It should look something like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b999e5e2-da72-440a-b247-9da6fa1e2c28 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d42d1154-f3a6-47fd-a7e2-cd715c8ed507 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
tmpfs     /dev/shm     tmpfs     defaults,ro     0     0
/dev/sda1	/media/Windows	ntfs	noatime,defaults,users,ro,umask=0 0 0
/Files/Apps/ROSETTA-STONE.iso /media/rosetta/	iso9660 ro,loop,auto 0 0

---

### Post by nodegamra on 2008-02-09
Hey Guys how are you?
Just reading your post and dejavu!
The same thing happened to me after editing the fstab.
I finished editing with nano saved the changes went to reboot and poof fstab was blank!

I wonder why that is?:confused:

Thanks by the way Taurus for helping me yesterday!

I recommend backing fstab before any changes are done!

What do you think Taurus?

sorry for the off topic.

---

### Post by nynoah on 2008-02-09
OK all other hard drives are disconnected.  That way there is no confusion with mounting the wrong one. 

I will run the commands from before and post them.

---

### Post by cmnorton on 2008-02-09
Here's one place to start and mounting drives is covered all of the forums:

[http://ubuntuforums.org/showthread.php?t=674328](http://ubuntuforums.org/showthread.php?t=674328)

---

### Post by nynoah on 2008-02-09
well...........ohhhh how life twists

Did just the same commands as before with only on drive in place.....and.....my fstab is blank


Ok is there a way to recreate it

---

### Post by nynoah on 2008-02-09
I have a normal install of ubuntu.  I do not have a separate home directory.  (I really should have done that, but what is done is done)

So when I open Gparted I have

/dev/sda1          as ext3
/dev/dsa2    extended 
 
with /dev/sda5   for linux swap         inside that

---

### Post by nynoah on 2008-02-09
I have an idea......should I cut and paste the previous set up to my fstab into the blank one and save that?

I will pick out the part for my primary hard drive alone.

Or should I just do that whole thing?

---

### Post by nynoah on 2008-02-09
ok well did just that.  I cut and pasted the file from the previous fstab.  I then went in under the gui interface to look at it.  I think I see a HUGE problem.......God why me..............when I go to open up my etc file...........there is NOTHING in it at all........I mean NOTHING......what is in there now is my saved fstab.  But nothing.  else.  Should I go and cut the contents of the fstab from the install disk into there.  Or will I be missing too much.  This is looking like the only thing I can do is wipe my system and start over.......

---

### Post by nodegamra on 2008-02-09
Have you made any hardware or BIOS changes since?

You mean under the /etc directory?

---

### Post by nynoah on 2008-02-09
if I am understanding you correctly.....no

The only thing I did was edit my fstab as stated in the begining of the thread.  

encase you mean disconnect hard drives, yes I have done that.  To make this simple  I disconnected all my storage drives.  I was going to reconnect them when I booted up.

---

### Post by nodegamra on 2008-02-09
I meant if everything is connected and configured just the way it was before you edited your fstab.
Did you say you lost everything in your /etc directory?

---

### Post by nynoah on 2008-02-09
looks to be so (lost all in etc directory)  I go into my home folder in the mounted hard drive and back up till I see the icon for etc.  Click on it....and it is empty.  I hit show hidden files and the only file in there is the one I just saved for my redone fstab.

---

### Post by nodegamra on 2008-02-09
Are you shure you are in /etc?

Try this to see if you got anything in there:

```
ls /etc
```

---

### Post by nynoah on 2008-02-09
got a whole bunch under that, but is that the results from my HD or from the live disk?

> ubuntu@ubuntu:~$ ls /etc
acpi                    group                pam.conf
adduser.conf            group-               pam.d
adjtime                 grub.d               pango
aliases                 gshadow              papersize
alternatives            gshadow-             passwd
anacrontab              gtk-2.0              passwd-
apm                     hal                  pcmcia
apparmor                hdparm.conf          perl
apparmor.d              hesiod.conf          pnm2ppa.conf
apport                  host.conf            popularity-contest.conf
apt                     hostname             power
at.deny                 hosts                ppp
avahi                   hosts.allow          printcap
bash.bashrc             hosts.deny           profile
bash_completion         hotplug              protocols
bash_completion.d       hp                   purple
belocs                  init.d               python
bindresvport.blacklist  initramfs-tools      python2.5
bluetooth               inputrc              rc0.d
bogofilter.cf           iproute2             rc1.d
bonobo-activation       issue                rc2.d
brlapi.key              issue.net            rc3.d
brltty                  java                 rc4.d
brltty.conf             kernel-img.conf      rc5.d
calendar                laptop-mode          rc6.d
casper.conf             ldap                 rc.local
chatscripts             ld.so.cache          rcS.d
compizconfig            ld.so.conf           readahead
console-setup           ld.so.conf.d         resolvconf
console-tools           lftp.conf            resolv.conf
cron.d                  libao.conf           rmt
cron.daily              libgda-3.0           rpc
cron.hourly             libpaper.d           samba
cron.monthly            locale.alias         sane.d
crontab                 locale.gen           scim
cron.weekly             localtime            screenrc
cups                    logcheck             scrollkeeper.conf
dbus-1                  login.defs           securetty
debconf.conf            logrotate.conf       security
debian_version          logrotate.d          services
default                 lsb-base             sgml
defoma                  lsb-base-logging.sh  shadow
deluser.conf            lsb-release          shadow-
devfs                   ltrace.conf          shells
dhcp3                   magic                skel
dictionaries-common     magic.mime           sound
discover.conf           mailcap              ssh
discover.conf-2.6       mailcap.order        ssl
discover.d              manpath.config       sudoers
dpkg                    mediaprm             sysctl.conf
emacs                   menu-methods         syslog.conf
environment             mime.types           terminfo
esound                  mke2fs.conf          timezone
event.d                 modprobe.d           ucf.conf
fdmount.conf            modules              udev
firefox                 modutils             uniconf.conf
fonts                   mono                 updatedb.conf
foomatic                motd                 update-notifier
fstab                   motd.tail            usplash.conf
fuse.conf               mtab                 vim
gai.conf                nanorc               w3m
gamin                   Net                  wgetrc
gconf                   netscsid.conf        wodim.conf
gdm                     network              wpa_supplicant
gimp                    NetworkManager       wvdial.conf
gnome                   networks             X11
gnome-app-install       nologin              xdg
gnome-system-tools      nsswitch.conf        xml
gnome-vfs-2.0           openalrc             zsh_command_not_found
gnome-vfs-mime-magic    openoffice
groff                   opt
ubuntu@ubuntu:~$ 



---

### Post by nodegamra on 2008-02-09
I did not realize that you are running a live session.
lets try both codes:

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nynoah on 2008-02-09
yeah I lost my Ubuntu when I edited my fstab in the begining of the post.  

This is what I get with you commands.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24863058

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35729   286993161   83  Linux
/dev/sda2           35730       36481     6040440    5  Extended
/dev/sda5           35730       36481     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ 


---

### Post by nodegamra on 2008-02-09
OK
Make a directory on the home directory:
```
mkdir ~/new1
```

Then mount the second partition of your hard drive to the directory you created:
```
sudo mount -t ext3 /dev/sda2 ~/new1
```

Then list the contents of the mounted partition:
```
ls ~/new1
```

---

### Post by nynoah on 2008-02-09
no go there so far

> ubuntu@ubuntu:~$ mkdir ~/new1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 ~/new1
mount: special device /dev/sda2 does not exist
ubuntu@ubuntu:~$ ls ~/new1
ubuntu@ubuntu:~$ 


---

### Post by nodegamra on 2008-02-09
do this instead:
```
sudo mount /dev/sda2 ~/new1
```
then
```
ls ~/new
```

---

### Post by nynoah on 2008-02-09
Just wanted to say thank you for helping me first......I know this is a hard problem to solve.  I did a reboot to see if it would come back up.  No such luck.

So I started back from where you started to ask me to do some commands.  Here is what I got.


> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24863058

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35729   286993161   83  Linux
/dev/sda2           35730       36481     6040440    5  Extended
/dev/sda5           35730       36481     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ mkdir ~/new1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 ~/new1
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ ls ~/new1
ubuntu@ubuntu:~$ sudo mount /dev/sda2 ~/new1
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ ls ~/new
ls: /home/ubuntu/new: No such file or directory
ubuntu@ubuntu:~$ 



---

### Post by nodegamra on 2008-02-09
Lets try this again
Make a directory on the home directory:
```
mkdir ~/new1
```

Then mount the second partition of your hard drive to the directory you created:
```
sudo mount -t xfs /dev/sda2 ~/new1
```

Then list the contents of the mounted partition:
```
ls ~/new1
```

sorry about the bad fs type:)

---

### Post by ve9gj on 2008-02-09
/dev/sda2 is just the Extended  partition.  All it contains is a swap partition sda5


Not exactly sure where you are at now.  Try booting with the live CD and mounting your sda1 partion which i understand contains your Ubuntu / filesystem.

sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1

Now
ls -ltr /mnt/sda1 
shoud list the / of your Ubuntu system with the newest stuff at the bottom

now
sudo chroot /mnt/sda1

/ is now your Ubuntu /
try
find / |grep fstab

does it find anything?



Glenn

---

### Post by ve9gj on 2008-02-09
Another thought
 in a new terminal window do

sudo vol_id /dev/sda1

Look for the FS_ID line does it match the original fstab you listed?

# /dev/sda1
UUID=d55486a5-76e3-4e44-8a40-ad8e93841c50 / ext3 defaults,errors=remount-ro 0 1

You are mounting by UUID so if you had been moving drives around maybe sda1 is not really where you /etc/ is.



Glenn

---

### Post by nynoah on 2008-02-09
Thanks for taking up my cause.  I had to run to get some food.  I have been at this for a while now.......

I tried your commands.  I tried the first set and it stopped working halfway through.  I have cut and pasted all what I got below.  I also ran the other command you gave too.

Let me know what you think?

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ s -ltr /mnt/sda1 
bash: s: command not found
ubuntu@ubuntu:~$ sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=d55486a5-76e3-4e44-8a40-ad8e93841c50
ID_FS_UUID_ENC=d55486a5-76e3-4e44-8a40-ad8e93841c50
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
ubuntu@ubuntu:~$ 




---

### Post by nynoah on 2008-02-09
also I just ran some of the commands from a previous user and changed what he wrote for sda2 to sda1.  Seemed to work well.  Here is what I got.  Not sure what to do from here.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24863058

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35729   286993161   83  Linux
/dev/sda2           35730       36481     6040440    5  Extended
/dev/sda5           35730       36481     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ mkdir ~/new1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 ~/new1
ubuntu@ubuntu:~$ ls ~/new1
bin    dev   initrd          lib    lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img      lib32  media       proc  srv   usr  vmlinuz.old
cdrom  home  initrd.img.old  lib64  mnt         root  sys   var
ubuntu@ubuntu:~$ 



---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> Thanks for taking up my cause.  I had to run to get some food.  I have been at this for a while now.......

I tried your commands.  I tried the first set and it stopped working halfway through.  I have cut and pasted all what I got below.  I also ran the other command you gave too.

Let me know what you think?

ubuntu@ubuntu:~$ sudo mkdir /mnt/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/sda1
ubuntu@ubuntu:~$ s -ltr /mnt/sda1
bash: s: command not found
ubuntu@ubuntu:~$ sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=d55486a5-76e3-4e44-8a40-ad8e93841c50
ID_FS_UUID_ENC=d55486a5-76e3-4e44-8a40-ad8e93841c50
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


I see I had a typo s -ltr s/b ls -ltr !!

Anyhow your output
 ID_FS_UUID=d55486a5-76e3-4e44-8a40-ad8e93841c50
confirms that you are looking at the right drive because your original fstab said # /dev/sda1
UUID=d55486a5-76e3-4e44-8a40-ad8e93841c50 / ext3 defaults,errors=remount-ro 0 1

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> also I just ran some of the commands from a previous user and changed what he wrote for sda2 to sda1.  Seemed to work well.  Here is what I got.  Not sure what to do from here.

ubuntu@ubuntu:~$ mkdir ~/new1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 ~/new1
ubuntu@ubuntu:~$ ls ~/new1
bin dev initrd lib lost+found opt sbin tmp vmlinuz
boot etc initrd.img lib32 media proc srv usr vmlinuz.old
cdrom home initrd.img.old lib64 mnt root sys var


What does 
ls - l ~/new1/etc
show ?

---

### Post by nynoah on 2008-02-09
any ideas now.  Right now I on ubuntu not as a live disk.....but I installed it on a crappy old 15gig hard drive I had sitting around.  Should I go back to the live disk?  If so, whats the next idea?

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> any ideas now.  Right now I on ubuntu not as a live disk.....but I installed it on a crappy old 15gig hard drive I had sitting around.  Should I go back to the live disk?  If so, whats the next idea?

Just to be clear you installed a 15g drive in the same pc and did a brand new gutsy install on the 15 gig drive?  Did you leave the original ubuntu / drive in the PC (sda) ?

what does sudo fdisk -l show now?

---

### Post by nynoah on 2008-02-09
well too much to deal with,  I disconnected the older drive and I am back on my live disk with only my SATA drive hooked up that has my primary ubuntu install.  Ok let me run the command and we can start from there

Thanks


Noah

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> well too much to deal with,  I disconnected the older drive and I am back on my live disk with only my SATA drive hooked up that has my primary ubuntu install.  Ok let me run the command and we can start from there

Thanks


Noah

Well lets get back to where you were and get sda1 mounted again.  using a previous test:

mkdir ~/new1
sudo mount -t ext3 /dev/sda1 ~/new1
ls ~/new1

You got:

bin dev initrd lib lost+found opt sbin tmp vmlinuz
boot etc initrd.img lib32 media proc srv usr vmlinuz.old
cdrom home initrd.img.old lib64 mnt root sys var

Can you repeat this and get the same result? etc is listed, what is in it?
post

ls -ltr ~/new1/etc

---

### Post by nynoah on 2008-02-09
here

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ mkdir ~/new1
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 ~/new1
ubuntu@ubuntu:~$ ls ~/new1
bin    dev   initrd          lib    lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img      lib32  media       proc  srv   usr  vmlinuz.old
cdrom  home  initrd.img.old  lib64  mnt         root  sys   var
ubuntu@ubuntu:~$ ls -ltr ~/new1/etc
total 0
?--------- ? ? ? ?                ? /home/ubuntu/new1/etc/fstab~
ubuntu@ubuntu:~$ 


---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> here

ubuntu@ubuntu:~$ ls -ltr ~/new1/etc
total 0
?--------- ? ? ? ? ? /home/ubuntu/new1/etc/fstab~




This doesn't look good.  All that seems to be in it is a fstab~ (temp file)
Also not sure why it does not display time stamps etc?

try posting 
ls -ltr ~/new1

try posting
find ~/new1 | grep mtab

mtab is another standard file in an etc folder.  This should show if the contents of etc got moved somehow.

I wonder if a chkdisk woud find anything.

cd /
umount /dev/sda1
chkdsk -f /dev/sda1


Glenn




I assume there is no backups anywhere for your etc folder.

---

### Post by nynoah on 2008-02-09
ok

> ubuntu@ubuntu:~$ ls -ltr ~/new1
total 5836
-rwxr-xr-x   1 root root    6607 2007-09-30 23:51 bin
drwxr-xr-x   2 root root    4096 2007-10-04 11:25 sys
drwxr-xr-x   2 root root    4096 2007-10-08 10:39 proc
drwxr-xr-x   2 root root    4096 2007-10-08 10:39 mnt
drwxr-xr-x   2 root root    4096 2007-10-15 23:16 srv
drwxr-xr-x   2 root root    4096 2007-10-15 23:16 opt
drwxr-xr-x   2 root root    4096 2007-10-15 23:16 initrd
drwxr-xr-x   4 root root    4096 2007-10-15 23:34 dev
drwx------   2 root root   16384 2008-01-11 17:37 lost+found
lrwxrwxrwx   1 root root      11 2008-01-11 17:38 cdrom -> media/cdrom
lrwxrwxrwx   1 root root       4 2008-01-11 17:38 lib64 -> /lib
lrwxrwxrwx   1 root root      30 2008-01-11 17:48 vmlinuz.old -> boot/vmlinuz-2.6.22-14-generic
lrwxrwxrwx   1 root root      33 2008-01-11 17:48 initrd.img.old -> boot/initrd.img-2.6.22-14-generic
lrwxrwxrwx   1 root root      25 2008-01-11 22:04 vmlinuz -> boot/vmlinuz-2.6.22-14-rt
lrwxrwxrwx   1 root root      28 2008-01-11 22:04 initrd.img -> boot/initrd.img-2.6.22-14-rt
drwxr-xr-x   4 root root    4096 2008-01-11 22:26 lib32
-rw-r--r--   1 1000 1000 5853184 2008-01-25 05:51 root
drwxr-xr-x   6 root root    4096 2008-01-27 01:20 home
drwxr-xr-x  18 root root    4096 2008-01-27 01:44 var
drwxr-xr-x   2 root root    4096 2008-02-06 00:40 sbin
drwxr-xr-x  18 root root   12288 2008-02-06 00:40 lib
drwxr-xr-x   3 root root    4096 2008-02-06 00:41 boot
drwxr-xr-x  13 root root    4096 2008-02-06 03:41 usr
drwxr-xr-x  10 root root    4096 2008-02-09 03:06 media
drwxrwxrwt   4 root root    4096 2008-02-09 03:23 tmp
drwxr-xr-x 147 root root   12288 2008-02-09 20:56 etc
ubuntu@ubuntu:~$ 



> ubuntu@ubuntu:~$ find ~/new1 | grep mtab
find: /home/ubuntu/new1/media/disk-2: Permission denied
find: /home/ubuntu/new1/media/disk: Permission denied
find: /home/ubuntu/new1/media/disk-1: Permission denied
/home/ubuntu/new1/media/.hal-mtab
/home/ubuntu/new1/media/.hal-mtab-lock
find: /home/ubuntu/new1/var/log/samba/cores: Permission denied
find: /home/ubuntu/new1/var/spool/cups: Permission denied
find: /home/ubuntu/new1/var/spool/cron/crontabs: Permission denied
find: /home/ubuntu/new1/var/spool/cron/atjobs: Permission denied
find: /home/ubuntu/new1/var/spool/cron/atspool: Permission denied
find: /home/ubuntu/new1/var/lib/python-support/python2.5: No such file or directory
find: /home/ubuntu/new1/var/lib/gdm: Permission denied
find: /home/ubuntu/new1/var/lib/gstreamer/0.10: No such file or directory
find: /home/ubuntu/new1/var/lib/slocate: Permission denied
/home/ubuntu/new1/var/lib/nfs/rmtab
find: /home/ubuntu/new1/var/lib/locales/supported.d: No such file or directory
find: /home/ubuntu/new1/var/lib/mozilla-firefox/extensions.d: No such file or directory
find: /home/ubuntu/new1/var/cache/system-tools-backends/backup: Permission denied
find: /home/ubuntu/new1/var/tmp/kdecache-noah: Permission denied
find: /home/ubuntu/new1/var/tmp/kdecache-root: Permission denied
find: /home/ubuntu/new1/var/tmp/BkITmgeeCkoFLfYNFfjEH: Permission denied
find: /home/ubuntu/new1/bin: Not a directory
find: /home/ubuntu/new1/lib/modules/2.6.22-14-rt/kernel/drivers: Not a directory
find: /home/ubuntu/new1/home/noah/.gnome2: Permission denied
find: /home/ubuntu/new1/home/noah/.metacity: Permission denied
find: /home/ubuntu/new1/home/noah/.local/share/applications: Permission denied
find: /home/ubuntu/new1/home/noah/.local/share/Trash: Permission denied
find: /home/ubuntu/new1/home/noah/.Trash: Permission denied
find: /home/ubuntu/new1/home/noah/.mplayer: Permission denied
find: /home/ubuntu/new1/home/noah/.nautilus/metafiles: Permission denied
find: /home/ubuntu/new1/home/noah/.nautilus/patterns: Permission denied
find: /home/ubuntu/new1/home/noah/.evolution/calendar/local: Permission denied
find: /home/ubuntu/new1/home/noah/.evolution/cache: Permission denied
find: /home/ubuntu/new1/home/noah/.evolution/memos/local: Permission denied
find: /home/ubuntu/new1/home/noah/.evolution/tasks/local: Permission denied
find: /home/ubuntu/new1/home/noah/.update-notifier: Permission denied
find: /home/ubuntu/new1/home/noah/.mozilla: Permission denied
find: /home/ubuntu/new1/home/noah/.thumbnails: Permission denied
find: /home/ubuntu/new1/home/noah/.scim: Permission denied
find: /home/ubuntu/new1/home/noah/.w3m: Permission denied
find: /home/ubuntu/new1/home/noah/.macromedia: Permission denied
find: /home/ubuntu/new1/home/noah/.themes/Pearl: Permission denied
find: /home/ubuntu/new1/home/noah/.themes/Monochromatic-black/gtk-2.0: Permission denied
find: /home/ubuntu/new1/home/noah/.themes/Candy: Permission denied
find: /home/ubuntu/new1/home/noah/.themes/SlicknesS(black-mac): Permission denied
find: /home/ubuntu/new1/home/noah/.themes/.theme-950852130: Permission denied
find: /home/ubuntu/new1/home/noah/.themes/circlingthesun/gtk-2.0/Panel: Permission denied
find: /home/ubuntu/new1/home/noah/.themes/circlingthesun/gtk-2.0/Menubar: Permission denied
find: /home/ubuntu/new1/home/noah/.config/tracker: Permission denied
find: /home/ubuntu/new1/home/noah/.config/deluge: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/Diskusage: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/NowPlaying: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/Sysmonitor: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/ClearWeather: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/Clock: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/Netmonitor: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/Sensors: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/Windowlist: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/CPUMeter: Permission denied
find: /home/ubuntu/new1/home/noah/.config/Screenlets/WaterMark: Permission denied
find: /home/ubuntu/new1/home/noah/.config/gtk-2.0: Permission denied
find: /home/ubuntu/new1/home/noah/.config/compiz: Permission denied
find: /home/ubuntu/new1/home/noah/.gnome2_private: Permission denied
find: /home/ubuntu/new1/home/noah/.gxine: Permission denied
find: /home/ubuntu/new1/home/noah/.opera: Permission denied
find: /home/ubuntu/new1/home/noah/Desktop/mP1tka: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.FontForge: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.gnome2: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.metacity: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.local/share/applications: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.local/share/Trash: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.Trash: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.mplayer: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.nautilus/metafiles: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.nautilus/patterns: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.armyops250: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.evolution/calendar/local: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.evolution/cache: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.evolution/memos/local: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.evolution/tasks/local: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.update-notifier: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.thumbnails: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.w3m: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.easytag: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.cache/thoggen: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.kluppe: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.macromedia: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Pearl: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Candy: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/circlingthesun/gtk-2.0/Panel: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/circlingthesun/gtk-2.0/Menubar: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Aero/gkrellm2: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Aero/gtk: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Aero/xfwm4: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Aero/gtk-2.0: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Aero/metacity-1: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.themes/Aero/xmms: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.config/tracker: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.config/deluge: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.config/graveman: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.config/autostart: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.config/gtk-2.0: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.config/compiz: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.config/thoggen: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.kompozer/3zuo718e.default: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.gnome2_private: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.gxine: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.kino-history: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.opera: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.dc: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.gconf: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.purple: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.gcjwebplugin: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.exaile/saved: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.dbus: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.aqualung: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.gconfd: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/visual appearences/extracted/Aero/gtk-2.0: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.secondlife: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/icesconfig: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.openoffice.org2: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.dbus-keyrings: Permission denied
find: /home/ubuntu/new1/home/noah/from old hard drive/.kde: Permission denied
find: /home/ubuntu/new1/home/noah/.gconf: Permission denied
find: /home/ubuntu/new1/home/noah/.purple: Permission denied
find: /home/ubuntu/new1/home/noah/.exaile/saved: Permission denied
find: /home/ubuntu/new1/home/noah/.xchat2: Permission denied
find: /home/ubuntu/new1/home/noah/72006-degradado pidgin: Permission denied
find: /home/ubuntu/new1/home/noah/.kde4: Permission denied
find: /home/ubuntu/new1/home/noah/.gconfd: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/Reflective_Icons_1.1a: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/extracted/Aero/gkrellm2: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/extracted/Aero/gtk: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/extracted/Aero/xfwm4: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/extracted/Aero/gtk-2.0: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/extracted/Aero/metacity-1: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/extracted/Aero/xmms: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/AWN Dock Theme: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/Sounds: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/GDM Theme: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/Pidgin: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/XMMS Audacious BMP Skin: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/GTK Login Splash: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/GTK Cursor Theme: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/GRUB Splash: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/Firefox Addons: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/Exaile AWN Plugin: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/Fonts: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/Emerald Theme: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/mac look/Mac4Lin_v0.4/USplash Theme: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/pidgin looks/65364-My-AER-OS-XK-pidgin-gaim-v1.0: Permission denied
find: /home/ubuntu/new1/home/noah/visual appearences/pidgin looks/pidgin: Permission denied
find: /home/ubuntu/new1/home/noah/.openoffice.org2: Permission denied
find: /home/ubuntu/new1/home/noah/.kazehakase: Permission denied
find: /home/ubuntu/new1/home/noah/.dbus-keyrings: Permission denied
find: /home/ubuntu/new1/home/noah/Music/2006 End of Year Charts: Permission denied
find: /home/ubuntu/new1/home/noah/Music/Best of 2007/Charlie Louvin [2007]: Not a directory
find: /home/ubuntu/new1/home/noah/Music/02006 Mixtapes: Permission denied
find: /home/ubuntu/new1/home/noah/Music/Happy Mondays - Greatest Hits (320kbps) rar: Permission denied
find: /home/ubuntu/new1/home/noah/.kde: Permission denied
find: /home/ubuntu/new1/root: Not a directory
find: /home/ubuntu/new1/lost+found: Permission denied
find: /home/ubuntu/new1/usr/lib/python2.5/xml: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/test: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/sqlite3/home/ubuntu/new1/usr/lib/python2.5/symtable.py
: Not a directory
/home/ubuntu/new1/usr/lib/python2.5/symtable.pyc
find: /home/ubuntu/new1/usr/lib/python2.5/hotshot: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/logging: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/encodings: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/plat-mac: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/lib-tk: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/lib-dynload: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/site-packages: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/plat-linux2: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/idlelib: Not a directory
find: /home/ubuntu/new1/usr/lib/python2.5/wsgiref: Not a directory
find: /home/ubuntu/new1/usr/local/games: Not a directory
find: /home/ubuntu/new1/usr/local/bin: Not a directory
find: /home/ubuntu/new1/usr/local/lib: Not a directory
find: /home/ubuntu/new1/usr/local/etc: Not a directory
find: /home/ubuntu/new1/usr/local/src: Not a directory
find: /home/ubuntu/new1/usr/local/include: Not a directory
find: /home/ubuntu/new1/usr/local/share: Not a directory
find: /home/ubuntu/new1/usr/local/sbin: Not a directory
/home/ubuntu/new1/usr/include/python2.5/symtable.h
/home/ubuntu/new1/usr/include/sepol/policydb/symtab.h
/home/ubuntu/new1/usr/include/unicode/symtable.h
/home/ubuntu/new1/usr/include/unicode/fmtable.h
find: /home/ubuntu/new1/usr/share/python-support/python-gtk2: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-libxml2: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-xdg: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-gnomecanvas: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-gtkhtml2: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/guidance-backends: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-dbus: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/gnome-applets-data: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-cups: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-gobject: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-gnome2-extras: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-gconf: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-apport: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-gnupginterface: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-vte: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/hplip: Not a directory
find: /home/ubuntu/new1/usr/share/python-support/python-at-spi: Not a directory
/home/ubuntu/new1/usr/share/app-install/desktop/gchemtable.desktop
find: /home/ubuntu/new1/usr/share/doc/kiwi: Not a directory
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/smileys: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/animations: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/status: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/buttons: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/plugin_pack: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/emotes: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/toolbar: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/protocols: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/pidgin-encryption: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/tray: Permission denied
find: /home/ubuntu/new1/usr/share/pixmaps/pidgin/guifications: Permission denied
find: /home/ubuntu/new1/usr/share/python-apt/templates: Not a directory
find: /home/ubuntu/new1/usr/share/pycentral/python-numeric/site-packages: Input/output error
find: /home/ubuntu/new1/usr/share/pycentral/python-gst0.10/site-packages: Not a directory
find: /home/ubuntu/new1/usr/share/pycentral/python-qt4/site-packages/PyQt4/uic: Input/output error
find: /home/ubuntu/new1/usr/share/pycentral/python-launchpad-bugs/site-packages: Input/output error
ubuntu@ubuntu:~$ 



---

### Post by nynoah on 2008-02-09
> ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ umount /dev/sda1
umount: /dev/sda1 is not in the fstab (and you are not root)
ubuntu@ubuntu:/$ chkdsk -f /dev/sda1
bash: chkdsk: command not found
ubuntu@ubuntu:/$ 


that is the last of it

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> tubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ umount /dev/sda1
umount: /dev/sda1 is not in the fstab (and you are not root)
ubuntu@ubuntu:/$ chkdsk -f /dev/sda1
bash: chkdsk: command not found
ubuntu@ubuntu:/$

Sorry I screwed up I should have said:

sudo umount /dev/sda1

and if now errors

sudo chkdsk -f  /dev/sda1

forgot the sudo

Glenn

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> 

ubuntu@ubuntu:~$ find ~/new1 | grep mtab



Did it again should have said sudo

sudo find ~/new1 | grep mtab
  But I don't hink that will find anything now so don't bother retrying.

It did throw some 'Input/output error" errors which shouldn't happen.

Let's wait for the chkdsk results

---

### Post by nynoah on 2008-02-09
> ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ umount /dev/sda1
umount: /dev/sda1 is not in the fstab (and you are not root)
ubuntu@ubuntu:/$ chkdsk -f /dev/sda1
bash: chkdsk: command not found
ubuntu@ubuntu:/$ sudo umount /dev/sda1
ubuntu@ubuntu:/$ sudo chkdsk -f /dev/sda1
sudo: chkdsk: command not found
ubuntu@ubuntu:/$ 

ok

---

### Post by nynoah on 2008-02-09
and the other command did not work either.  Should I have my hd mounted in order to run those?

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> 
ubuntu@ubuntu:/$ sudo umount /dev/sda1
ubuntu@ubuntu:/$ sudo chkdsk -f /dev/sda1
sudo: chkdsk: command not found
ubuntu@ubuntu:/$


Ok now I feel like a complete idiot!
please run

sudo fsck -f /dev/sda1


chkdsk is the windows fsck!

Sorry

Glenn

---

### Post by nynoah on 2008-02-09
Ok that is running now

---

### Post by nynoah on 2008-02-09
got a whole bunch of errors so far so this is taking a while.

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> got a whole bunch of errors so far so this is taking a while.

Well this may explain the missing etc mystery.  If fsck is finding errors sda1 is suffering from some form of corruption.  Hopefully fsck can fix it up but this is not always the case.  I guess we will have to wait for it to finish and hope for the best.  After that we can find out if it is the actual hard drive that is going south or ???

when it is done try

sudo smartctl -d on /dev/sda
sudo smartctl -a /dev/sda

smartctl should be able to dump the hard drives internal log.  Logg for a line that wil say something like Errors logged or maybe "No Errors Logged" If there are any amount of errors logged the drive is toast.

fsck can take awhile to run on a large drive

---

### Post by nynoah on 2008-02-09
yeah there were TONS of errors.....like on everything.

It ran through and fixed them and now it is running through again.  It is taking forever too.  I have to run to meet someone.  But I will run your commands when I get back.  If you would be so kind as to check out this thread in the morning.  That would be great.  You have been a great help so far.  Thank you.  

I hope my drive is not toast......I really don't have the money for a new one.  Anyone want to chip into the "buy Noah a 500gig Sata" fund...........guess not  LOL  

I am lucky there is a Micro center in town atleast.  Prices there are GREAT.  I get a 8 gig memorie stick for 30 dollars.  A 500 gig SATA drive is only 100 too.

---

### Post by ve9gj on 2008-02-09
> **nynoah said:**
> yeah there were TONS of errors.....like on everything.

It ran through and fixed them and now it is running through again.  It is taking forever too.  I have to run to meet someone.  But I will run your commands when I get back.  If you would be so kind as to check out this thread in the morning.  That would be great.  You have been a great help so far.  Thank you.  

I hope my drive is not toast......I really don't have the money for a new one.  Anyone want to chip into the "buy Noah a 500gig Sata" fund...........guess not  LOL  

I am lucky there is a Micro center in town atleast.  Prices there are GREAT.  I get a 8 gig memorie stick for 30 dollars.  A 500 gig SATA drive is only 100 too.

fsck can take a very long time to run when there are problems.  Make sure you let it finish and don't interupt it!  I think your original editing of fstab had nothing to do with this.  I work with a lot of linux servers and file corruption on its own is really unheard of.  Main cause seems to be bad drives followed by bad RAM.  After that maybe loose ide/sata cables or power problems.  ext3 file systems are very good at recovering from power problems.  You can check for bad ram by booting a live CD and typing memtest at the boot: prompt.  I think that works with a Ubuntu install CD.

I think I will retire for the evening here myself but I will check in the AM and see what you found out.

Fingers crossed
Glenn

---

### Post by ve9gj on 2008-02-10
> **nynoah said:**
> yeah there were TONS of errors.....like on everything.



Were they fsck errors or kernel IO errors such as seek or drive not ready errors?  The latter pretty much means failed drive.

Typical toasted drive kernel errors:

```

Feb 10 12:50:30 linux kernel: hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Feb 10 12:50:30 linux kernel: hdb: dma_intr: error=0x40 UncorrectableError }, LBAsect=16210739,  
Feb 10 12:50:30 linux kernel: end_request: I/O error, dev 03:41 (hdb)
 
```

---

### Post by nynoah on 2008-02-10
well the Fsck went through.........but things got MUCH worse.  Now I can not find any of the files on that hard drive.  Is there any program that can help recover those files.  I have 200 gigs worth of files in there that I want to recover.

Noah

---

### Post by ve9gj on 2008-02-10
> **nynoah said:**
> well the Fsck went through.........but things got MUCH worse.  Now I can not find any of the files on that hard drive.  Is there any program that can help recover those files.  I have 200 gigs worth of files in there that I want to recover.

Noah
 Very sorry to hear that.  Was fsck happy it was done?  What happens when you try annd mount it now and do a ls? Is there anything in lost+found dir?  It certainly sounds like the drive is bad, did you get kernel I/O errors or did smartctl show excessive errors logged?

Do you have another drive to try and clone the bad drive to?  There is a tool called dd_rescue which will do it's best to clone a bad drive, the tough part is I think you said your drive is a 400 or 500GB, that's alot of blocks to copy and the replacement drive would have to be the same size or larger.

---

### Post by nynoah on 2008-02-10
well........this drive was only 300 gig large.  But I still don't have a spare 300 gig drive that is empty.  When I check the properties of the drive by R clicking on it, it shows that the files are in there.  Because it is not empty.  But I have no clue how to access them now.  Let me run those other commands that you were talking about and I will post that

---

### Post by nynoah on 2008-02-10
That command did not work.....is there another way to do it?

> noah@noah-desktop:~$ sudo smartctl -d on /dev/sda
[sudo] password for noah:
sudo: smartctl: command not found
noah@noah-desktop:~$ sudo smartctl -d on /dev/sda1
sudo: smartctl: command not found
noah@noah-desktop:~$ 



---

### Post by ve9gj on 2008-02-10
> **nynoah said:**
> That command did not work.....is there another way to do it?

Sorry for the slow reply, I'm in and out this evening!
I guess I am used to Knoppix live cds, smartctl must not be included with a Ubuntu live session.  We can look at it later for now I think we can assumme the drive is bad.

So what happens when you do?

mkdir ~/new1
sudo mount -t ext3 /dev/sda1 ~/new1
 ls -l ~/new1

Does it list anything?

---

### Post by nynoah on 2008-02-10
> noah@noah-desktop:~$ mkdir ~/new1
noah@noah-desktop:~$ 
noah@noah-desktop:~$ mkdir ~/new1
mkdir: cannot create directory `/home/noah/new1': File exists
noah@noah-desktop:~$ sudo mount -t ext3 /dev/sda1 ~/new1
[sudo] password for noah:
noah@noah-desktop:~$ ls -l ~/new1
total 5756
-rwxr-xr-x  2 root root    6607 2007-09-30 17:51 bin
lrwxrwxrwx  2 root root      11 2008-01-11 10:38 cdrom -> media/cdrom
lrwxrwxrwx  2 root root      28 2008-01-11 15:04 initrd.img -> boot/initrd.img-2.6.22-14-rt
lrwxrwxrwx  2 root root      33 2008-01-11 10:48 initrd.img.old -> boot/initrd.img-2.6.22-14-generic
lrwxrwxrwx  2 root root       4 2008-01-11 10:38 lib64 -> /lib
drwx------ 76 root root   20480 2008-02-09 20:25 lost+found
-rw-r--r--  2 noah noah 5853184 2008-01-24 22:51 root
lrwxrwxrwx  2 root root      25 2008-01-11 15:04 vmlinuz -> boot/vmlinuz-2.6.22-14-rt
lrwxrwxrwx  2 root root      30 2008-01-11 10:48 vmlinuz.old -> boot/vmlinuz-2.6.22-14-generic
noah@noah-desktop:~$ 


Now just encase something looks strange.  I am on my 15 gig drive not the live CD.

Should I download a copy of Knopix?  Would that work better to recover what I am looking for?

---

### Post by ve9gj on 2008-02-10
> **nynoah said:**
> Now just encase something looks strange.  I am on my 15 gig drive not the live CD.

Should I download a copy of Knopix?  Would that work better to recover what I am looking for?

If you are on your 15g drive just use synaptic to install smartmontools and you can try the smartctl commands again.  What is your 15g drive /dev/sdb ?

if you still have /dev/sda1 mounted as ~/new1 try

sudo ls-l /home/noah/new1/lost+found
is there anything in there?

---

### Post by nynoah on 2008-02-10
Yeah checked through ALL the files in the lost and found.  No go there.  The size of my lost and found is only 2.2 gigs.  

I will download those others.

Noah

---

### Post by nynoah on 2008-02-10
Also the space 15 gig HD is a Eide......so it should be listed as "hda"  My larger drive with the problem is a SATA so it is listed as a sda....This was my understanding of the abbreviations.  Correct me if I am wrong.

---

### Post by nynoah on 2008-02-10
cut and paste after the other codes

> noah@noah-desktop:~$ sudo smartctl -d on /dev/sda
[sudo] password for noah:
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=======> INVALID ARGUMENT TO -d: on
=======> VALID ARGUMENTS ARE: ata, scsi, marvell, sat, 3ware,N, hpt,L/M/N cciss,N <=======

Use smartctl -h to get a usage summary

noah@noah-desktop:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint T133 series
Device Model:     SAMSUNG HD300LJ
Serial Number:    S0D7J1KP100517
Firmware Version: ZT100-13
User Capacity:    300,069,052,416 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Sun Feb 10 17:32:58 2008 MST
SMART support is: Available - device has SMART capability.
SMART support is: Disabled

Warning! SMART Attribute Data Structure error: invalid SMART checksum.
Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum.
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Total time to complete Offline 
data collection:                 (   0) seconds.
Offline data collection
capabilities:                    (0x00)         Offline data collection not supported.
SMART capabilities:            (0x0000) Automatic saving of SMART data                                  is not implemented.
Error logging capability:        (0x00) Error logging supported.
                                        General Purpose Logging supported.

SMART Attributes Data Structure revision number: 33188
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
232 Unknown_Attribute       0xdf03   012   000   003    Pre-fail  Always   In_the_past 21198501843712
169 Unknown_Attribute       0xe647   146   101   071    Pre-fail  Always       -       255086697644103
  1 Raw_Read_Error_Rate     0x0800   000   000   000    Old_age   Offline  FAILING_NOW 0
101 Unknown_Attribute       0x0047   000   000   071    Pre-fail  Always   FAILING_NOW 8796110055424
236 Unknown_Attribute       0x0000   000   000   000    Old_age   Offline  FAILING_NOW 0
112 Unknown_Attribute       0x00b3   000   000   179    Pre-fail  Always   FAILING_NOW 0
169 Unknown_Attribute       0x1347   044   169   071    Pre-fail  Always   FAILING_NOW 306645429575

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 164
Invalid Error Log index = 0x81 (T13/1321D rev 1c Section 8.41.6.8.2.2 gives valid range from 1 to 5)

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 33188
Warning: ATA Specification requires self-test log structure revision number = 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging
noah@noah-desktop:~$ 



---

### Post by ve9gj on 2008-02-10
> **nynoah said:**
> cut and paste after the other codes

try 
sudo smartctl -s on

sudo smartctl -d ata /dev/sda


I am not sure where to go from here.  The whole drive seems to be hosed.  If we try anything else on the drive I think we are going to make it worse.

---

### Post by nynoah on 2008-02-10
OK will stop now, and take the drive out.  I will try to borrow a external HD from a friend so that I could use that to make a mirror.

Thank you so much.........I am sure this was a real brain wracker.

Noah

---

### Post by ve9gj on 2008-02-10
There is some fille recovery tools in the package testdisk.  One of the tools is called photorec which can pull files out of a mess pretty good. It can find over 100 different file types. I have used it a couple of times before but I am certainly no expert. What kind of files do you need to recover?  

There is another tool called magicrescue but I have never used it myself.
Do you have another drive with space copy files to?

---

### Post by nynoah on 2008-02-10
I am going to get a drive from a friend hopefully............I just need to ask around and hope someone has one.   I just bought this drive 3 months from Micro Center too.............I have no clue where the receipt is though.  

I will check into those things you are talking about.  Most of the files that I want are my music files and pictures.  All the other things can be reloaded.  I have 200 gigs worth of music on there.  I don't have most of those Cds anymore either......

Ohhh life in the digital world.  

Noah

---

