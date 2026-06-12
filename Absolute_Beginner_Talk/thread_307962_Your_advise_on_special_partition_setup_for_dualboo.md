---
title: "Your advise on special partition setup for dualboot"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-11-27
Hi everyone,

after having seen how nice Ubuntu is with the LiveCD, I'm ready to do the install on my laptop and dualboot it with XP. I know there are plenty of guides everywhere that explain how to dualboot Linux and XP or how to setup partitions but I'd like to do it in a special way focusing on 2 purposes:

a) I want a separate /home partition. This partition will be ext3 but it will be shared between XP and Ubuntu (XP can read/write ext3 partition with FSDrive driver).

b) I want one separate partition for Linux swap and another one for XP pagefile. Apparently it's best to place these virtual memory partitions at the very beginning of the disk since it provides faster access (is this true????)

c) I also want a separate partition for temporary files (both XP and Linux /tmp folder). This partition is also ext3 (accessed by XP through FSDrive)

d) I'd like Ubuntu to be in a partition before XP so that when I will want to get rid of XP I can simply give its partition space to the /home partition without having to "move" Ubuntu system files.

My laptop has a 60Go HDD. In summary here is the layout I propose to achieve:

1) Linux Swap   (1 Go)
2) XP pagefile  (1 Go, NTFS)
3) Ubuntu       (10 Go, Ext3)
4) XP           (10 Go, NTFS)
5) /tmp         (5 Go, Ext3, shared by XP and Ubuntu)
6) /home        (32 Go, Ext3, shared by XP and Ubuntu)

So my questions are:

- Is this a good partition setup?

- Now XP is installed on the first partition of the disk, will it still boot OK if I create 3 partitions before it to place Linux swap, pagefile and Ubuntu? I will use PartitionMagic to do that.

- Is it recommended to place Linux Swap at the very beginning of the disk (first partition)? XP gurus say that placing the pagefile as the first (separate) partition is best to achieve speed.... Is this the same for Linux swap?

- Any other recommandations?

Thanks.

---

### Post by tonyr1988 on 2006-11-27
Would you be keeping your Windows programs in the /home partition or in hda4? Most recommendations I've heard say XP should have at least 15GB, but it all depends on how many programs you plan on having.

NOTE: It is possible to have all your windows programs in a separate partition. You can easily change the default install path to something other than C:\Program Files.

I'm not sure about the swap / pagefile. You'll need someone a lot smarter than me for that. :)

Also, I wouldn't use PartitionMagic (I won't be the first to recommend against that, either). It does Linux partitions poorly (from what I've heard). I personally love the GParted LiveCD. Check it out here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by bulldog on 2006-11-27
This will be a no go,sorry.

Your windows must be on the first partition otherwise it won't boot if you put a swap file as first partition.

And for the rest of your layout,I'm not seeing any advantage in doing it this way,you just create a fair change of malfunction and loosing data from Ubuntu and XP as well.

About the page file and the swap,you won't notice any difference if it's at the end of you drive.

---

### Post by kilou on 2006-11-27
XP programs will be in the same partition than XP itself and I plan on giving this partition 10Gb. My current install has now 8Gb so it should be OK. I guess the advise of 15Go is if you put everything (including pagefile and temporary folders) on the same partition.

It is definitely possible to have XP installed on another partition than the first one. I already did that and those that run the pagefile on the first partition also don't have problems. The only thing is that I don't know if it is possible to do it without completely reinstalling XP. Basically as long as the boot loader knows where XP is installed it should be OK no?

Not sure if swap at the beginning of the disk is really good or not. This is recommended by XP gurus but.... 

Bulldog, what problems are you seing in my layout? What would potentially cause troubles? It has been recommended here ([http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)) to use a shared ext3 partition between XP and Ubuntu since XP can access ext3 through FSDrive. I could also use FAT32 but ext3 + FSDrive appears as a better choice since my primary OS will be Linux.

Another possible layout with swap at the end would be:
1) XP (10Gb, NTFS)
2) Ubuntu (10Gb, EXT3)
3) /tmp (5Gb, EXT3, shared with XP)
4) /home (32Gb, EXT3, shared with XP)
5) XP pagefile (1Gb, NTFS)
6) Linux swap (1Gb)

Another question:
Is it easy to move Linux /tmp to another partition once Ubuntu is installed?

---

### Post by housam on 2006-11-27
I think you can use Gparted live CD as it is a good partitioning tool. 
I suggest that you Do not change xp location (as it may damage the MBR data)and to partition your HDD as follows :
 
win-xp   10G   ntfs 
ubuntu   10G   ext3
swap     1G (as much as yor RAMs)
/home   39G   ext3  (including pagefile & tmp.)

N0 harm if you deleted xp afterwards.
good luck

---

### Post by az on 2006-11-27
In regards to the page/swap partition, I think it is meaningless.

If you want to improve performance, just add more ram.

I doubt that data reads/writes faster from the beginning of the disk than the end of the disk, and even if this was true, it would be pretty much irrelevant considering the relative difference in accessing something from ram and accessing it from a hard disk.

As well, linux probably uses the swap space a little differently than XP uses the page file/space.  I know that you can avoid swapping altogether in linux, provided you have sufficient ram.

Be sure to not use suspend-to-disk (hibernation) if you plan on sharing the swap partition with another OS -  the contents of your ram are dumped there just before it suspends.  The swap space needs to be about 25 per cent larger than your system ram for it to work.

---

### Post by kilou on 2006-11-27
@Housam
Since I already have the Ubuntu LiveCD, I should be able to access GParted from it too before doing the installation.

Why would you put temp (and pagefile) in /home? Wouldn't it be better to have a separate partition for all temporary files (XP temp and Ubuntu /tmp) to prevent fragmentation on other drives?


@Azz
Is it possible to share the Linux Swap partition with XP????? I would be highly interested in doing this but as far as I know XP can access ext3 with FSDrive....but Linux swap are a different format, no? It would be excellent if I could put both Ubuntu swap and XP pagefile on the same partition (I don't care about hibernation, I never need this feature).

Is Linux swap also a ext3 format?
How can I disable hibernation in Ubuntu?

---

### Post by duality on 2006-11-27
Windows usually takes over the first sectors of the disc (the MBR), so you might want to have it on the first partiton, then install ubuntu, heres my setup on my 100gb laptop:
1.windows XP  14Gb
2.root 5Gb
3.var 2Gb
4.swap 1.5Gb
5.home   the rest

but you can also just have everything on root and swap.

---

### Post by housam on 2006-11-27
Just to save wasting your HDD into many partitions.

---

### Post by kilou on 2006-11-27
I will use either Mozilla Thunderbird or Evolution as mail client. Is the mailbox saved in /home or in /var?? I definitely want it to be saved on another partition than the system. Duality, is this why you created a separate partition for /var??

Do you know if the swap partition is also Ext3 or another format?

---

### Post by housam on 2006-11-27
swap is a swap format, 82 linux/solaris

---

### Post by kilou on 2006-11-27
It seems it is possible to share swap space between Linux and Windows but I still need to find out how to do this since it sounds a little hard core for a newby like me but this would be great. I could find this at least: [http://tldp.org/HOWTO/Swap-Space-6.html](http://tldp.org/HOWTO/Swap-Space-6.html)

I'm also wondering if I should do a separate partition for /usr/local. From what I read this folder is where you store 3rd party applications that are installed manually. It would be nice to have it on a separate partition because if I need to reinstall Ubuntu, I can format and reinstall it on its partition but all the 3rd party applications will still be available on first boot since they are not located on the partition that was erased! Is this a good thing to do? 

What about a separate /var partition too (I'm confused whether mail is stored in /home or /var). Again is there anything in /var that you don't want to loose if you erase the root partition when reinstalling??

---

### Post by az on 2006-11-27
> **kilou said:**
> It seems it is possible to share swap space between Linux and Windows 

Than link deals with windows issues.  From the linux point of view, you cannot use a partition as swap unless it is of the swap type.  I should have mentioned this earlier.

> **kilou said:**
> 
I'm also wondering if I should do a separate partition for /usr/local. From what I read this folder is where you store 3rd party applications that are installed manually.  

You will not need /usr/local.  Unless you know for a fact that you will be compiling a lot of stuff, don't bother.  Everything you can possibly need is already in the repos and it is better to stick with the software from the repos.

> **kilou said:**
> 
What about a separate /var partition too (I'm confused whether mail is stored in /home or /var). Again is there anything in /var that you don't want to loose if you erase the root partition when reinstalling??

You don't need a seperate /var unless you are running a server.

In fact, you don't even need a seperate home partition.  It is far simpler to back up your home partition than to dedicate a whole partition to it.  You gain more flexibility in terms of not running out of space by using one single root partition anyway.

Not to mention that it may be that your hidden config files in your home partition are not compatible with earlier versions of the applications they are for -  that means that if you try to dist-upgrade to a beta release, for example, you will still have broken settings when you reinstall and try to use the same home partition again.

---

### Post by kilou on 2006-11-27
If I don't have a separate partition for /usr, what happens when you want to make a clean install (not an upgrade) of a new version of Ubuntu?? Will I loose all the programs I installed and will need to reinstall them all?? I thought that having a separate /usr would "solve" this problem: I could do a clean install but since /usr and thus programs are on another partition, they would be readily available when booting back in Ubuntu.

Is there anything wrong with that? Are the services and libraries required by installed applications also in the /usr folder?

---

### Post by az on 2006-11-27
> **kilou said:**
> If I don't have a separate partition for /usr, what happens when you want to make a clean install (not an upgrade) of a new version of Ubuntu?? Will I loose all the programs I installed and will need to reinstall them all?? I thought that having a separate /usr would "solve" this problem: I could do a clean install but since /usr and thus programs are on another partition, they would be readily available when booting back in Ubuntu.

Is there anything wrong with that? Are the services and libraries required by installed applications also in the /usr folder?

What applications?

---

### Post by kilou on 2006-11-28
Ubuntu comes with a bunch of "preinstalled" software (like Firefox, Gimp etc). Then I will want to add other applications like K3b or Amarok for example by using Synaptic package manager. These additional applications will be stored in /usr right? I could also install 3rd party softwares by downloading them on the web, not through Synaptic. These will be installed in /usr too (/usr/local?). So if a new version of Ubuntu comes out and I want to do a CLEAN install (not an upgrade), will I have to reinstall all these software again?? I was thinking that if the /usr was on another partition, the applications would still be available directly after booting the new Ubuntu.

The second question concerned Qt application especially. When installing a Qt application in Gnome, the required KDE libraries for this application will be downloaded as well. The application is installed in /usr but where do the libraries go? If they go in /usr too then storing /usr on a separate partition will efficiently make all applications available after a clean install of Ubuntu. However if the libraries are stored somewhere else, then it deserves no purpose to put /usr on its own partition.....or am I missing something?

For now I'm thinking of the following layout:
1) XP (10Gb, NTFS)
2) Ubuntu (10Gb, Ext3)
3) Swap (1Gb, Swap/Fat32, shared by linux and XP*)
4) Temp (4Gb, Ext3, shared by linux /tmp and XP temporary files)
5) /home (35Gb, Ext3, shared by linux and XP)

*possible but tricky: the swap partition is created when linux boots and is reverted to a Fat32 accessible to XP when linux shutdowns (look at my 2nd previous post).

---

### Post by CowzRule on 2006-11-28
IMHO, having a partition formated to FAT32 is the safest way to go. In Linux you need to install "Driver" type software in order to write to NTFS and a "Driver" for XP to read/write Ext3. Both read/write FAT32 natively.

---

### Post by housam on 2006-11-28
Try to read this before partitioning :

[http://community.linux.com/howtos/Partition/index.shtml](http://community.linux.com/howtos/Partition/index.shtml)

hope it will help.

---

### Post by kilou on 2006-11-28
Great link, very informative. Thanks Housam!

For sure I want a separate partition for documents but I prefer having my profile settings on the root partition. I usually use Norton Ghost to backup (image) my system and I want all the system information to be on the same partition for easier imaging. If I understood well, it means that I should place /home in the root partition too (so that it will be in the Ghost image). I guess that /home is something similar to "documents and settings" + "My documents" folders in XP. If I build a separate partition for documents but keep /home in the root partition, it it possible to configure softwares (OpenOffice, Email etc) so that they automatically save documents somewhere else than in /home??? This is especially important for mailbox that MUST NOT be stored in the same partition as root otherwise it will be overwritten after each system restore! So is it possible to tell Thunderbird or Evolution to store mails in a separate partition (not in /home)??

I also definitely want a separate partition for /tmp since I don't want to backup temporary files when imaging the root partition in Norton Ghost.

@CowzRule: I may consider a FAT32 volume too but since I want to get rid of XP, I prefer putting everthing in Ext3 and access it through FSDrive from XP. 


Sorry for all these questions. I'm quite confused but I prefer having a clear layout before going with the install. It's much easier to maintain afterwards. So my actual (but not definitive) thinking is (if docs and mail can be stored somewhere else than in /home):

1) XP
2) Ubuntu (including /home)
3) Swap (shared with XP)
4) Temp (shared with XP)
5) Documents and mails (shared with XP)

---

### Post by az on 2006-11-28
> **kilou said:**
> So is it possible to tell Thunderbird or Evolution to store mails in a separate partition (not in /home)??


You can mount things wherever you want.   You can mount an external hard disk in /home/me/files for example.

---

### Post by kilou on 2006-11-28
So is it not a good idea to leave /home on the same partition as / and simply store emails and documents somewhere else? 

For me the point was that I prefer everything related to system on the same partition (except temporary files) and put documents and mails somewhere else because I'm used to partition imaging (but I won't use this anymore since it appears there are much better things for Linux). From what I understand /home contains much more than only my documents or mails, it also contains my profile settings etc. It's probably important to include it in a "system backup" rather than in a "document backup". Therefore would it be better to leave /home with the root and put docs and mails elsewhere?

---

