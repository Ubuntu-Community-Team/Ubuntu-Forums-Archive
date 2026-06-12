---
title: "What in the world was that ?!"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-08
Hi folks!

I started off with Ubuntu 6.06 (with Gnome default DE). Here's what happend: two days ago I installed KDE for I was very curious; I like it very much, I even set it up to be my default DM. Yesterday I kind of messed around a little, I downloaded 4 or 5 themes for KDE (I have release 3.5.2), I didn't like them, I made my own theme, and then I installed Wine (according to [this](http://www.psychocats.net/ubuntu/wine) guide), I configured it and I tried to install a Windows program. That didn't work (it was installed but I couldn't run it). But that's not the problem. The problem is that this morning when I started my computer, it gave me a strange error message and I can't figure out why; here's what it said:
```
/dev/hdc6 UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i.e., without -a or -p options)
* An automatic file system check of the root filesystem failed
* A manual fsck can be performed in maintenance mode. Please note that the root filesystem is currently mounted read-only
* The fsck should only be performed while the root filesystem is mounted read-only. However, the command to remount it read-write is # mount -u -o remount,rw /
* In order to exit from this maintenance shell, press CONTROL-D and the system will REBOOT.
bash : groups : command not found
bash : lesspipe : command not found
bash : dircolors : command not found

```

Alright I did what it told me, I did fsck, it encountered a lot of I/O errors in certain inodes, it asked me if it should ignore the error (with a default <y>), I said yes, then it asked me if it should rewrite to that block (also with a default <y>), I said yes... and then I rebooted and everything is back to normal again. Just in case, I had a .tar.bz2 backup of my system, but fortunately I didn't have to use it.

In the maintenace shell I tried to run Midnight Commander, I just installed it yesterday, but when I typed mc and hit enter, it told me that "command not found". I wonder why, since now I still have it and it's still working.

I can't figure out what went wrong and if and what I did yesterday could determine such a behaviour. I hope you can point me what the problem is.

Thanks in advance, 

LLRNR

---

### Post by LLRNR on 2006-11-08
Come on now, really, I'm sorry for bumbing this thread, but... err... I'm very curious about this issue, I'd like to know if :

a) some of you had the same problem ;
b) is it _normal_ ?
c) how can such things be avoided ?

Again, sorry for bumping this up and thanks in advance,

LLRNR

---

### Post by bsussman on 2006-11-08
No it is not normal and yes - many folks see these problems.

Before even reading the rest of this post, you should consider verifying your backups - the ones not on this disk.

It is very likely not directly related your changes.  But you are using more disk space so it might have been the indirect cause.

It lit is usually the distant warning of a marginal disk.

Meaning that it is going to get worse and you should begin to take actions to safeguard your data and plan to replace your disk.

If you need that last sentence in boldface, I will be happy to oblige :)

1.  You should generally let it repair the errors unless you have a specific reason to not do so.  At least it did rewrite the block.  I do not know the logic behind the ignore=yes default.  Maybe it has to do with whether it continues verifying.  You did the best that can be done in that situation :)

2.  You should use tune2fs to reduce the time/cycles tween checks.  I recommend  checking at every boot for at least the next 3 days.  If you get absolutely no errors, you can consider waiting to replace, but I wouldn't.


the ext2/3 filesystem is very good - it has many internal safeties.  But I always consider them to be useful for temporary survival whilst arranging a repair/replacement rather than to be used to continue using a marginal disk.

---

### Post by goatflyer on 2006-11-08
Your questions:
a) some of you had the same problem ;
b) is it _normal_ ?
c) how can such things be avoided ?

a) Not me.

b) No. this is not normal.  Something about your installation is deteriorating.  (Backup what you can asap!) What kind of device is /dev/hdc ?   By ignoring errors in fsck what you are doing is basically sweeping the problem(s) under the rug.  But some files went missing as your other errors show.

c) I see two possibilities:  the worse one is it could be your hard drive is dying.  The best one is that you (manually) messed up your installation making it inconsistent. Whichever one it was, some of your files seem to be already lost.

After backing up what you can, you might try to re-format the drive, reinstall your system and hope for the best, or else (if the drive IS dying) replace the drive.

---

### Post by LLRNR on 2006-11-08
Thanks, bsussman! Although your prediction doesn't sound too optimistical... this means that I have a faulty HDD, right (on which I have the Ubuntu's filesystem on) ?

Regarding repairing the errors encountered, yes, when I ran fsck (which I didn't know anything about until this morning), it only asked me if it should ignore the error (yes being default) and then if it should try to rewrite to that block (also with yes as default). I did that and then it booted normally.

There is one more thing though: before not-wanting-to-boot, I remember it saying something about the filesystem (?) not being checked during the last 30 boots, and forcing the check now (and then the error message I quoted in the first post appeared).

Well... I looked through the tune2fs manual pages, and there sure are a lot of options. I'm not quite sure which of these to use. (I don't have any previous Linux experience) Would you be kind enough to suggest me which of these I ought to use ?

Oh and one more thing: you mean that I should have my .tar.bz2 backup on another physical HDD (a _safer_ one), right ?

Thank you very much,

LLRNR

---

### Post by LLRNR on 2006-11-08
Goatflyer, my /dev/hdc/ is actually the HDD I installed Ubuntu upon. It's a 80 GB Maxtor which caused me problems before - I once had to reformat it, since it couldn't recognize any of my files, back in my MS days, when my system simply hanged when trying to acces it from My Computer or from the Command Prompt. 

It is not the primary HDD, and it has 2 partitions: one for general-use files: books, documentation and music, and the second partition is ext3 - the filesystem for Ubuntu. 

I really don't think screwing up the installation myself, I'm very precaucious and before I try something I make back-ups of the files to be modified (for instance that's what I did when attempting to reconfigure xserver-xorg). I also have a backup of the entire filesystem, but it's still in /.

Another thing that makes me believe that I didn't screw up the installation myself, making it inconsistent, is that after I ran fsck, it booted up normally and all the changes (visible changes at least :D) that I applied to my system last night are... still there. 

Alright guys, since both of you actually tell me the same thing and since I had problems before with this lousy HDD, I think that's the problem... :( If I reformat it, I can do it with the installation CD, right ? I mean it still has to be ext3, I suppose...

Thanks,

LLRNR

---

### Post by bsussman on 2006-11-08
> **LLRNR said:**
> Thanks, bsussman! Although your prediction doesn't sound too optimistical... this means that I have a faulty HDD, right (on which I have the Ubuntu's filesystem on) ?

Probably but not absolutely definitely.  So I do not like gambling on my data and hard work setting up my system.  And my wife's teaching, design and other documents?  Risk is out of the question.
> 
Regarding repairing the errors encountered, yes, when I ran fsck (which I didn't know anything about until this morning), it only asked me if it should ignore the error (yes being default) and then if it should try to rewrite to that block (also with yes as default). I did that and then it booted normally.

There is one more thing though: before not-wanting-to-boot, I remember it saying something about the filesystem (?) not being checked during the last 30 boots, and forcing the check now (and then the error message I quoted in the first post appeared).
Yes - that is normal and not a really terrible default for normal circumstances although I always shorten it. And this is not a normal circumstance.
> 
Well... I looked through the tune2fs manual pages, and there sure are a lot of options. I'm not quite sure which of these to use. (I don't have any previous Linux experience) Would you be kind enough to suggest me which of these I ought to use ?

Yes - it is a complex utility.
```
tune2fs -c 1
```should do it for now, and I like 
```
tune2fs -c 7 -i 7
```for normal (that's 7 days or 7 mounts).  It is a small price to pay for knowing linux likes the state of my disk.

Please make sure you understand what this does.  Trust nobody with your system!
> 
Oh and one more thing: you mean that I should have my .tar.bz2 backup on another physical HDD (a _safer_ one), right ?
Yes - exactly.  I have never seen a problem on one disk actually take out another but I have seen separate partitions on the same disk be affected by a failure, for obvious reasons.

---

### Post by LLRNR on 2006-11-08
Alright, bsussman, thanks for the "syntax highlight" lol ! I'll try it as soon as I get home, I'm at school right now (oups now I see I really have to go to the course I'm a little late even).

Great advice, you're right, it's sure worth it in order to know Linux is safe and well...

LLRNR

---

### Post by bsussman on 2006-11-08
:)

---

