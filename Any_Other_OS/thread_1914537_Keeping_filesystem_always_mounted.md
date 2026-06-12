---
title: "Keeping filesystem always mounted"
date: 2012-01-24
forum: Any Other OS
---

### Post by sunfromhere on 2012-01-24
Hello!

How can I have Ubuntu /home partition always mounted in other distros (CentOS)?

F.e. I select a wallpaper that is in Ubuntu /home, and it doesn't show until I mount it. Any way to skip manual mounting every single time I log-in?

---

### Post by Double.J on 2012-01-24
you need to make an entry in the /etc/fstab file.

```

gksudo gedit /etc/fstab
```

at the bottom add a line like the following
> 
#ubuntu home
/dev/sdaX          /path/to/mount            extX          defaults          0       0

/dev/sdaX is the partition number
/path/to/mount is where you want to mount at - i'll come to this
extX is the filesystem type - probably EXT4

As for the mount point - this is for you to choose ;)

Basically you can either use the partition to house both /home partitions, or you can mount it at a different point - /mnt, /home/ubuntu and /data are common options. to make a directory to mount at, use 
```

sudo mkdir /path/to/directory
```

If you want to use it to share both home partitions, it's best yto use a different username on each distro - I'd use jonu and jonc ;)you first rename your /home directory /home.old, then create a new directory called /home.

once made, mount the partition at /home, set the fstab file to mount at the new /home driectory, and then copy the contents of /home.old to /home - remember different user names.

If you wanted to link between the relevent folders - you'd use symlinks - don't link between things link desktop; this is the reason you don't use the same user name - the desktop settings of one woudl overwrite the settings of another! just link/share things like documents, pictures, videos etc.

Hope it helps!

---

### Post by Double.J on 2012-01-24
Just noticed you're using cent - so you'll be using 'su' instead of sudo, and gksu instead of gksudo... just be careful not to stay signed in as root ;)

---

### Post by sunfromhere on 2012-01-24
Thanks for the help, I did as you said and now it mounts on start-up (I put Desktop as mount point).

But... (there's always a but :)

symlinks from the mounted /home don't work. I need to give me root access for it to work.

Perhaps it's to do with partial permissions, I will need to recheck that. I need to give my accounts on 3 other distros full permissions to use Ubuntu /home, although I want them to have their separate /home also. :confused:

EDIT: Upon a closer inspection, the decision to mount Ubuntu /home at Desktop wasn't the brightest of ideas... Serves me right for being too lazy to create a special folder for that.
I've gone and made a mess again...

---

### Post by Double.J on 2012-01-24
Sorry for taking a while to get back to you. Yes as you've probably notice mounting at desktop isn't really for the best! Unmounting the drive and mounting at a new point is best - wherever you put it, it is best to make a directory for it to go so it doesn't just spill all over the parent diretory.

With regards to the links, did you use softlinks (symlinks)

```

ln -s /path/to/ubuntu/home/partition/ /path/to/cent/partition

```

for example - say I have mounted my ubuntu home partition at /data/ubuntu, and I want to link my pictures to ubuntu's pictures:
```

ln -s /data/ubuntu/user/Pictures /home/user/Pictures

```

Hope it helps :)

---

### Post by sunfromhere on 2012-01-25
Thanks for the reply.

I used softlinks, and now something even weirder has happened:

The Ubuntu /home/.mozilla/firefox now has 3 different subfolders folders, named something in the lines of 16-20 random letters and numbers. Three folders have appeared since I softlinked this .mozilla to CentOs and Debian.

All of these folders correctly remembers bookmarks&cache, but not saved passwords.

---

### Post by sunfromhere on 2012-01-25
Been reading about fstab a bit.

It seems this would be the problem: defaults.
According to [this]("http://ubuntuforums.org/showthread.php?t=283131") thread, default is [COLOR=Black]defaults = rw, suid, dev, exec, auto, _nouser_, and async, and [/COLOR]nouser - Only permit root to mount the filesystem. This is also a default setting.

So, it should work if I set "user" option?

EDIT: instead of "default", would "auto,user,rw" do the trick?
And of course, a smarter mount point ;)

---

### Post by Double.J on 2012-01-25
> **sunfromhere said:**
> Been reading about fstab a bit.

It seems this would be the problem: defaults.
According to [this]("http://ubuntuforums.org/showthread.php?t=283131") thread, default is [COLOR=Black]defaults = rw, suid, dev, exec, auto, _nouser_, and async, and [/COLOR]nouser - Only permit root to mount the filesystem. This is also a default setting.

So, it should work if I set "user" option?

EDIT: instead of "default", would "auto,user,rw" do the trick?
And of course, a smarter mount point ;)


Hi there, sorry, my bad!

yes, a common fstab entry for shared data would be
```
rw,auto,nouser,exec,async
```
async or sync don't really matter unless it's a removeable drive - then use sync not async :)

---

### Post by sunfromhere on 2012-01-25
This is working (atm in Debian, 2 more to go).
Even Thuderbird shows e-mails, accounts... :KS

Thanks!

---

### Post by Double.J on 2012-01-25
Glad to hear it's going well :D so long as you don't share system specific info - I've not had any problems, OS X, PC-BSD, and Linux all share the same directories for media and documents on mine :)

---

