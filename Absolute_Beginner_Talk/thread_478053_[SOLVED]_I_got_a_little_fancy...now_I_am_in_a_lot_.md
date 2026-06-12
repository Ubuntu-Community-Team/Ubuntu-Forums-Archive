---
title: "[SOLVED] I got a little fancy...now I am in a lot of trouble."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by mfxp on 2007-06-18
Hello out there.

Here is what I did.

I am in 7.04 and I was trying to set up a partition so I could read AND write from my XP dual boot, the dive on XP is F:

I got fancy copied the /etc/fstab file (so I do have a back up) and modified the file like I thought I could - I loaded the nfts-g3 or something,  too.

I think I picked the wrong partition because when I rebooted my Ubuntu boot partition complained that it was read-only.  

So being the creative one I loaded the 7.04 installation disk and have been hitting the net trying everything in the terminal, and to make matters worse it HIT back.  The poor CD in the drive cracked....so I will be creating another ISO file tomorrow at work.

Here are the steps I think I have to go through to back to square one ... but I have no idea how to do this.

1.  Boot from a installation disk - under one of the options (is there a better one?)
2. Open up the terminal
3. execute sudo fdisk -l    (I see the partition there it is /dev/hda3)
4. I am assuming I have to mount it. some command something like sudo mount /dev/hda3 or sudo mount -0 remount /dev/hda3 / ext3 ????

5.  Give myself some form of permission      sudo chmod 777 /dev/hda3 ???
6. Magically "change" to that partition (drive?)
7. Get to the /etc/fstab  subdirectory
8. copy (rename) the old file back to the new file
9. Reboot

Hopefully someone out there has been down this road and can fill in my many blanks...

Thanks.... I'll check this tomorrow when I have my New CD.....I think I will have the strength to "hit back" on this problem.

---

### Post by atria on 2007-06-18
If i remember correctly there is no easy way to mount a ntfs partition with ntfs-3g on boot since fuse is not in the root directory. If you want to mount your ntfs partition using ntfs-3g (assuming that your ntfs volume is sda2), try making sure that your fstab entry looks something like

```
/dev/sda2 /media/sda2     ntfs-3g    defaults,nls=utf8,noauto 0       1
```

If you need access controls, use the umask mount option instead of chmod so that the resulting entry looks like

```
/dev/sda2 /media/sda2     ntfs-3g    defaults,nls=utf8,umask=077,uid=1000,noauto 0       1
```

where the user you want to give full read/write/execute access to has a uid of 1000.

You can also mount the volume using this command without editting your fstab:
```
sudo mount -t ntfs-3g -o defaults,nls=utf8 /dev/sda2 /media/sda2
```

Hope that helps

---

### Post by mfxp on 2007-06-20
Thank you for your response.  I looked at your response and some other sites and played around a bit and this is what *discoveries* I made.


First don´t play with fstab. Just kidding I intend to go back and use some of atria´s  suggestions also I found this resource in web land , which appears helpful.

[http://www.cae.wisc.edu/site/public/?title=linfstab](http://www.cae.wisc.edu/site/public/?title=linfstab)

I also read a ¨cheat book¨ and got the idea that when you mount something it is not a drive in the ´Windows¨  concept; rather, it is a sub-directory that was helpful because that ment I had to use the cd command.

Here are my solution steps.

1. Re-burn a new live-cd  (my previous one cracked).
2. Boot up in live-cd and open up a terminal.

3. issued the command  ¨sudo fdisk -l¨ to make sure I could see the partition

I read another site and they said to make a new directory called /recovery - I don´t quite know if this was a virtual one of what so I did it, and named it recovery.  I don´t understand if the directory is waiting to exist someplace or what just yet because the second command made use of it some how:

4.   sudo mkdir /recovery

5.   then I mounted the partition using the following command

     sudo mount -t ext3  -o rw  /dev/hda3  /recovery

6. Then I CHANGED DIRECTORY

cd  /recovery   

then issued an listing command

ls -l

cd /etc

pwd    (print working directory)

ls -l

and I was in the subdirectory where my fstab file was.  It took me another couple of tries and a lot of reboots because I kept on getting the following error when I tired to rename/copy the files with the sudo mv command:

sudo: uid 999 does not exist in the passwd file!

I stumbled around on the web (on the XP side of my machine) and learned that I needed to (for some reason) give root a password or something like that.  So I issued the following command:

7.   sudo passwd root  

     and answered the prompts

then I was able to rename the current fstab to fstab.bad with the mv command

8. sudo mv  fstab  fstab.bad

I then renamed my good, old version of the file to fstab.

9. sudo mv fstab.good  fstab

After that command  was done there was nothing I could do more than take the CD out of the drive, turn the machine off and reboot and cross my fingers.....and to my surprise I am back to the state I was in before I got fancy......I will wait a couple of days before attempting to get that partition the way I want it.....I have to lick my wounds for a couple of days.

I hope I remember this the next time I mess up my fstab.

Good day and good luck.

---

### Post by H.E. Pennypacker on 2007-06-20
> I think I picked the wrong partition because when I rebooted my Ubuntu boot partition complained that it was read-only. 

Please reproduce the exact error that shows up on the screen, not a rephrasing, but the exact error, word for word, including all punctuation.  Also, please tell us exactly when you see the error, before what, and after what.

Please remember to reproduce the exact error.

---

