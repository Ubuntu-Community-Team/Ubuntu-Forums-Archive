---
title: "How do I view My Ubuntu files from Mac OS X?"
date: 2015-07-22
forum: Apple Hardware Users
---

### Post by Turon on 2015-07-22
Is it possible to make my Ubuntu drive viewable from Mac OS X? I'd like to be able to view and copy files across...

---

### Post by este.el.paz on 2015-07-22
> **Turon said:**
> Is it possible to make my Ubuntu drive viewable from Mac OS X? I'd like to be able to view and copy files across...

Short answer, no--OSX is a "jealous" lover and doesn't "see" any system except itself.  Some OSX files **might** be seen via linux side, but many are "blocked."  Best of both worlds is some "virtual" program, like Parallels or VB, so you are running linux in OSX, then might be possible to "file share" . . . otherwise, it's like two ships passing in the night . . . .

---

### Post by SeijiSensei on 2015-07-22
I wouldn't be so sure the situation is that bleak: [http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/](http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/)

I'd be careful about trying to write to the Linux filesystem though.  
> While OSXFuse adds EXT read support, write support to EXT is disabled by default and probably not recommended to use at all, it’s considered experimental and unsupported by FUSE for a reason. 

Copying from Ubuntu to OS X should work though.

---

### Post by este.el.paz on 2015-07-24
> **SeijiSensei said:**
> I wouldn't be so sure the situation is that bleak: [http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/](http://osxdaily.com/2014/03/20/mount-ext-linux-file-system-mac/)

I'd be careful about trying to write to the Linux filesystem though.  


Copying from Ubuntu to OS X should work though.

@Seiji:

Since the OP doesn't seem to be responding, I will say, thanks, that does look interesting and worth (free) looking into.  I don't know whether that ***actually*** meets the expectations of the OP question for "view AND copy" . . . assumption being "back and forth" . . . .  This it seem would let you "view" from OSX, and, what, drag over from Linux to OSX, not "write" to Linux from OSX.  That, as I mentioned probably could be done from Parallels or something like that, running Linux in "virtual" within OSX . . . .

e..

---

### Post by Turon on 2015-07-25
I guess in that case I'll have to be content with sharing files via flashdisk...

---

### Post by farukajam12345 on 2015-07-27
i use on my mac with this prosess 


[http://osxfuse.github.io/](http://osxfuse.github.io/)


fast install   fuse   application  on your mac os x 
then restart


 then use following command on terminal string to enable write support:


[LIST]
[*]sudo sed -e  's/OPTIONS="auto_xattr,defer_permissions"/OPTIONS="auto_xattr,defer_permissions,rw+"/'  -i .orig /System/Library/Filesystems/fuse-ext2.fs/fuse-ext2.util 
[/LIST]

then restart

  
                                                           in your terminal type 

                                                            mkdir /Volumes/Linux

 ENTER    then  TYPE
                                                            sudo mount -t fuse-ext2 /dev/disk0s6 /Volumes/Linux

than type your password  ........ and  mount
 
   here my linux partion drive is                      /dev/disk0s6 

you got full controll on this partion... read , write.. every thing


guaranteed   on my mac,,, replay me  if you need full video proof


best regards by faruk

---

### Post by vishal733 on 2015-08-09
I have a few comments.

(1) I have been using FUSE from OSX to view linux. and It works well. I haven't enabled write to ext because I do not want to risk losing my linux partition (since FUSE themselves do not recomment the write operation)

(2) For a safe data exchange between mac and linux, I have create a separate partition on my HD.
I tried the following following filesystems on the shared drive:
(i) exFAT: This is supported by both mac and linux (after installation of a package). But for some reason after around 20 days of usage, the exFat drive started saying it was corrupted. I lost all my data

(ii) Unjournaled HFS+: This in my opinion is the best option. Mac can obviously read it. And Linux can write to unjournaled HFS+ partitions. By default Mac creates a journaled HFS+ partition, which cannot be written to from linux.
NOTE: I will suggest do not try converting your existing Mac partitions with OSX system into unjournaled HFS+. Just create a separate drive and do your experiments.

---

