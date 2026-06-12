---
title: "Removing files/directory?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-09-12
I have been trying (unsuccessfully) to install gnomad2 and get it towork with my MP3 player.  Now, I just want to get it all off my system and be done with it.  I have already attempted a removal, and here is what I have...

gary@Faith:~/gnomad_install$ sudo dpkg -r gnomad2
(Reading database ... 89113 files and directories currently installed.)
Removing gnomad2 ...
dpkg - warning: while removing gnomad2, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing gnomad2, directory `/usr/local' not empty so not removed.
gary@Faith:~/gnomad_install$ cd /usr/local
gary@Faith:/usr/local$ ls
games  include  lib  man  sbin  share  src

To me, this is saying that the /usr/local/ directory needs to be removed; however there are several sub directories in it so it won't remove them.  I have no idea what these directories contain, so I don't know if I SHOULD remove them.  I'd appreciate a little advice.  Thanks

---

### Post by taurus on 2006-09-12
See if you have gnomad2 in /usr/local/share!!!  Maybe that's the one you have to remove by hand...

```
ls -la /usr/local/share
```

---

### Post by Guns90 on 2006-09-12
gary@Faith:/usr/local$ ls -la /usr/local/share
total 24
drwxr-xr-x 6 root root  4096 2006-09-12 10:01 .
drwxr-xr-x 8 root root  4096 2006-09-12 10:01 ..
drwxrwsr-x 2 root staff 4096 2006-05-30 20:56 fonts
drwxr-xr-x 3 root root  4096 2006-05-30 20:55 games
drwxrwsr-x 7 root staff 4096 2006-05-30 20:56 sgml
drwxrwsr-x 6 root staff 4096 2006-05-30 20:56 xml
gary@Faith:/usr/local$

This doesn't tell me anything.

---

### Post by taurus on 2006-09-12
> **Guns90 said:**
> gary@Faith:/usr/local$ ls -la /usr/local/share
total 24
drwxr-xr-x 6 root root  4096 2006-09-12 10:01 .
drwxr-xr-x 8 root root  4096 2006-09-12 10:01 ..
drwxrwsr-x 2 root staff 4096 2006-05-30 20:56 fonts
drwxr-xr-x 3 root root  4096 2006-05-30 20:55 games
drwxrwsr-x 7 root staff 4096 2006-05-30 20:56 sgml
drwxrwsr-x 6 root staff 4096 2006-05-30 20:56 xml
gary@Faith:/usr/local$

This doesn't tell me anything.
Then don't worry about it!!!  Next time, try to install package for Ubuntu, not Debian because not all Debian packages would work in Ubuntu.  Otherwise, find the source and build it yourself.

---

### Post by Guns90 on 2006-09-12
:) I did try to install it from source.  That's what got me in trouble in the first place.  Thanks for the advice though.

Oh, if I might, I also have two folders each of gnomad2, libnjb, and libmtp in my trash file that when I try to empty trash it says "/home/gary/...K/AUTHORS" cannot be deleted because you do not have permissions to modify its parent folder.  How would I get rid of these, please?

---

### Post by taurus on 2006-09-12
```
sudo rm -rf <directory>
```

---

### Post by Guns90 on 2006-09-12
taurus, I'll take your word for it that the command you gave me will work, providing I type in the right directory.  I know I look like an idiot for asking this, but I can't find the trash directory.  It has to be in my /home/gary/ directory, doesn't it?

---

### Post by Guns90 on 2006-09-12
taurus, I'll take your word for it that the command you gave me will work, providing I type in the right directory and path.  I know I look like an idiot for asking this, but I can't find the trash directory.  It has to be in my /home/gary/ directory, doesn't it?

---

### Post by taurus on 2006-09-12
Are you talking about ~/.Trash--/home/gary/.Trash???

---

### Post by Guns90 on 2006-09-12
Sorry about the time; I had a small emergency.  

I'm referring to the 'trash' window that comes up when you click on the little trash can in the lower right corner.  I said that I assumed it was in my /home/gary...directory because I'm the only user who can see them in the 'Trash File-Browser' window.

---

### Post by steve.horsley on 2006-09-12
Don't worry about it not being able to delete /usr/share. It tried, but failed because the directory isn't empty. If it had succeeded, your computer would need reinstalling. It's a "Last one out please turn off the lights" kind of thing. Except gnomad2 isn't last one out so the directory isn't empty. All is as it should be.

I believe that the trash goes in ~/.Trash (folder .Trash in your home directory). But files and folders beginning with a dot are normally hidden. You can see it with "ls -a" where -a means all, or you can use Ctrl-H in nautilus which turns on showing hidden files. Perhaps the easiest thing is to delete the entire trash directory with this command:
**sudo rm -rf ~/.Trash**
assuming there isn't anything vital in there of course.

---

### Post by Guns90 on 2006-09-13
That did the trick.  Thank you very much steve.horsley.

---

