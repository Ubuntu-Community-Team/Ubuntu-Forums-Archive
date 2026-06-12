---
title: "Fatal Error!"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ira miles on 2007-04-16
Hi all, 
I am moving along slowly here. I have had some difficulty installing new programs. Add remove won't start and synaptic manager is no help (as far as I can tell). I can't get easy ubuntu to do anything etc, etc.......
So, I saw where one thread suggested to try it out of the install cd, which I did and I installed xchat and got it to work. When I went to see if it worked when I booted up on mu HD, I got the following alert when I agreed to some upgrade prompts (the whole thing is foreign to me as I am a total newbie):

A fatal error occured

Please report this as a bug and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.

In the alert it reads:


Traceback (most recent call last):

  File "/tmp/distupgrade.Yl4236/edgy", line 40, in ?
    app.run()

  File "/tmp/distupgrade.Yl4236/DistUpgradeControler.py", line 765, in run
    self.edgyUpgrade()

  File "/tmp/distupgrade.Yl4236/DistUpgradeControler.py", line 706, in edgyUpgrade
    if not self.updateSourcesList():

  File "/tmp/distupgrade.Yl4236/DistUpgradeControler.py", line 289, in updateSourcesList
    self.sources.backup(self.sources_backup_ext)

  File "/tmp/distupgrade.Yl4236/aptsources.py", line 325, in backup
    shutil.copy(source.file,"%s%s" % (source.file,backup_ext))

  File "shutil.py", line 81, in copy
    copyfile(src, dst)

  File "shutil.py", line 47, in copyfile
    fsrc = open(src, 'rb')

IOError: [Errno 2] No such file or directory: '/etc/apt/sources.list'

---

### Post by Happy_Man on 2007-04-16
Uh... are you running Feisty?

---

### Post by ira miles on 2007-04-16
Uhm, how do I tell? I just downloaded Friday.

---

### Post by Happy_Man on 2007-04-16
Go to System --> About Ubuntu.

---

### Post by ira miles on 2007-04-16
Thank you for your interest in Ubuntu 6.10
                - the Edgy Eft - released in October 2006.

---

### Post by thelinuxguy on 2007-04-16
Create the file /etc/apt/sources.list
```

gksudo gedit /etc/apt/sources.list

```
and paste the following (from my Edgy system's sources.list)
```

deb http://in.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://in.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://in.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ubuntu.beryl-project.org edgy main
deb http://ubuntu.citadel.org/ubuntu/ edgy main

```

I have some extra sources added in case you want them later.

---

### Post by ira miles on 2007-04-16
ira@IraMiles:~$ gksudo gedit /etc/apt/sources.list
(gedit:6287): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Happy_Man on 2007-04-16
Never mind that error, it's normal. (yeah, I know.) Did gedit open, though?

---

### Post by ira miles on 2007-04-16
Yes, I didn't know it was supposed to though. This is sucha foreign environment for me. Thanks for your help1!! Do I paste the subsequent text in gedit or in terminal?

---

### Post by Happy_Man on 2007-04-16
gedit.

---

### Post by ira miles on 2007-04-16
Ok, then save? Then what? Reboot? Sorry I'm such a noob. I knew what to do on a mac.....kinda

---

### Post by Happy_Man on 2007-04-16
Then save. No need to reboot. After, go to a terminal and enter

```

sudo apt-get update && sudo apt-get upgrade

```

If it works, everything is a-ok. If not, post the errors.

---

### Post by ira miles on 2007-04-16
It's like the first time I did something else...i don't know what i am doing but something is happening....weeeeeee

---

### Post by ira miles on 2007-04-16
> **Happy_Man said:**
> Then save. No need to reboot. After, go to a terminal and enter

```

sudo apt-get update && sudo apt-get upgrade

```

If it works, everything is a-ok. If not, post the errors.

Oh, I just saw this....I had opened easyubuntu and it started working
FYI it says that citadel repository can't be reached and then gave me an alert, but I just clicked through it. Think it is all good. I will keep you posted....thanks a bunch.

---

### Post by ira miles on 2007-04-16
ira@IraMiles:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Ign [http://ubuntu.citadel.org](http://ubuntu.citadel.org) edgy Release.gpg
Ign [http://ubuntu.citadel.org](http://ubuntu.citadel.org) edgy/main Translation-en_US
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/main Translation-en_US
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/restricted Translation-en_US   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/multiverse Translation-en_US   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/universe Translation-en_US     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy Release                        
Ign [http://ubuntu.citadel.org](http://ubuntu.citadel.org) edgy Release                           
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US     
Ign [http://ubuntu.citadel.org](http://ubuntu.citadel.org) edgy/main Packages
Get:3 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release [2961B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/main Packages                       
Err [http://ubuntu.citadel.org](http://ubuntu.citadel.org) edgy/main Packages                          
  404 Not Found
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/universe Packages
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/universe Sources
Fetched 3153B in 1s (3076B/s)
Failed to fetch [http://ubuntu.citadel.org/ubuntu/dists/edgy/main/binary-powerpc/Packages.gz](http://ubuntu.citadel.org/ubuntu/dists/edgy/main/binary-powerpc/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Happy_Man on 2007-04-16
That's okay, you're good! Congrats! 

Note: about the part at the bottom, that will be addressed if/when you install Beryl. For now, don't worry.

---

### Post by ira miles on 2007-04-16
Wow, thanks, Happy_Man...it really is pretty easy with a little help! You're the best!

---

