---
title: "Unable to mount partitions (yeah, stupid n00b here!)"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by asfaq on 2007-04-24
Hi folks,

Having installed Ubuntu LTS (it was breeze, i must admit) I am unable to mount 2 of my windows FAT32 partitions. I get these erros when i try to do so..

error: device /dev/hdb1 is not removable
error: could not execute pmount

and...

error: device /dev/hdb5 is not removable
error: could not execute pmount

here are the contents of my etc/fstab file
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

tried modifying the etc/fstab file to mount the drives automatically on start-up, but it says that i dont have permissions as i am not the 'owner'. AFAIK, i am the only user profile on the OS.

So, could someone be kind enough to help me out here please? ideally i'd like my drives to mount automatically on start-up.

---

### Post by marko_4454 on 2007-04-24
did you try doing the commands in super user mode?
Maybe something like

```
sudo mount /dev/hdb5 <mountpoint>
```

replace <mountpoint> with the actual folder where you want to mount it on.

IF that works, then just post back and editing your fstab will be much easier. I dont have much experience with Windows drives in linux, so just post back.
Remember that initially FAT32 is only supported as Read-only, you need to add extra software for read/write support. This is done fairly easy.

---

### Post by asfaq on 2007-04-24
> **marko_4454 said:**
> did you try doing the commands in super user mode?
Maybe something like

```
sudo mount /dev/hdb5 <mountpoint>
```

replace <mountpoint> with the actual folder where you want to mount it on.

erm.. no. As an example where should I be mounting this drive to? Does this mean that it will copy all the contents of that drive to the designated folder?

> **marko_4454 said:**
> Remember that initially FAT32 is only supported as Read-only, you need to add extra software for read/write support.


ah! thanks for the tip.. *goes around to repositories for help*

---

### Post by asfaq on 2007-04-24
another update..

asfaq@Asfaq:~$ sudo mount /dev/hdb5 /home/asfaq/desktop
Password:
mount: mount point /home/asfaq/desktop does not exist

I tried mounting the drive to the desktop as i wanted to see it there.. but it says that the folder does not exist.. hmm...

---

### Post by marko_4454 on 2007-04-24
Ok you should go to this link:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
That should give you an idea of what I am talking about.
A superuser (root) is like an Administrator in Windows....it can do anything. 
where you mount your hard drive is where you access it pretty much, instead of having the /dev/hdb you have a more easy path, like /media/Windows or something like that. To do that, you can just type:
```
sudo mkdir /media/Windows
```
which will make a directory called "Windows" where you can mount your hard drive.
Anyways, everything should be explained in the psychocats website. That is an excellent newbie guide. Try and read as much as possible :)

---

### Post by marko_4454 on 2007-04-24
Linux is case sensitive. 
Desktop != desktop

so type:
```
sudo mount /dev/hdb5 /home/asfaq/Desktop
```

I am not sure if you want to mount a hard drive in Desktop though.

---

### Post by asfaq on 2007-04-24
w00t !! thanks man! looks like a promising tutorial.. will update you on further developments :)

---

### Post by AlexenderReez on 2007-04-24
you need to create a folder.....that is because you try to mount to a place that doesn't exist....

---

### Post by asfaq on 2007-04-24
> **marko_4454 said:**
> Linux is case sensitive. 
Desktop != desktop

so type:
```
sudo mount /dev/hdb5 /home/asfaq/Desktop
```

I am not sure if you want to mount a hard drive in Desktop though.

Case sensitive.. oh.. so u say its a bad idea to mount the HD on the desktop, come to think of it, i havent seen any tutorial that advises you to do so, so i guess i'll stick to your suggestions..

:)

---

### Post by AlexenderReez on 2007-04-24
> [http://news.softpedia.com/news/Installing-NTFS-Write-Support-on-Fedora-Ubuntu-41390.shtml](http://news.softpedia.com/news/Installing-NTFS-Write-Support-on-Fedora-Ubuntu-41390.shtml)

learn to understand....

---

### Post by asfaq on 2007-04-24
> **reez0105 said:**
> learn to understand....

but tht article is for NTFS partitions.. i have FAT32.. am guessing the commands are not the same then.. or are they?

---

### Post by asfaq on 2007-04-24
another update..

I followed the instructions in the tutorial and got the windows 'd:/' drive to mount.. it now shows up under '/windows'. Under Computer though, i get this error:
> mount: according to mtab, /dev/hdb1 is already mounted on /windows
mount failed
I'd rather have the partion mounted under Computer. Any suggestions on how to do the same? do i have to just go: 'sudo mount /dev/hdb5 /Computer' and edit the etc/fstab file accordingly?

Also, the other partion, am guessing that was 'hdb5', is missing now. I had wanted both of them to 'load' or 'appear' inside the /windows directory. Is it because of this that i dont get to see the other partition too?

---

### Post by marko_4454 on 2007-04-24
OK, i am kind of confused of what you have as of now....but since you mounted hdb1 you have to unmount it to be able to mount it again:
```
sudo umount /dev/hdb1
```

Also, anything that you mount will appear in "Computer", so you cannot mount anything to "computer". I recommend mounting HD's in the /media/ folder. So my suggestion is this:
1) make directory called Windows
```
sudo mkdir /media/Windows
```
2) Mount your HD
```
sudo mount /dev/hdb# /media/Windows
```

*change the # for the partition number (possibly 1). If it does mount and you wanna try again for some reason remember you MUST unmount it before you can mount another partition number by using the command above*

---

### Post by marko_4454 on 2007-04-24
> **asfaq said:**
> but tht article is for NTFS partitions.. i have FAT32.. am guessing the commands are not the same then.. or are they?

They are not the same and I screwed up thinking that you had NTFS...Linux actually supports FAT32. I just did a simple Google search and I came up with this:

[http://forums.techguy.org/unix-linux/283474-read-write-fat.html](http://forums.techguy.org/unix-linux/283474-read-write-fat.html)

So do not worry about any software anymore :) It does support!

---

### Post by asfaq on 2007-04-24
> **marko_4454 said:**
> They are not the same and I screwed up thinking that you had NTFS...Linux actually supports FAT32. I just did a simple Google search and I came up with this:

[http://forums.techguy.org/unix-linux/283474-read-write-fat.html](http://forums.techguy.org/unix-linux/283474-read-write-fat.html)

So do not worry about any software anymore :) It does support!

Oh cool !! Btw (just to inject some humor)..

[QUOTE=the website you linked to,]Be Right Back! 

The Tech Support Guy server is currently doing our daily backup. It should be back online in about 25 minutes, so please check back then! 

In the future, you can also check [http://status.techguy.org/](http://status.techguy.org/) for scheduled downtime. 

Thanks for your patience!![/QUOTE]

Just my lucky day today eh? ;)

Following your steps right now.. will edit this post as soon as i reboot and find the results..

---

### Post by marko_4454 on 2007-04-24
> **asfaq said:**
> Oh cool !! Btw (just to inject some humor)..



Just my lucky day today eh? ;)

Following your steps right now.. will edit this post as soon as i reboot and find the results..

Wow that is really bad luck...but thats why we have Google Cache :)
[http://72.14.253.104/search?q=cache:cQow-d75BjgJ:forums.techguy.org/unix-linux/283474-read-write-fat.html+FAT32+linux+support&hl=en&ct=clnk&cd=10&gl=us&client=firefox-a](http://72.14.253.104/search?q=cache:cQow-d75BjgJ:forums.techguy.org/unix-linux/283474-read-write-fat.html+FAT32+linux+support&hl=en&ct=clnk&cd=10&gl=us&client=firefox-a)

---

### Post by asfaq on 2007-04-24
Your instructions were spot on.. it worked !! :) Thanks a bunch.. I learnt a lot today, quite a few terminal commands are like DOS and that all future drives have to be mounted under '/media', only then do they show up under 'Computer'.

Thanks once again for the google cache link, its so funny that once you start recieving help, you completely forget to look at the other possibilites available. I should have checked the cache link.. my bad :D

U have a great day now! 

Asfaq Tapia.

PS: Thanks to everyone else who helped :)

---

### Post by marko_4454 on 2007-04-24
wow, even I am impressed...I didnt put that much care and it still worked. Awesome!
I am off to sleep now since its 1AM here in California, USA. 
I am glad that I was able to help. you should still read about commands and all that linux stuff...its pretty easy if you have some, even the smallest, DOS (terminal) experience. 
In order to mount it automatically, just add an entry to your fstab file using some scheme that you can find somewhere in another thread. It shouldnt be hard, just search "fstab fat32" or something like that. 
If that doesnt work...just google it.

---

### Post by asfaq on 2007-04-24
oh. heh.. i was making all the changes in etc/fstab all along.. so yeah, it should mount automatically everytime.. thnx again.

Am located on the other side of the planet in India :)

Nighty night!

---

