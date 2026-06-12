---
title: "Secondary Hard Drive Formatting"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Mizled on 2007-03-02
I have a secondary Hard Drive mounted. Its /dev/hdb1 I believe. Theres some files on there I want to save but I really want to clean this disk up....Is there a program I can use in Gnome to partition it in half and drop the files on it I want save then format the other half and then merge the two partitions back together saving the files I want to keep? This is a NTFS disk by the way. I don't want to do backups on discs/dvds because theres about 60+ gigs of data I need to save...Also, should I leave it NTFS or is there a better one to use...its only going to be used for music, dvd backups, pictures, and document storage...

---

### Post by mgmiller on 2007-03-02
I think the program you want is gparted.  It's in the repositories, just use synaptic.  If your system is Ubuntu only, I would suggest changing the drive from ntfs to ext3.  The ability to write reliably to an ntfs volume is still iffy, and there is a nice utility for windows to enable reading / writing to ext2-3 volumes, if you need to maintain compatibility with windows.

---

### Post by laidback on 2007-03-02
Gparted is worth a look. It's probably on your system in System>Administration>Gnome disc editor.
Would this work?
If you could format a new linux partition, e.g. using ext3 format, with Gparted large enough to hold your data without deleting existing partition. Copy over the data to the new partition using standard file copy (not Gparted) then with Gparted again delete the old partition and resize the new ext3 partition.

---

### Post by Mizled on 2007-03-02
That's what I'm looking for. I'll give Gparted a shot and use Linux ext3. Will Windows be able to recognize the ext3 via a network with the correct setup (i.e. the right windows drivers etc)? I'm currently running straight Ubuntu on all my computers except my main computer that I use for Gaming/DVD Backup and would like to able to access some of those from that network computer...is that possible?

---

### Post by mgmiller on 2007-03-02
> Will Windows be able to recognize the ext3 via a network with the correct setup

Yes.  You will need to setup samba on the Ubuntu machine and then windows can see and share files without any problems.

Read up on setting up a samba server in the Ubuntu starter guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")


Once it's setup, on the windows machine you would just type in the name of your ubuntu machine preceeded by \\ in the browser address bar.  For example, my Ubuntu machine is named tux, so in the address bar I enter \\tux and you will be prompted for your user name and password.  It drops you into your home directory.  you can navigate from there and even set up short cuts to various folders in the Ubuntu machine on your Windows boxes on your windows desktop, just like you would save any other website shortcuts.  I use this on my home network with 2 Ubuntu computers and 3 WinXP machines.  They all share files and stream audio and video seamlessly.

---

