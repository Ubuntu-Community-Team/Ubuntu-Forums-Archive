---
title: "Please help me mount this without killing XP"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-08
I have been persevering with this issue for the whole week or so that i have been using unbunto.

I have read the guide and tried to follow it but here i am again..

XP on 40g main hd and ubunto on small 3.2g slave drive

Xp hd has 2g of unallocated space on the end of it(nothing to do with xp)

I have really tried to do this but fail everytime.

I have used gpart to format that little itty bitty space to ext3 so as to give ubunto a bit more seeing as its on such a small hd in the first place

Then i have followed the tutorial to mount this space and to put the appropriate info into the fstab but must be making a mess of it as XP has BSOD when trying to boot to it.

Prviously i was doing it even more wrong but could always go back and undo what i`d done and boot xp to last good config and it would work again BUT this time i want to sort it once and for all.

Anyway...i followed the tutorial and seemed to brake down at giving the right permissions as i copied and pasted the codes up till then ok(changing MY drive names etc) but the last part did`nt seem to happen as it was supposed to.
This was how my fstab ended up

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2 /storage ext3 defaults 0 0


I know ive made a mess BUT IM TRYING.......HELP

Ps when i first looked the small 2g space was showing in my computer along with hda(xp) and filesystem(hdb) ...NOW ive rebooted after trying xp it`s no longer showing up

Sorry about the edits......It does show up in discs??????????IM LOST

---

### Post by xpod on 2006-08-08
dad@dad-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4673    37535584    c  W95 FAT32 (LBA)
/dev/hda2            4674        4865     1542240   83  Linux

Disk /dev/hdb: 3243 MB, 3243663360 bytes
255 heads, 63 sectors/track, 394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         373     2996091   83  Linux
/dev/hdb2             374         394      168682+   5  Extended
/dev/hdb5             374         394      168651   82  Linux swap / Solaris
dad@dad-desktop:~$


Thought this might help too........It looks like it`s there BUT is it in the right place ,it`s surely something simple i need to tell the thing but i just cant figure out what.

I dont mind messing about with most stuff but im weary about doing something even worse to xp than what ive done already.Please help a Scotsman in need...:sad:

Ive also just noticed that the partition has a locked padlock next to it in gparted

---

### Post by xpod on 2006-08-08
They MUST be fed up of ME.......people wanting to UNINSTALL are getting more advice than me who`s trying to ADD linux .....

......ALL TOGETHER "AAAAWWWWWWWWWWWW"

---

### Post by xpod on 2006-08-08
I get it.....Your all helping me to brake completely free of windows by NOT helping me get my xp back........

....WOW.....i never thought i`d have been using an alternitive OS and no XP in such a short space of time....THIS LINUX IS REALLY GOOD EH...LOL:rolleyes:

---

### Post by FizDev on 2006-08-08
Just to be sure... did you defragment your XP Partition before resizing it?

---

### Post by anaconda on 2006-08-08
> 
They MUST be fed up of ME.......people wanting to UNINSTALL are getting more advice than me who`s trying to ADD linux .....


Or your question is too difficult..

Strange. everything seems to be OK in your fstab, exept that your windows partition isn't there, but maybe you didn't even want it there..

have you created the "/storage" -folder, where you try to mount your hda2 ?

Cant understand what broke your XP, but you should try to rescue it with your winXP CD.. Taking backups of any critical data first would be wise..

---

### Post by xpod on 2006-08-08
Hi..thank you for replying...

This 2g of space on the end of the main xp hd was always there as an unallocated space...it had always been like this.

But yes i still did the defragment thing.XP actually only takes up about one third of the 38g partition.

I can access this space by going into "discs" but if i go to "computer" it is not now there but it was initially

The new "storage" file as it`s called has a lost and found file in it(?)

When i previously tried this procedure i dont even think i was actually "mounting" anything but i was able to go back to gparted and cancel what i had done and xp would come back on using "last good config"

Ive obviously got further into the proper procedure this time but havent yet UNDONE anything as i would need to also undo everything i done in the terminal as per the tutorial and i would`nt know how.

I think i can supply any info ok and follow any help....i just want it done correctly.

---

### Post by xpod on 2006-08-08
SORRY....never seen that last post.
Yes i used the terminal as per the tutorial and created a "storage" folder.
it`s there and when i look in it the space in question is in there.

PS....i was only having a bit of fun with the comments above.

Scottish humour...sorry....& cheers

PS...unfortunately im one of the lucky people who got a 1386 directory instead of an xp disk.

Xp`s still there ok....i know if i go back and unmount (i realise it IS mounted now...i think)the little partition and revert it back to UNalloacated space that my xp will come back on like it has on previous attempts at this.


I HOPE...lol

---

### Post by anaconda on 2006-08-08
If you have "lost and found" in your /storage , that means that your 2GB is mounted succesfully. Empty partititon has only "lost and found" in it. (It is like recycle bin in windows.)

If you want to be certain, you could copy some data to /storage, unmount it and verify that the data and "lost and found" are gone.
eg.
unmount /dev/hda2

then mount it back and note that they came back..
mount /dev/hda2

EDIT: sorry didn't read your last post before writing...
but if your windows requires (for some odd reason)  unallocated space at the end of the disk, what can you do? better leave it so that windoze works.

Luckily your windows is on a fat32 partition, so you can just make a folder there, and use it for extra space for ubuntu..

---

### Post by xpod on 2006-08-08
It`s definetly there but theres something about the whole thing that xp aint agreeing to.
I could go and do the unmounting thing like you say to confirm it does exist but that still would`nt tell us why it`s affecting xp.......OTHER than it works when i dont play around with it.

IF i do have to revert what ive done would i need to change the fstab back as well to the previous one.

Was hoping i could get round that this time:confused:..the unmount that is

AND I MISSED THAT EDIT...lol

So your saying i can just cancel whats gone before and then i take it the xp would need mounting(i believe it is`nt presently)Then i could create this folder you mention...

We dont store anything on any of our 3 pc`s their all just for teaching the kids ....and moi.We only got our first(m.e)a few months ago and ive somehow come into bit`s and pieces of other`s and have managed to build three working pc`s...xp/ub  and kbunto as well as the m.e(it`s next)

All im concerned about is when the 700mb left of space on here runs out with all the regular updates and the odd thing i get from add/remove,synaptic and automatix etc.

Change of direction then it is.......watch this space

---

### Post by xpod on 2006-08-08
When i tried the unmount command i got the first message so i then (out of curiosity)tried the second and got this lot

dad@dad-desktop:~$ unmount /dev/hda2
bash: unmount: command not found
dad@dad-desktop:~$ mount /dev/hda2
mount: according to mtab, /dev/hda2 is already mounted on /storage
mount failed
dad@dad-desktop:~$

---

### Post by xpod on 2006-08-08
Well,as expected xp came back as soon as i deleted the little partition and reverted it back to UNallocated.

I also unmounted it and again i seen it as a 2g filesystem in "computer" when i rebooted but again it`s gone since.

Do i just delete that copy of the fstab now and will the backup be automatically reused.Sorry but i dont want to make an even bigger mess.

I think i`ll then be able to mount my xp okay retracing my steps but replacing the little space with the xp one.

could you also tell me what exactly ..if anything i need to do for this(ubunto) to automatically use this file i create in xp if and when it needs it

---

### Post by catlett on 2006-08-08
You are having a strange error with xp and that partition. Instead of fighting XP, why not go along with it. Fat32 is the former filesystem of choice for  windows' and linux can read and write to it.
Why don't you try and make it a fat32 partition. Maybe that won't bother xp?

---

### Post by xpod on 2006-08-08
Hey....Hi again....AYE....still here

Well ive come a bit further since then (not much..lol)...

I ended up unmounting and reverting back to unallocated and xp is ok BUT..

..That fstab is still now listing the space and im not to sure if it NEEDS to have the old backup put back(how?)

I went into xp and created an Ubunto file and i managed to get it mounted but it dissappears upon reboot and i have to go back into "discs" and put a path back in(media/windows)and enable it again.The whole thing that is

I Think i now mabey need to put THAT in the fstab(am i wrong?)

Lastly...will ubunto USE the folder OR any part of the free 22g of space that i have in there if and when it needs it??
I have 700mb of the space left on this little slave with ubunto so am at some point going to need to use more space.

I imagine it would need mounted permanantly for that?CHEERS AGAIN BTW

Ps...xp is fat32 already........as well as tempromental

---

### Post by catlett on 2006-08-08
I wasn't talking about XP, I meant the 2g of unallocated. Make it fat32 instead of ext 3.
Or you can give it to windows.
If XP is fat32, then all of that partition is available to ubuntu. You could make a folder in XP called Ubuntu and use that folder for ubuntu.
What is your /etx/fstab right now? The one you posted doesn't have windows mounted. If you mount windows, you can use the free space there.
If you want to mount windows, post your /etc/ftsab and the oputput of sudo fdisk -l. Post the returns of this
```
cat /etc/fstab
```
```
sudo fdisk -l
```

---

### Post by xpod on 2006-08-08
Thank you

dad@dad-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2 /storage ext3 defaults 0 0
dad@dad-desktop:~$

AND

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4673    37535584    c  W95 FAT32 (LBA)

Disk /dev/hdb: 3243 MB, 3243663360 bytes
255 heads, 63 sectors/track, 394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         373     2996091   83  Linux
/dev/hdb2             374         394      168682+   5  Extended
/dev/hdb5             374         394      168651   82  Linux swap / Solaris
dad@dad-desktop:~$


Ive already created the file in xp and i can access the whole 38g when i go to discs and specify a path(/media/windows)then enable it.

But im not quite doing it right as per as it dissappears on reboot

PS remember ive unmounted that little 2g and changed it back so it dosent show uo in that list now...it was /dev/hda2

---

### Post by xpod on 2006-08-08
Catlett my friend .....im afraid i have to call it a night.

Thank you for your time and i will be on any advice first thing in the morning.

zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz:arrow: goodnight for now

Thank you one and all

---

### Post by catlett on 2006-08-08
Good morning Xpod,

Or as my ancestors ,who were once your kinsman, say "top O' the morning to ye'"
This is what to do. First we'll issue a command and then we'll edit your /etc/fstab
This is going to put windows in the media folder as a folder called windows.     
The first command is going to make the folder for windows. The next one will oipen up your /etc/fstab
sudo mkdir /media/windows
sudo gedit /etc/fstab

You can edit the list to make it look like this one or you can erase that list and copy/paste this list in. Make sure to save the file after your finished.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc                  proc     defaults                   0 0
/dev/hdb1    /                        ext3     defaults,errors=remount-ro 0 1
/dev/hdb5    none                  swap     sw                         0 0
/dev/hdd     /media/cdrom0    udf,iso9660 user,noauto             0 0
/dev/hda1   /media/windows   vfat     iocharset=utf8,umask=0000   0 0
```

That /etc/fstab remove /dev/hda2 which doesn't exist any more. It also mounts windows in /media/folder. If the feature is enabled in nautilus, there will be an icon on your desktop the next time you boot your computer.
If you don't get an icon go to the top panel and enter into Places<Computer<Filesystem<Media and there will be a windows folder. If the mount was successful then there will be files in it. If it didn't mount it will be empty. Make sure to restart your computer before you chack.

 The part of the windows line that says umask=0000 gives read and write access to everyone who uses the computer. If you are the only person on your computer it doesn't matter. If you want to keep it from being altered, you can make it so that only the owner has read/write and everyone else has read only. You do this by changing 0000 to 0222.

---

### Post by xpod on 2006-08-09
Top of the morning to ye.

Well thats another hurdle overcome my friend.It all seems in order as my wee windows icon has magically appeared where before there was none.

Just to reiterate my previous question though....WILL ubunto automatically use this new found 21g...ie i have created the unbunto folder on the root of my c drive but what will happen when the 700mb left on here runs out???

WILL ubunto know what to do or will i have to point it in the right direction.

By the way...i have some irish friends(im a jock)who have relatives on your side of the pond......I know it`s boston they live but i dont know where.
I aint seen my irish friends for a while as they still live in Scotland and i unfortunately live in london nowadays......BUT unlike my compatriot the esteemed "William Wallace" i aint quite gone to pieces down here yet.

Thank you again my man......As i explained in a previous thread ive only been doing this pc stuff for a few months and although i may ask a lot of questions initially i learn quickly.I was doing things with my xp that most people would be taking their pc`s to shops to get done.

I just have SO much windows stuff crammed in that i need to remind myself thats not where i am now..........GOOD STUFF

---

### Post by catlett on 2006-08-10
No Ubuntu will not automatically put anything in the folder. You have to purposefully put data/downloads there.
Just use that to store any documents/pictures/anything you obtain while using ubuntu on it. If you don't add more appplications your system isn't going to grow much more.
One thing you can do to save space is change the way Synaptic Package Manager (and apt becuase synaptic is the gui front end for apt) handles the apt cache.
Go to System<Administration<Synaptic Package Manager and select "Settings" and then select "preferences". When that window opens select the "files" tab. In files do 2 things. First hit on the box "delete cached package files", this will delete the files that were held in the cache from your installing through apt-get or synaptic. Then change the filter for "temporary files" to "delete downloade packages after installation". You can also change the History File filter to "delete after ?days" but I do not think this becomes anything considerable.
I had a cache of 500mb so it was worthwhile for me, but I do not know what yours will be.
This is the only space saving I do but I am sure others know much more. I remember one post that said to go into synaptic and delete the extra fonts because it will free up a couple hundred mb but I do not remember the post that welll nor do I have personal knowledge of it.

Take care.

P.S. If you talk to the Irshmen with kin on my side, they will know where I live, it is a bastion of Irish Catholocism. Charlestown, MA. is to Boston like  Charlestown is part of Boston but the different parts have their own names. The first English settled here and named it after King Charles. They eventually moved across the river to the Boston peninsula for better drinking water. Most people know Charlestown because it was the site of the  Battle of Bunker Hill when we kicked the British out :razz:  on St Patricks Day no less! I actually live on a litle street off on Bunker Hill Street. In case you are very bored and your fiends are curious, here is a Google map link (gota love the internet :D  ) [http://maps.google.com/?q=1+Short+Street+Pl,+Charlestown,+MA+02129+(Apt)&ie=UTF8&ll=42.383274,-71.070557&spn=0.021746,0.05403&om=1](http://maps.google.com/?q=1+Short+Street+Pl,+Charlestown,+MA+02129+(Apt)&ie=UTF8&ll=42.383274,-71.070557&spn=0.021746,0.05403&om=1)

---

