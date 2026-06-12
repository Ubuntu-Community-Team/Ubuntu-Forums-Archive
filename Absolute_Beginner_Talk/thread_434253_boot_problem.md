---
title: "boot problem"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by mayardjembe on 2007-05-05
Hi! this is a very happy ubuntu user. I had no problems before only a win modem, but that is another issue.
The problem today is that my 6.06 ubuntu  hangs while it is in boot sequence. It stops at *mounting root file system*. I have tryed the recovering option on GRUB but it is also imposible to boot from there. While it goes for all the boot process on the recovery mode it finds an *ide error*.

All of this started after a little  accident with my pc. I thought at first the hard disk was broken :confused: but no.
I have windows xp on another partition and it works well (well you know how windows works can not be that well, but it works)

Right now i am using the live cd and after fdisk -l i have the following:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         523     4200966   1b  Hidden W95 FAT32
/dev/hda2   *         524        3928    27350662+   7  HPFS/NTFS
/dev/hda3            3929        4864     7518420    5  Extended
/dev/hda5            3929        4581     5245191   83  Linux
/dev/hda6            4583        4736     1236973+   b  W95 FAT32
/dev/hda7            4737        4864     1028128+  82  Linux swap / Solaris

I am wondering if i try with the *recovering crashed system application on Ubuntu alternate cd * but I am affraid i will lose all installed software on my previous installation.

Does any one can help me?

Thank you


More info :


by usin the recovery mode booting i got the following:


Ide: failed opcode was: unknown
i/o error, dev hda, sector 71762426
high =4 low = 4653562, sector= 71762426



Using the IFS Drives for Windows i can read my /dev/hda5   where my Linux system is so seems that is not a physical problem after the accident, but something that i noticed is that the swap partition is full on ubuntu's partition application and on windows it doesn't show either the used or free space 

hope someone can help!

---

### Post by Herman on 2007-05-05
Hello mayardjembe,
There are some jobs the 'Alternate CD' is good for and there are other jobs a 'live CD is good for. Well to be more exact  I don't know how to use that part of the 'Alternate' CD for what you might need to do, someone else may know.

One easy thing to try first would be to use a LiveCD like a Ubuntu Desktop LiveCD or Knoppix and run a filesystem check on the file system in your Ubuntu partition.
You already know from your fdisk output in your post above that your Ubuntu partition is /dev/hda5.
Try 'sudo e2fsck -CO -p -f -v /dev/hda5', and see if that helps, if you are lucky that will fix it for you or at least give an error message telling you something else you might need to do to fix the problem.
> sudo e2fsck -C0 -p -f -v /dev/hda5If you don't like using the command line, try downloading a new version of [GParted -- LiveCD]("http://gparted.sourceforge.net/") and burn it to a CD-RW or CD-ROM disk and boot that. When GParted LiveCD is running, right-click on the partition and click 'check'. When the filesystem check is finished you can click on the triangle shaped buttons to expand the output box and see what GParted has fixed and if there is any more to be done to your filesystem.

With luck a filesystem check may fix your problem, and at least it is always a good thing to do and will always help and not hurt your system. Post back here when you are ready and if more needs to be done I or someone else will try to help you.

What kind of accident did your PC have?

Regards, Herman :)

---

### Post by Mihkal on 2007-05-05
It sounds like the hard disc was damaged.

If you can mount your linux partition from the live cd, use gparted
to check it.

---

### Post by mayardjembe on 2007-05-05
Hi Herman, hi Mihkal, thank you for your replay,

Herman I have done what you told me to do and this is what i got;

> root@ubuntu:/home/ubuntu# e2fsck -C0 -p -f -v /dev/hda5
Error reading block 557070 (Attempt to read block from filesystem resulted in short read) while doing inode scan.

/dev/hda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)


Mihkal what i have on Gparted is the following;
Filesystem: ext3
Size:          5.00 GB
Used:        3.75 GB
Unused:     1.25 GB
Flags:

Path:        /dev/hda5
Status:     Not mounted

First Sector: 63103383
Last Sector: 73593764
Total Sectors:10490381

still trying to figure out what isexactly the problem.

The accident with the pc is simple It felt from the table, my pc is a Packard Bell EasyNote R4345 laptop, and after it felt seemed that there was no problem at all, I worked for hours.
The problem came as soon as i restarted the computer. 

When i talked about trying with the *recovering crashed system application on Ubuntu alternate cd* i wondered hmmm... since it finds the different partitions that maybe it could repair any damage. Lucky me all my info is on a different hd an external one, but i want to keep all the software that i allready installed, not all is from the repostories and since i am quite inexpert on compilation you know... if you come from windows enviroment you become a lazy one.

Well if you have any other suggestion i'll be happy to try

again 
thank you

---

### Post by Herman on 2007-05-06
Hmm, well I am reluctant to hurry right now, but I think you will have to do as the output advises and run e2fsck from the LiveCD again without the -p option.
The -p option was for fixing all the errors it could without safely fix without human intervention.

You should back up any files you might have on this disk, I know you said you have most of your files in the external hard drive, but if you have any in the laptop hard drive you should make a backup of them the best way you can asap.

This time when you run e2fsck again it will want to move some of your files to the lost and found directory, it will ask your permission first.I forget exactly how these questions are worded, but something to that effect. If you say no, you'll probably have to go through the whole process again so I don't know if there is any advantage in saying no. You might say no to all questions if you weren't expecting any trouble and you didn't have all your files backed up already and you want a chance to save what you can before running e2fsck again. I would expect you will lose at least a few files now, sorry about that.

If you don't want to have to type 'y' or 'yes', possibly hundreds of times in succession, run e2fsck with the -y option. That will be faster. You will lose files. If the damage is not very widespread, and the files you lose are not vital, you can boot the operating system and it will run again. Then you might be able to recover some of your files from the lost + found again. If the damage is widespread or if it affects vital files you may have to re-install, sorry. 
I would run 'sudo e2fsck -y -f -v /dev/hda5' ```
sudo e2fsck -y -f -v /dev/hda5
``` and then I would run 'sudo e2fsck -c -c -k -v /dev/hda5' ```
sudo e2fsck -c -c -k -v /dev/hda5

```That command will run a different kind of filesystem check to test your hard disk for bad blocks in that partition and it will remember which ones they are so the filesystem will be able to skip them and not write any data to those bad blocks any more.

I hope after that your operating system will reboot and it will be okay.

Actually I think you should not do anything for a while and wait for a second opinion on all of this first. Hopefully someone with more experience will be able to see a mistake in my advice or else maybe can confirm that this is okay to go ahead with.
You should also check the man page for e2fsck yourself as well and see if you agree with these command options or if you want to try something a little different instead.```
man e2fsck
```

I hope a more experienced forum member will comment on this before you go ahead with these commands.

Regards, Herman :)

---

### Post by mayardjembe on 2007-05-06
Hi Herman, good to hear another advice from you. 
Actually I allready pass trough the lost and found process, but not with e2fsck, instead as the prompt recomended
> /dev/hda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)

After that still nothing, can't boot my pc, but one thing i forgot to say is that at one point seems that the recovering mode finishes the boot process and it takes me to a login prompt not a GUI login but the text one and after i type the username it starts looking for the hd again. No login, or ending boot secuence.  

So, with the all the "yes" that i had to type with the fsck, i had also the time to search a little bit more, I found by searching "stall boot mounting root file system" so i found that there is a problem to others that is quite similar to my problem

here
[http://ubuntuforums.org/showthread.php?t=186115&page=2&highlight=stall+boot+mounting+root+file+system]("http://ubuntuforums.org/showthread.php?t=186115&page=2&highlight=stall+boot+mounting+root+file+system")


and here

[http://ubuntuforums.org/showthread.php?t=197956&highlight=stall+boot+mounting+root+file+system]("http://ubuntuforums.org/showthread.php?t=197956&highlight=stall+boot+mounting+root+file+system")


there is also this page 

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/36667]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/36667")

but is too far from my linux-starter skills thoug i keep learning every minute an i like that


So far i haven't done any of the workarounds that those pages suggest, mainly because i dont understand the process, sorry too newby for this :confused: . In fact i am not sure if it is exactly the same problem

But i will keep trying

Next thing i'll do is just what you said.

thank you very much for your advice. I'll post any changes

---

### Post by mayardjembe on 2007-05-06
there is also this page [URL="http://ubuntuforums.org/showthread.php?p=1257154"]
 it shows that it is actually a bug but still wondering if my problem fits exactly on this issue.
keep searching.

---

### Post by Herman on 2007-05-06
Hello mayardjembe,
I think if the laptop fell off the table while the hard disk was still possibly spinning, the read/write heads of the hard drive may have been jarred into contact with the platter. That could have done a small amount of damage to the hard disk surface, or maybe even quite a lot of damage.
I'm not a hard disk expert, but that's what I imagine would be likely.
Some important parts of the operating system are loaded in the computer's RAM while the system is still up and running. Then when you turn the computer off it forgets those things. Next time you try to boot up if it can't read some of those important files from the hard disk it can't boot. Maybe something like that anyway, I am only guessing.

That would be unlikely to have anything to do with any bugs in Ubuntu.

No-one so far has either criticised or confirmed whether the commands I suggested are okay or if they could be improved.

You have to decide how important your time is to you. It only takes about half an hour to re-install Ubuntu and then some time to re-install your files and added software. 
To keep trying to fix your existing install, if a few easy commands can't fix it, could take forever and you might end up having to learn enough to build your own operating system from scratch. You might be old and grey by the time you get it fixed.

I think just run those e2fsck commands and if you still can't boot up normally then just delete the whole partition and re-install.

But first I can help you mount your old partition with the live CD and rescue any files first like your email or bookmarks and that sort of thing. Let me know if you need help with that. (If those files are still able to be read).

Regards, Herman

---

### Post by mayardjembe on 2007-05-07
Hi Herman!

Yes in fact that was my first thougt, but you know when something can be really bad with the hard disk you just avoid the idea and keep trying even if it is useless...
Right now I am just waiting until I have a little free time to get into the all installation process.
To much aplications to download, to much configuration to do...
Any way thank you very much for your advise, and yes i would like also some info about recovering the information. I have tryed mounting /dev/hda5  using the live cd but so far can't mount it. I want to recover that info using linux even when i have access to hda5 from windows using a windows driver *"IFS Drives for Windows"*.
Well again thanks 

ps Do you know a good guide or tutorial for linux on pdf format?

---

### Post by Herman on 2007-05-08
Hello mayardjembe,
I haven't tried making very many .pdf files, I like .html files the best. I make those with 'NVU' in previous versions of Ubuntu like Dapper Drake and Edgy Eft. Now in my new Feisty install I make them with 'KompoZer'. KompoZer is the new NVU for Feisty. To install NVU in Ubuntu 6.06 or 6.10 if you have the right repositories enabled you should be able to find it in either Add/Remove Applications or in Synaptic Package Manager, or use apt-get.
I find .html files very handy for recording most types of written information in my computer because I can easily hyperlink all the .html files I have from one big index file. That way I can look things up very quicky, sometimes in an instant. I have the master index file set as my homepage in firefox.  I have it divided into two sections, outside links which are like bookmarks to the internet and internal links to my own ,html file collection. My collection of .html files is all inside one special directory for only .html files and their folders containing any images that go with them. It's a very good way to organize any computer.
As far as making .PDF files goes, all I know is I can make them with Open Office .org Word Processor, just click the File menu and click 'Export as .PDF', but I think you are looking for some type of advanced course in it maybe?

About mounting your old Ubuntu installation in your Live CD to rescue your files, here is a link to the part of my web page on that where I explain the basic idea of it, **       [   Filesystem mounting basics]("http://users.bigpond.net.au/hermanzone/p10.htm#Filesystem_mounting_basics")** 
Then when you have the basic idea, you can take a look here at how to [                                  Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
                                           [COLOR=#666666][COLOR=#000000]When you have tried something like that in your computer, using /dev/hda5 instead of /dev/hda2 I used in my example, you should be able to 'see' all your old files, I hope. :)

What kind of media have you got around that you can back up your files to? Your external USB drive would be the easiest if you still have enough room left on it. I imagine that's what you will probably do.
Some people need to use some kind of networking like [/COLOR][/COLOR][SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm") to transfer the files to another computer when they do a file rescue.

It's easy to find all your regular files in your /home/username folder.
This page has information that will help you find your email as well as calendar settings, addressbook, memos and tasks if you had any of those in evolution, and firefox bookmarks too. [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm")
There might be a few other things you will be able to save that I didn't think of as well, you should take time to think it over before you delete the old file system and re-install.  Maybe your /etc/apt/sources.lst if you had special repositories added and maybe /boot/grub/menu.lst if you had it customized.

Next time when you have Ubuntu re-installed it is better to use apt-get to install most of your added software if you can instead of Add/Remove or Synaptic. That way you can copy each of your apt-get commands to a text file and save it so you'll remember what to re-install in the future if you ever need to do it again. You can make that into a script that can run automatically and replace all your added software fairly quickly and easily.

Actually, you can use Partimage or Clonezilla in [GParted -- LiveCD]("http://gparted.sourceforge.net/") if you want and make a backup of your entire partition when it is running well. If anything like this ever happens again you'll be able to restore everything including all your added software from a Partimage or Clonezilla backup.

That's all for now, good luck mayardjembe,
Regards, Herman  :)

---

### Post by mayardjembe on 2007-05-08
Thank you very much Herman I'll give it a try to apt and maybe clonezilla, but first it is learning time, let's read the pages you send in order to mount the partition on live cd...

as allways thank you

Regards mayardjembe :)

---

