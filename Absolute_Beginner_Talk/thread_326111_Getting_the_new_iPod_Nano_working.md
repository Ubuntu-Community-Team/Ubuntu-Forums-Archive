---
title: "Getting the new iPod Nano working"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Skraeling on 2006-12-27
I got an ipod nano for Christmas and it just wont mount
(i followed a tutorial somewhere on theses forums)
I created a mount point 
sudo dkdir /mnt/iPod
added this line to /etc/fstab
/dev/sdb /mnt/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000 ,user,defaults,noatime,iocharset=utf8 0 0
now im getting an error message:

[mntent]: line 11 in /etc/fstab is bad
mount: can't find /mnt/iPod in /etc/fstab or /etc/mtab

when the /dev/sdb is the usual (in the tutorial) /dev/sda2 it says (when i run dmesg | grep sda)

VFS: Can't find a valid FAT filesystem on dev sda2.

which is understandable since Device Manager says its in sdb

now, where is my error, or if im going about getting an ipod nano running all wrong can someone please point me to an nice more newb friendly guide to getting a brand spanking new nano running?

(oh and where does all of "/dev/sdb /mnt/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000 ,user,defaults,noatime,iocharset=utf8 0 0" come from? what do all the bits mean?)

Before i did all this i got gtkpod an it returns this error message "iPod directory structure must be present before synching to the iPod can be performed.", i checked on my windows computer, the directory is all there.

---

### Post by aosmith on 2006-12-27
if you just want music to work try amarok...
otherwise those instructions probably refrence "windows" ipods which are fat32... You need to find out which filesystem is running on your ipod.

---

### Post by adewale on 2006-12-27
try yamipod i don't know much about ipod

---

### Post by eclesh on 2006-12-28
Please see [http://ubuntuforums.org/showpost.php?p=1934664&postcount=11](http://ubuntuforums.org/showpost.php?p=1934664&postcount=11)

That's how I got my new nano working.

---

### Post by tipdrinker on 2007-12-22
I've tried to follow the steps in that example but it comes unhinged when i get to step 7. Im guessing i'm supposed to put somethin where the * part is but i dont know. I'm not good with the terminal stuff...

root@89-125-52-231:~# mkdir hal-ipod-fix && cd hal-ipod-fix
root@89-125-52-231:~/hal-ipod-fix# sudo apt-get build-dep hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list
root@89-125-52-231:~/hal-ipod-fix# apt-get source hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list
root@89-125-52-231:~/hal-ipod-fix# sudo apt-get install fakeroot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fakeroot is already the newest version.
The following packages were automatically installed and are no longer required:
  chromium-data ubuntustudio-session-splashes freetennis-common
  x11proto-gl-dev libglpng libgnorbagtk0 libstartup-notification0-dev wired
  warsow-data libsdl-sound1.2 libmikmod2 sauerbraten-data python-pysqlite2
  libflac7 wormux-data liborbit0 emerald libemeraldengine0 glob2-data
  libmpeg3-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@89-125-52-231:~/hal-ipod-fix# wget [http://librarian.launchpad.net/4838850/via-raid-fix.debdiff](http://librarian.launchpad.net/4838850/via-raid-fix.debdiff)
--23:07:55--  [http://librarian.launchpad.net/4838850/via-raid-fix.debdiff](http://librarian.launchpad.net/4838850/via-raid-fix.debdiff)
           => `via-raid-fix.debdiff'
Resolving librarian.launchpad.net... 91.189.90.247
Connecting to librarian.launchpad.net|91.189.90.247|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://launchpadlibrarian.net/4838850/via-raid-fix.debdiff](http://launchpadlibrarian.net/4838850/via-raid-fix.debdiff) [following]
--23:07:56--  [http://launchpadlibrarian.net/4838850/via-raid-fix.debdiff](http://launchpadlibrarian.net/4838850/via-raid-fix.debdiff)
           => `via-raid-fix.debdiff'
Resolving launchpadlibrarian.net... 91.189.90.235
Connecting to launchpadlibrarian.net|91.189.90.235|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,290 (2.2K) [text/plain]

100%[====================================>] 2,290         --.--K/s             

23:07:57 (152.64 MB/s) - `via-raid-fix.debdiff' saved [2290/2290]

root@89-125-52-231:~/hal-ipod-fix# patch -p0 < via-raid-fix.debdiff
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -u hal-0.5.7.1/debian/changelog hal-0.5.7.1/debian/changelog
|--- hal-0.5.7.1/debian/changelog
|+++ hal-0.5.7.1/debian/changelog
--------------------------
File to patch: cd hal-Add debian/patches/00upstream-07-hald-runner_fdleak.patch:
cd: No such file or directory
Skip this patch? [y] n
File to patch: hal (0.5.7.1-0ubuntu17) edgy; urgency=low
hal: No such file or directory
Skip this patch? [y] n
File to patch: cd hal-*
cd: No such file or directory
Skip this patch? [y] y
Skipping patch.
1 out of 1 hunk ignored
patching file hal-0.5.7.1/debian/patches/23-fix-via-raid-detection.patch
root@89-125-52-231:~/hal-ipod-fix# dpkg-buildpackage -rfakeroot
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
root@89-125-52-231:~/hal-ipod-fix# sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
root@89-125-52-231:~/hal-ipod-fix# 


what am i doing wrong?

---

### Post by eclesh on 2007-12-28
> **tipdrinker said:**
> 
root@89-125-52-231:~# mkdir hal-ipod-fix && cd hal-ipod-fix
root@89-125-52-231:~/hal-ipod-fix# sudo apt-get build-dep hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list
root@89-125-52-231:~/hal-ipod-fix# apt-get source hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

You need to add the source repositories (in Synaptic, click "sources" or something for each repository).

Note, though, that modern Ubuntu (Gutsy) won't need these steps to make it work, AFAIK.  Most iPods should be recognized immediately (except iPhone, and maybe iPod Touch.  These steps won't help it though.)  If an iPod still doesn't work, it probably warrants a new and different bug for the bug tracker.

---

