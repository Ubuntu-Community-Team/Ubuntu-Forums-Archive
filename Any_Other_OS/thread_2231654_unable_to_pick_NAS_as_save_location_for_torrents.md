---
title: "unable to pick NAS as save location for torrents"
date: 2014-06-26
forum: Any Other OS
---

### Post by tony49 on 2014-06-26
so i have my NAS mounted under Network and am able to move and use files like normal with the drive. the problem comes when i try to make this drive my save location for torrents. i tried using qBittorrent and Deluge both no luck. the drive does not appear on the "choose a save directory window" through each application. i was able to see a folder in the NAS if i went to "recently used" in the qBittorrent "choose a save directory window" but when i choose it an error appeared. it said "qbittorrent cannot change to folder because it is not local". so im not sure what to do as the drive is currently mounted. am i missing something?

---

### Post by nerdtron on 2014-06-27
> qbittorrent cannot change to folder because it is not local

I guess it says right here. There is nothing wrong on your NAS. It is just the program you are using, qbittorent, does not support saving on a network drive.
Either you can manually move your torrents to the NAS folder or write a script to automatically do it for you.
Or try using other torrent clients and see if they support saving on a network drive. There are a lot of torrent clients on the software center. I haven't tested many of them so I can't recommend which to install.

---

### Post by Toz on 2014-06-27
If you mounted the NAS drive via Thunar's Network link, it would have been mounted by gvfs, meaning that the actual mount point is located in the /run/user/1000/gvfs directory (assuming your userid is 1000). Try setting the save location to the NAS mount point in that directory to see if it works.

If you still get a "not local" error message, you can try creating a link to that directory in your home directory and pointing the app to that link.

---

### Post by tony49 on 2014-06-28
ok so i was able to select  /run/user/1000/gvfs as the save location with no error. it downloaded in that folder but.. that is not my NAS. it just dl'ed to my local harddrive. where would it be on my NAS if i chose that directory? 

maybe someone can recommend a bit torrent client that will work for me?

---

### Post by Tadaen_Sylvermane on 2014-06-29
I tested a setup like that once. Shared out a folder on my server and mounted it at /home/$USER/Downloads. I built my file server though, currently running Ubuntu using samba (don't preach nfs please, real world test shows less than 1% difference in speed for me at least). If you can mount the nas to a local folder then the torrent client will see it as just another drive / folder. Going through the Network tab is sketchy at best and I gave up on that after a good while. Is also more convenient I find mounting it properly as you can work with it as just another folder / partition on your computer.

Network speed is why I didn't keep that setup though. Wired isn't practical at my house and wireless is only 4 megs a second give or take. If had desktop with 1gbe+ ... wouldn't do it any other way.

---

### Post by Toz on 2014-06-29
> **tony49 said:**
> ok so i was able to select  /run/user/1000/gvfs as the save location with no error. it downloaded in that folder but.. that is not my NAS. it just dl'ed to my local harddrive. where would it be on my NAS if i chose that directory? 
It wouldn't be the /run/user/1000/gvfs directory, but a directory inside that directory. It would only exist after you mounted it with Thunar.

---

### Post by tony49 on 2014-07-06
> **Tadaen_Sylvermane said:**
> I tested a setup like that once. Shared out a folder on my server and mounted it at /home/$USER/Downloads. I built my file server though, currently running Ubuntu using samba (don't preach nfs please, real world test shows less than 1% difference in speed for me at least). If you can mount the nas to a local folder then the torrent client will see it as just another drive / folder. Going through the Network tab is sketchy at best and I gave up on that after a good while. Is also more convenient I find mounting it properly as you can work with it as just another folder / partition on your computer.

Network speed is why I didn't keep that setup though. Wired isn't practical at my house and wireless is only 4 megs a second give or take. If had desktop with 1gbe+ ... wouldn't do it any other way.

i see so mounting to the Network tab is not mounting it locally? i had some issues mounting the drive and made a thread about here: [http://ubuntuforums.org/showthread.php?t=2230024&p=13051621#post13051621](http://ubuntuforums.org/showthread.php?t=2230024&p=13051621#post13051621)

the only way i was able to access the drive was writing the NAS address in file manager...  but i guess thats not compatible with saving directly to the drive as its not local.
> **Toz said:**
> It wouldn't be the /run/user/1000/gvfs directory, but a directory inside that directory. It would only exist after you mounted it with Thunar.
no directory exist inside that directory..

perhaps i need to try to mount the drive some other way again. from the original thread it was still unclear where my issue was so im not sure my next move.

---

### Post by tony49 on 2014-07-06
im noticing now the following lines when attempting to mount the drive:

mount error: cifs filesystem not supported by the system
mount error(19): No such device

---

### Post by Toz on 2014-07-06
> **tony49 said:**
> mount error: cifs filesystem not supported by the system
Make sure you have the **cifs-utils** package installed. Look for it in the Software Centre or:
```
sudo apt-get install cifs-utils
```

---

### Post by tony49 on 2014-07-06
yup its already installed

---

### Post by Toz on 2014-07-06
That's odd. Can you tell us a bit more about your system:

1. Version of Ubuntu:
```
cat /etc/lsb-release
```

2. Your kernel and architecture information:
```
uname -a
```

3. Status of cifs-utils:
```
apt-cache policy cifs-utils
```

4. Exactly what command did you use when you attempted to mount the drive?

---

### Post by tony49 on 2014-07-06
> **Toz said:**
> That's odd. Can you tell us a bit more about your system:

1. Version of Ubuntu:
```
cat /etc/lsb-release
```
**DISTRIB_ID=Ubuntu**
**DISTRIB_RELEASE=13.10**
**DISTRIB_CODENAME=saucy**
**DISTRIB_DESCRIPTION="Ubuntu 13.10"**



2. Your kernel and architecture information:
```
uname -a
```**Linux localhost 3.8.11 #1 SMP Mon Jun 9 02:39:27 PDT 2014 x86_64 x86_64 x86_64 GNU/Linux**


3. Status of cifs-utils:
```
apt-cache policy cifs-utils
```
**Installed: 2:6.0-1ubuntu2**
**  Candidate: 2:6.0-1ubuntu2**
**  Version table:**
** *** 2:6.0-1ubuntu2 0**
**        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages**
**        100 /var/lib/dpkg/status**


4. Exactly what command did you use when you attempted to mount the drive?
**sudo mount.cifs //<ip address of NAS>/<sharename> /mnt/tony -o user=tony**


[COLOR=#000000]first i followed these instructions [/COLOR][http://cocoaallocinit.com/2014/01/04...nas-on-ubuntu/]("http://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/")
then i tried about 10 other ways but nothing has worked besides just putting the address into the file manager and pulling it through network

---

### Post by Morbius1 on 2014-07-07
OK, so I installed Deluge on one Xubuntu, created a samba share on another, and made a connection to it via Thunar.

I can set the download location to the local mount point of the remote share without error:[ATTACH=CONFIG]254536[/ATTACH]
I can start the download without error: [ATTACH=CONFIG]254537[/ATTACH]
And when it's done I have on the samba server the downloaded file: [ATTACH=CONFIG]254538[/ATTACH]

There may be an issue with the particular NAS device you are using but I don't think it's with Thunar, gvfs, it's local mount point, or Deluge.

If you have to mount it manually I would suggest changing this:
> sudo mount.cifs //<ip address of NAS>/<sharename> /mnt/tony -o user=tony
To this:
```
sudo mount -t cifs //<ip address of NAS>/<sharename> /mnt/tony -o user=tony,password=something,uid=1000
```

The way you had it before:
** user=tony refers not to the local user but the user name required to gain access on the NAS.
** You passed a user name but no password so I added that to the command.
** Depending of how the samba server is set up you never specified permissions on the local mount point in the command so by default it would have mounted it with read / write access to root and read access to everyone else. So I added the uid=1000 to make it r/w to you ... assuming you are 1000.

One more thing. A lot of these NAS devices are fixated on using a version of Samba that was state of the art .... in 1999. You may have to add another option to your list if this is the case with yours - sec=ntlm. So the command would become:
```
sudo mount -t cifs //<ip address of NAS>/<sharename> /mnt/tony -o user=tony,password=something,uid=1000,sec=ntlm
```

---

### Post by tony49 on 2014-07-07
sudo mount -t cifs //<ip address of NAS>/<sharename>  /mnt/tony -o user=tony,password=<mypass>,uid=1000,sec=ntlm
mount error: cifs filesystem not supported by the system
mount error(19): No such device
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

same deal :(

btw tony is the user name for the NAS not the local user.

and i know that this perticular model NAS can be mounted in linux as the instruction link indicates: [http://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/](http://cocoaallocinit.com/2014/01/04/wd-my-cloud-nas-on-ubuntu/)

can it be that cifs are not enabled somewhere? why would it say not supported..

but yeah what you did is exactly what im trying to achieve.

---

### Post by tony49 on 2014-07-07
so i just tried following these instructions: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

but on the last step i got the following error

sudo mount -a
bad option uid="tony"

edit/ so i realized uid is your ubuntu user name not your NAS user name but then i got

sudo mount -a
mount error: cifs filesystem not supported by the system
mount error(19): No such device
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

LOL cant win

---

### Post by Toz on 2014-07-08
You state in your original post that you "have my NAS mounted under Network and am able to move and use files like normal". Do you mean, that within Thunar, if you click on Network, it shows up as an icon?

If so, do that again so that it's accessible (i.e. you can move files to it), then post back the results of:
```
ls -l /run/user/1000/gvfs
```

---

### Post by tony49 on 2014-07-08
i can only click on browse network and the only thing there is "windows network" which i cant access. below that are the two mounted directories from my NAS
[ATTACH=CONFIG]254582[/ATTACH]

and my results

ls -l /run/user/1000/gvfs
total 0

---

### Post by Toz on 2014-07-08
How did you mount those directories? 

What does the following say?
```
mount
```

---

### Post by tony49 on 2014-07-08
i mounted those just by going to file manager and in the address bar typing: smb://<ip of NAS> nas/

from the command "mount" i got:
/usr/local/chroots/saucy on / type ecryptfs (rw,relatime,ecryptfs_fnek_sig=4169acdfdb76739d,ecryptfs_sig=627271078b3895b8,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
devtmpfs on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=1992096k,nr_inodes=498024,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620)
shmfs on /dev/shm type tmpfs (rw,nosuid,nodev,noexec,relatime)
tmp on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=398648k,mode=755)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
varrun on /var/host/dbus type tmpfs (rw,nosuid,nodev,noexec,relatime,mode=755)
varrun on /var/host/shill type tmpfs (rw,nosuid,nodev,noexec,relatime,mode=755)
varrun on /var/host/cras type tmpfs (rw,nosuid,nodev,noexec,relatime,mode=755)
/dev/mapper/encstateful on /var/host/timezone type ext4 (rw,nosuid,nodev,noexec,relatime,discard,commit=600,data=ordered)
/dev/root on /lib/modules/3.8.11 type ext2 (ro,relatime)
media on /var/host/media type tmpfs (rw,nosuid,nodev,noexec,relatime)
/home/.shadow/97006d66eb09124fdd6d6c7804ad96d46c342aa5/vault on /home/newage51/Downloads type ecryptfs (rw,nosuid,nodev,relatime,ecryptfs_sig=45894b2f493cfd1a,ecryptfs_fnek_sig=1c1995e132f123da,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime,gid=236,mode=750)
none on /sys/fs/cgroup type tmpfs (rw,nosuid,nodev,noexec,relatime,mode=755)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,nosuid,nodev,noexec,relatime,cpu)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,name=systemd)

---

### Post by Toz on 2014-07-08
That's one interesting setup you have there. Is saucy running in a chroot? Can you tell us more about it?

Can I see a few more things:
```
ls -l /run/user/$UID/gvfs
```
```
dpkg -l | grep gvfs
```

And on a wild guess that shouldn't work:
```
ls -l ~/.gvfs
```

---

### Post by tony49 on 2014-07-08
well im on a Dell 11 Chromebook and then installed crouton as shown here: [http://www.cnet.com/how-to/how-to-run-both-chrome-os-and-ubuntu-on-a-chromebook/](http://www.cnet.com/how-to/how-to-run-both-chrome-os-and-ubuntu-on-a-chromebook/)

these are my results:
(saucy)newage51@localhost:~$ ls -l /run/user/$UID/gvfs
total 0
(saucy)newage51@localhost:~$ dpkg -l | grep gvfs
ii  gvfs:amd64                            1.18.2-0ubuntu1                        amd64        userspace virtual filesystem - GIO module
ii  gvfs-backends                         1.18.2-0ubuntu1                        amd64        userspace virtual filesystem - backends
ii  gvfs-bin                              1.18.2-0ubuntu1                        amd64        userspace virtual filesystem - binaries
ii  gvfs-common                           1.18.2-0ubuntu1                        all          userspace virtual filesystem - common data files
ii  gvfs-daemons                          1.18.2-0ubuntu1                        amd64        userspace virtual filesystem - servers
ii  gvfs-libs:amd64                       1.18.2-0ubuntu1                        amd64        userspace virtual filesystem - private libraries
(saucy)newage51@localhost:~$ ls -l ~/.gvfs
ls: cannot access /home/newage51/.gvfs: No such file or directory

---

### Post by Toz on 2014-07-08
I'm somewhat baffled.

Can you run this command:
```
gvfs-info smb://<IP-OF-NAS>/public
```
...of course replacing <IP-OF-NAS> with the actual ip of the nas. I want to see what gvfs says about the share.

---

### Post by tony49 on 2014-07-08
Error getting info: The specified location is not mounted

---

### Post by Toz on 2014-07-09
I wonder if this has something to do with Crouton. I'm not that familiar with it but from what I've just read, it seems to install its own version of the kernel. This may be the issue. I also found [this post]("https://github.com/dnschneid/crouton/wiki/How-to-mount-network-shares-on-Chromebook-using-smbnetfs") that talks about mounting samba shares which is different from stock ubuntu. 

I'm going to move this thread to the *Other OS/Distro Support* sub-forum as I believe crouton is significantly different from Ubuntu.

---

### Post by tony49 on 2014-07-09
o yeah maybe thats the issue. i have not come across this instruction you linked to, thanks. will this only work while in the chrome os, or will this work in ubuntu?

---

### Post by tony49 on 2014-07-09
so just tried to follow the steps and encountered some problems

first:
[LIST=1]
[*]Create smbnetfs configuration file ( touch ~/.smb/smbnetfs.conf
[/LIST]
said no such file or directory so i just went into my ubuntu and created the path and file

then:
when trying to mount
(precise)newage51@localhost:~$ smbnetfs ~Downloads/Network
WARNING!!! Configuration directory /home/newage51/.smb is not found. Please create it.
This directory should contain at least two files: smb.conf and smbnetfs.conf.
You may copy smb.conf from the /etc/samba directory. You can find a sample of
smbnetfs.conf in the /etc directory.

Using default settings for now.
fuse: bad mount point `~Downloads/Network': No such file or directory
(precise)newage51@localhost:~$ mkdir ~/Downloads/Network
mkdir: cannot create directory `/home/newage51/Downloads/Network': File exists
(precise)newage51@localhost:~$ smbnetfs ~/Downloads/Network
WARNING!!! Configuration directory /home/newage51/.smb is not found. Please create it.
This directory should contain at least two files: smb.conf and smbnetfs.conf.
You may copy smb.conf from the /etc/samba directory. You can find a sample of
smbnetfs.conf in the /etc directory.

Using default settings for now.
fusermount: failed to open /etc/fuse.conf: Permission denied
fusermount: failed to access mountpoint /home/newage51/Downloads/Network: Permission denied
(precise)newage51@localhost:~$ sudo smbnetfs ~/Downloads/Network
WARNING!!! Configuration directory /home/newage51/.smb is not found. Please create it.
This directory should contain at least two files: smb.conf and smbnetfs.conf.
You may copy smb.conf from the /etc/samba directory. You can find a sample of
smbnetfs.conf in the /etc directory.

Using default settings for now.
fuse: bad mount point `/home/newage51/Downloads/Network': Permission denied
(precise)newage51@localhost:~$ 

so now im stuck with these instruction which im not sure will work for my application..

---

### Post by tony49 on 2014-07-10
do you guys think i would just be better off installing a full version of linux([FONT=Georgia]chrUbuntu)[/FONT] on my chromebook? crouton allows for switching back and forth but it seems to have its draw backs regarding mounts..

[http://it-nthusiast.blogspot.com/2013/05/ubuntu-linux-on-chromebook-crouton-vs.html](http://it-nthusiast.blogspot.com/2013/05/ubuntu-linux-on-chromebook-crouton-vs.html)

---

### Post by tony49 on 2014-07-13
the issue was crouton. as its not a full version of ubuntu i guess mounting the drive in such a way to allow full capabilities is impossible. i solved this by factory resetting the chromebook and install chrubuntu. my NAS was visible and accessible under Network which was not possible before. i then could choose it as a local drive in my torrent save location. thanks for the help guys!

---

### Post by A.M.Danischewski on 2015-03-13
> **tony49 said:**
> the issue was crouton. as its not a full version of ubuntu i guess mounting the drive in such a way to allow full capabilities is impossible. i solved this by factory resetting the chromebook and install chrubuntu. my NAS was visible and accessible under Network which was not possible before. i then could choose it as a local drive in my torrent save location. thanks for the help guys!

I know this post is marked SOLVED already but this may be useful since the OP said he had to reinstall. 

In the future if you have problems with cifs on Crouton you can take a look at the following link on how to compile your own Crouton compatible kernel module:  

[https://github.com/dnschneid/crouton/wiki/Build-chrome-os-kernel-and-kernel-modules](https://github.com/dnschneid/crouton/wiki/Build-chrome-os-kernel-and-kernel-modules) 

Or you can search online and find a compatible pre-built cifs.ko, but you have to make sure to unlock module locking before you can dynamically insert the new kernel module. 

E.g. 

$ sudo chmod 0666 /sys/module/lsm/parameters/module_locking
$ echo 0 > /sys/module/lsm/parameters/module_locking

$ sudo insmod /your/favorite/place/for/cifs.ko

A bit late, but you have an alternate solution for next time.

---

