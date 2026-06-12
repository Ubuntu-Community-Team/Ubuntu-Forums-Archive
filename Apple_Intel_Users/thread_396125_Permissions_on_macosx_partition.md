---
title: "Permissions on macosx partition"
date: 2007-03-29
forum: Apple Intel Users
---

### Post by scorpio2002 on 2007-03-29
Hi there. I'm using Ubuntu Feisty on a macbook first generation. When I mount the hfsplus partition from within Gnome, it gets mounted with some kind on permissions and i can't get into my macos home directory. How do I tell Ubuntu to mount it giving my user full permissions? (maybe at start-up...).

Thanks in advance.

---

### Post by oskarloko on 2007-03-29
The default driver for HPF+ ( the MacOsX filesystem ) is readonly. 
A writing-enable driver exists, but it's experimental and has some bugs..

( as far as I know )

So you can read from MacOsX partition, but don't try to write....

---

### Post by scorpio2002 on 2007-03-29
Yeah... I didn't mean that. i want to be able to access (aka read, not write) every directory in mi hfs+ partition. But, if i'm noot root, it doesn0t let me read all the directories in the partition..

---

### Post by Gen2ly on 2007-03-29
Yeah, thats default linux behavor.  Try accessing /root as a normal user you'll have the same exact response.  I haven't tried it but changing permssions here may be risky.  If there is still the option, make a 3rd partition (e.ge OS X, Linux, Shared) if you want to be able to access documents in both Mac OS X and Ubuntu.

---

### Post by siepo on 2007-03-29
I changed my osx uid to match my linux uid, and that did it. IIRC, I logged in with a separate admin account and changed the uid from within netinfo, and after that I did a chown on my home directory to make it mine again.

---

### Post by Gen2ly on 2007-03-30
you can change your Mac OS X uid safely?  That surprises me as this is very dangerous in linux.  I don't use OSX very much could explain in a little more detail?  Is netinfo a command line utility?

---

### Post by siepo on 2007-03-30
I don't know how safe it was, but it went allright. Netinfo Manager is a GUI application that you can find in the Applications/Utilities folder. You get an interface like the Finder column view. Navigate to /users/<your user name> and you'll find a uid entry.

The chown command that you need afterwards is

chown -R /Users/<your user name>:<your user name>

---

### Post by cyberdork33 on 2007-03-30
I have no issues... I mount the OSX partition in fstab as follows:
```
/dev/sda2       /home/username/OSX           hfsplus user,rw 0 0
```

Before people jump on me, I know write is dangerous...

---

### Post by Gen2ly on 2007-03-30
This could be useful.  I had a third (Shared) partition formatted as HFSplus before but abandoned it and formatted is FAT32.  Thanks.

---

### Post by ronocdh on 2007-03-31
Siepo, Cyberdork, both very helpful, thank you! I'm going to give both a whirl and see whether I can't have full sharing between my parties.

---

### Post by Gen2ly on 2007-04-02
I changed my UID successfully.  Appears all is well.  Tomorrow I'll transfer my files to another partition and format my Shared Partition as HFSplus.  I also think its important to note that its a good idea to have the user names the same as well.  I forgot FAT32 only allows files up to 1 GB.  I was backup up linux when it happened.  Strangely it did accept it ( a 4.3 GB file ) though I didn't trust it and decided to copy it to my OS X partiiton.  I'll tell more tomorrow.

---

### Post by ronocdh on 2007-04-02
Much luck! However, I must mention that I have come to using ext3 as the FS to share between all my computers (my towers at home both dual boot Linux and XP). This way I can grab any drive and plug it into any computer, and all is well.

For Windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)
For OS X: [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

Both have treated me very well over the past several months.

---

### Post by Gen2ly on 2007-04-03
Well, I successfully did it!  I converted an FAT32 partition that I used to shared between OS X and Linux and converted it to HFS+.  All file permissions match and it's running absolutely perfect.  I can now backup my Linux and won't be stopped by the 4 GB limit.    Thanks to sepio who told me it could be done, and ronocdh, I like your idead as well.  I put the infomation in the [Gentoo-Wiki]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Using_the_4th_partition_for_Swap.2C_Boot_or_Shared_Partition") as it seem a nice place for it.

---

### Post by darkmaster on 2007-04-05
Boys, I need a simple way to access to my Mac HD folders as a normal user. I do not whant the rights to modify files! I just whant to be able to read them! For example, I need my Music in the Mac HD, I cannot use double the space needed because of this! As a normal user, I cannot even enter into the music dir... any help?

in fstab I automount at boot my Mac HD with this line:
/dev/sda2       /media/osx           hfsplus user,rw 0 0

And yet, as a normal user, I cannot access some folders...

---

### Post by cyberdork33 on 2007-04-05
If you don't need to modify files then use 'ro' instead of 'rw' in fstab

ok try this:

```
/dev/sda2    /media/osx    hfsplus    user,ro,umask=0644    0 0
```

That should make ubuntu see all the files on that mount as readable.

---

