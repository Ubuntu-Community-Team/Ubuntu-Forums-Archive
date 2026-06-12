---
title: "Fstab, Dual Boot, Sharing a User"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by kaan on 2008-01-17
Hi, I am currently dual booting Gutsy Gibon and Vista. I have a 500 GB second hard disk that is formatted with NTFS. I moved my entire user files to this folder. Now I want it to be automatically mounted to the User Directory in Ubuntu, so that I don't have two sets of Documents, Desktop, Videos, etc..

So I have the following line in fstab:

/dev/sda1     /home/username      ntfs         $defaults          0  0 

This kind of works in the console. I am able to see all my files and probably write to them as well, haven't tried, They are, however, marked owned by root : plugdev. This does not sit well with gnome. When I start my session it complains about one of its configurations files having the wrong owner and permissions and quits. How do I make it so that after mounting all the files and directories on the drive are owned by username : username and have (770) rwxrwx___ permissions?

I realize I can mount the drive as /media/winuser and replace Documents, Desktop, etc... with symbolic links but I would prefer to have everything on the one drive. So how do I set the permissions and user in the fstab line?

---

### Post by kaan on 2008-01-17
I think i found the solution myself. I'm not so sure because I am at work and the computer I wan't to do it on is at home, but im guessing

either

/dev/sda1 /home/username ntfs $defaults,uid=001,gid=001,umask=007  0 0 

or

/dev/sda1 /home/username ntfs $defaults,uid=001,gid=001,fmask=117,dmask=007  0 0 

will work well for me. The latter, with all files marked -x  seems more sane but i guess ill have to make gcc output binaries somewhere else.

I am starting to think it might be better if i create a small ext3 partition on the same disk and mount as follows:

/dev/sdb1 /media/winuser ntfs $defaults,uid=001,gid=001,fmask=117,dmask=007  0 0 
/dev/sdb2 /home/username ext3 $defaults 0 0 

and then just use symbolic links for the common parts. 

Has anyone done anything similar to this? I wouldn't mind some input.

---

