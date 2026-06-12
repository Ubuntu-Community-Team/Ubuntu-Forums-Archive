---
title: "Pre-install HDD Cleanup"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Cyberbayne on 2007-01-17
I've decided to take the plunge, but would prefer to learn on the shallow end of the pool, so I'm preparing to install Ubuntu on my slave HDD while keeping my WINXP intact on the master. I'm down to a few applications that I need to transfer from the slave to the master, and was hoping someone could recommend a (preferably free) transfer utility that would move the applications and update the registry as part of the transfer. Any suggestions?

---

### Post by oilchangeguy on 2007-01-17
not sure if this will work, but give it a try. open my computer, open the c drive and your other drive so you can view the contents and the click on the file in the slave drive and drag it to the master drive. this should work for document files, don't know about program files.

---

### Post by Cyberbayne on 2007-01-17
Thanks for the feedback.

The method you describe will work fine for data files or any applications that don't update the registry upon installation. As a general guideline, if you see an application listed in the Add/Remove Programs window, you cannot just move it somewhere else and expect it to work. Stand alone apps that make no changes to your registry can be moved anytime.

If I can't find a transfer utility that updates the moves I make in the registry, I'll need to uninstall them and reinstall them in the new location, then manually move and (hopefully) integrate the user/data files in the new installation directory.

---

### Post by oilchangeguy on 2007-01-17
ok, if that is the case then, you should be able to drag the program files to the c drive. because unless you have an os installed on your slave drive the only place the reg. is located is on the c drive, so therefore no changes are being made (i think) the  only thing you may have to change is the path to the program. if you installed it on another drive rather than the default c: path. the path will read something like this F:/program files/adobe photoshop/.  change the drive letter to c: and it should be ok.

---

### Post by bodhi.zazen on 2007-01-17
Well, how much room (free space) do you have on the second HD ?

You may be able to resize the partition and forgo all that transfer stuff :p

for Ubuntu you can squeeze by with 5 Gb for your root partition and max 1 Gb for swap ....

To resize, first defragment the drive then follow directions here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

go ahead and install grub into your MBR ;)

You may find after a while you boot to windows less and less ...

---

### Post by bodhi.zazen on 2007-01-17
> **oilchangeguy said:**
> ok, if that is the case then, you should be able to drag the program files to the c drive. because unless you have an os installed to your slave drive the only place the reg. is located is on the c drive, so therefore no changes are being made (i think) the  only thing you may have to change is the path to the program. if you installed it on another drive rather than the default c: path. the path will read something like this F:/program files/adobe photoshop/.  change the drive letter to c: and it should be ok.

Unfortunately windows does not work that way with most programs ....

At least it did not 5 years ago when I had a problem. It was in the days of small HD and I ran out of room on C:

I installed a new HD and some programs simply would no go to the new drive, insisted on C:

Others had to be re-installed.

Some could be simply moved as you suggest, but they were in the minority.

---

### Post by Cyberbayne on 2007-01-17
> **bodhi.zazen said:**
> Well, how much room (free space) do you have on the second HD ?
You may be able to resize the partition and forgo all that transfer stuff :p
for Ubuntu you can squeeze by with 5 Gb for your root partition and max 1 Gb for swap ....
To resize, first defragment the drive then follow directions here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
go ahead and install grub into your MBR ;)
You may find after a while you boot to windows less and less ...

Well, that's part of the problem. Its a single 30GB FAT32 HDD that I turned into 2 virtual drives, the second of which I now want to use for the Ubuntu. But the Ubuntu installer sees it as the second partition of the slave and for some reason won't let me re-partition it. So I figured I'd just clear the drive, reformat, and dedicate the full 30GB to the new installation. I'm down to a half dozen "registered" apps and was just looking for a shortcut...

---

### Post by dbd on 2007-01-17
If you just copy the programs to C and then clear the drive as your say, but also make a small windows partition. Then you can just copy all your programs back from C to the new windows partition and they should work fine.

---

### Post by Cyberbayne on 2007-01-17
> **dbd said:**
> If you just copy the programs to C and then clear the drive as your say, but also make a small windows partition. Then you can just copy all your programs back from C to the new windows partition and they should work fine.

OK, that's just too simple. :wink: 
Thanks... *looking for a "humble" smilie*

---

### Post by Cyberbayne on 2007-01-18
Just wanted to answer my initial question for any who may come here looking for the same help. I did find an application that ran like a race horse. It has a clever name, too:

"Application Mover" [http://www.funduc.com/app_mover.htm](http://www.funduc.com/app_mover.htm) 

The trial period is for ten free moves.

Thanks again to those who offerred advice.

edit: Ubuntu is installed :) 
Now I need to figure out how to connect to my wireless network, so I'm off to find that thread.

---

### Post by Tux Aubrey on 2007-01-18
I know the OP has been answered, but I have a supplementary question (Mr Speaker) and this thread has the right title.:) 

bodhi.zazen said:

> To resize, first defragment the drive then follow directions here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

No argument.  But I rarely see the bit about defragging the Windows install in the documentation or posts here.  Is it necessary?

When I first installed Ubuntu all those months ago, I was really uptight about squeezing Windows into the smallest possible space - I deleted the Windows swap file thingy (can't even remember what its called now! - Virtual Memory?) and then I used an aggressive 3rd party defragger to get everything in order.  I think I ran it several times.  I recreated the swap file, left myself a few gigs and then installed Ubuntu on the rest of the drive.  

Now this paranoia about the defrag wasn't my idea - I read it on O'Reilly [here]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") - an article that really does go on and on about the need to defrag.  I know its about an older version of Ubuntu (and the second bit about the rescue disk is, I now realise, complete overkill.)

So, is this all really necessary?

I'd like to know so that when I am helping people install Ubuntu, I can confidently defrag away or not.

(BTW.  My precious Windows partition is now full of dust and cobwebs as I think I've now booted to it about three times since I installed dapper.  I did it again the other night and I felt dirty)

---

### Post by Cyberbayne on 2007-01-18
I think it makes good sense to defrag if you are going to have both OSs on the same HDD, especially if the partition you want to create was first used by windows (as opposed to using a new HDD for fresh mounts of both). If you are going to mount the *nix on its own drive, re-formatting the drive should be sufficient.

---

### Post by bodhi.zazen on 2007-01-18
> **Tux Aubrey said:**
> I know the OP has been answered, but I have a supplementary question (Mr Speaker) and this thread has the right title.:) 

bodhi.zazen said:



No argument.  But I rarely see the bit about defragging the Windows install in the documentation or posts here.  Is it necessary?

Yes, you should defragment and backup before you resize or reformat your partitions. It is not "necessary", but it is not uncommon for people to have problems with resizing if they do not defragment.
  
> When I first installed Ubuntu all those months ago, I was really uptight about squeezing Windows into the smallest possible space - I deleted the Windows swap file thingy (can't even remember what its called now! - Virtual Memory?) and then I used an aggressive 3rd party defragger to get everything in order.  I think I ran it several times.  I recreated the swap file, left myself a few gigs and then installed Ubuntu on the rest of the drive.  

Now this paranoia about the defrag wasn't my idea - I read it on O'Reilly [here]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html") - an article that really does go on and on about the need to defrag.  I know its about an older version of Ubuntu (and the second bit about the rescue disk is, I now realise, complete overkill.)

So, is this all really necessary?

No, it is better to bite the bullet and just install over the top of windows :p

Most, however, will dual boot for some time as they transition.

Unless you need to squeeze space out of a HD (windows) I do not think you need to do more then 1 cycle of defragmentation before you install Ubuntu.

Minimal size for Ubuntu is 5 Gb, but if you stay with it you will certainly want to increase that to 15-20 Gb.

> I'd like to know so that when I am helping people install Ubuntu, I can confidently defrag away or not.

(BTW.  My precious Windows partition is now full of dust and cobwebs as I think I've now booted to it about three times since I installed dapper.  I did it again the other night and I felt dirty)

Well I hope that information helps you (and others).

It is helpful to advise:

Defragment - Dont worry if there is some fragmentation remaining, this is the nature of Windows. The goal is to minimize fragmentation before you resize.

Backup - Although data loss is rare, keep in mind wiping the windows partition may be only a few mouse clicks away and you may well be helping someone who has never partitioned, formatted, or installed previously ...

Ubuntu will partition the free space you make automatically. I usually advise some kind of data partition, either /home or a FAT partition. If you want to advise ext3 for a data partition give a link to the windows driver:

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Let the liberation begin :twisted:

---

### Post by Tux Aubrey on 2007-01-18
Thanks b.z

Good info, as always.  Installing Ubuntu is a good opportunity for people to spring clean their Windows installation, so I will continue to recommend a defrag (and backup) and a considered partitioning plan for dual booters.

---

