---
title: "Dual Boot OSX/Kubuntu drive/partition visibility"
date: 2007-11-16
forum: Apple Intel Users
---

### Post by changuito on 2007-11-16
HI there. I suspect the answer to my question is out there but i'm having a hard time finding it so it thought i post this. It's a very basic question.

If i have the following partition configuration
MAC HD: hfsplus
EFI: vfat
Linux: ext3
swap

can i access Mac HD when I boot in linux? (i can see it but the mount is always refused)
can i access linux when i boot in mac? (dont think i can even see it at all)

I actually installed a fat32 partition but i dont think i made it large enough, so i'm considering going back and enlarging it before i have too much invested in either of my OSes.

Thanks!

---

### Post by cyberdork33 on 2007-11-16
> **changuito said:**
> can i access Mac HD when I boot in linux? (i can see it but the mount is always refused)
need more info. How are you trying to mount it? What is the error you get?

> can i access linux when i boot in mac? (dont think i can even see it at all)
yes. get the dev version:
[http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713)

---

### Post by changuito on 2007-11-17
cyberdork, thanks for your help.

I followed these instructions

[https://wiki.ubuntu.com/MacBookPro]("https://wiki.ubuntu.com/MacBookPro")

which are repeated elsewhere on the ubuntu forums.
basically the steps are: bootcamp -> install refit -> partition -> install kubuntu

I enter kubuntu, then I go on to modify /etc/fstab as described. I end up with /media/Macintosh as a read-only file system. That's not what I want...

In OSX, i have to enter the disk utility to even be able to see that the system (I'm not at all familiar with Mac inner workings). Here I am unable to mount or to verify the linux partition. (I am also not able to mount the fat32 partition I created.)

While the details are important, I'm just unlcear about what to expect and what my best options are for partitioning my drive if i want to be able to share documents between the 2 OSs. I know there are various benefits to partitioning, but I'm interested in what is practical mostly in terms of usability by both systems and want to avoid a permissions nightmare. I'm tempted to think having a fat32 partition might be useful in this case, but I'm really not basing that on anything...

cheers

---

### Post by cyberdork33 on 2007-11-17
I don't know what the issue is with the fat32 partition. 

Did you get the software I linked to to mount ext3 partitions in OSX?

> **changuito said:**
> I enter kubuntu, then I go on to modify /etc/fstab as described. I end up with /media/Macintosh as a read-only file system. That's not what I want...

Well then it _is_ mounting, that is not your issue.
You cannot write to an HFS+ filesystem unless journaling is disabled.
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)
You will still have permissions errors since your Ubuntu user and OSX user are not the same. You will have to make sure you change the permissions of any files in OSX that you want to make sure you can access from in Ubuntu.

---

### Post by changuito on 2007-11-17
g'day!

I'm very close to having this all ironed out. 

I am able to read and write to the Mac partition now from within Kubuntu after diabling journaling on the Mac Partition. Excellent! Check it off. 

I installed Ext2FS and now am able to mount my ext3 linux partition when I am in Leopard. However, it remains read-only. I noticed that the ext3 partition is journaled. Is this causing it to be mounted read-only? I went into the ExtFS manager and I do not have the read-only mount option checked, so it's some how forced to mount this way. 

In the end, I will probably ditch my fat32 partition if i get the above issue sorted, since i have external fat32 drives and having only 2 partitions which are transparent to both systems will just reduce fussing.

I was wondering if the details here should be added to the wiki page on dual booting, since they seem highly relevant. (I dont feel like i should be the person to add them, however... unless someone else insists!)

Thanks for your help, CyDork33, it's very much appreicated.

---

### Post by changuito on 2007-11-17
I changed the linux partition to ext2, but that did not make it writable from OSX. 

Not sure what next.

---

### Post by changuito on 2007-11-18
So, suspecting that things were not done properly when trying to convert my ext3 partition to ext2, i wiped my linux side of things and performed a reinstall using both ext3 and ext2. 

When I reinstall on ext2, I am able to writeably mount my linux partition from OSX using ext2fs. When I install using ext3, I get read-only status for my linux partition from OSX (from ext2fs). So, while seeing no confirmation of this anywhere in anything i've read, i infer that (as for journaling on the mac partition) journaling (ext3) forces mac to see the ext3 partition as read-only. Is this true? Reading some other posts, people have apparently given up on writing to ext3, i've seen no accounts of making ext3 writable.  

So, at this point my situation was:
-In OSX i can mount my linux partition but I dont have the proper permissions (eventhough my username is the same on both systems, but my userid is not). I can choose to ignore permissions in ext2fs and i get write permissions, but that's not satisfactory as I'm afraid i might ruin sensitive files on my ubuntu installation.
-In Ubuntu, i have slightly too much permissions from chmod 777 /media/Macintosh - since I want to restrict myself to directories which I've already created in OSX.

In Ubuntu, I had tried to change my userid in system settings -> user management before, but this always failed with some odd behavior. So i resorted to command line with the following:

sudo groupmod -g 501 userid
sudo usermod -g 501 userid
sudo usermod -u 501 userid

then
sudo chmod 755 /media/Macintosh

I then reboot in to either OS. (When logging into ubuntu, you may not see your account listed, but you can still login as normal - this issue is mentioned below)

** This seems to solve the problem ** 
-In OSX i do NOT ignore permissions in ext2fs when mounting the linux partition. I now seem to have the correct accesibility. I navigated around in command line and did some "touching" and "rm-ing" and "cp-ing." only those directories owned by my user name/id allowed me to write! that's what i want. 

-In Ubuntu, accessing /media/Macintosh also seems to behave correctly! But there is a new/another issue (which i will come to in momentarily). I navigate around and do the same as above and everything seems cool. My only concern is that /media/Macintosh/efi is owned by myself. I am considering changing the owner ship on this to root, but I will investivate and sollicit advice on this before doing that.

So, the new issue in Ubuntu is that Ubuntu is confused (or something) when dealing with your user ID. As mentioned, your account is not listed at login in the list but you can still login. Going into system preferences -> user management also fails to show your account! WTF? Is there something in the interface that needs the userid number to be greater equal to 1000? WTF? Is this behavior expected? Is this a bug? So far, everything else seems stable and good... Can anyone elaborate on this new glitch? Should I be more concerned?

---

