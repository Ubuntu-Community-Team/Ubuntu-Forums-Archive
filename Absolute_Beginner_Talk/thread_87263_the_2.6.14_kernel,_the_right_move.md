---
title: "the 2.6.14 kernel, the right move?"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by iamtaylormade on 2005-11-07
[FONT=ARial, helvicia][SIZE=2]So I see that Mr. Turvalds released the 2.6.14 kernel just a couple of days ago. I have been waiting for some NTFS support and the way I read the article, it may be in there?
[/SIZE][/FONT]
 [FONT=ARial, helvicia][SIZE=2]
[http://www.desktoplinux.com/news/NS8664091380.html]("http://www.desktoplinux.com/news/NS8664091380.html") 
[/SIZE][/FONT]
  [SIZE=2]
[/SIZE] 
 [FONT=ARial, helvicia][SIZE=2]I Just started with Ubuntu and the whole Linux change in the last couple of weeks. Not sure how to upgrade the kernel, where to get it or if I should even do it at all right now or if I even can do it right now. Damn, I hate being a Linux noob! I refuse to quit, this stuff is too good![/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=ARial, helvicia][SIZE=2]I am running Ubuntu Breezy in 64bit mode (AMD) and would really like to have some NTFS support, considering I am attempting to make this box a file server (1TB RAID) to support Linux and NTFS based Windows machines.[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=ARial, helvicia][SIZE=2]Any comments, recommendations etc. would be greatly appreciated.[/SIZE][/FONT]
 [SIZE=2]
[/SIZE] 
 [FONT=ARial, helvicia][SIZE=2]MT[/SIZE][/FONT]

---

### Post by Kyral on 2005-11-07
NTFS support (writing at least) will be sketchy for a while. Read support has been around for a LONG time. Though I am afraid that you will never be able to install Linux on NTFS

---

### Post by iamtaylormade on 2005-11-09
Kyral, A question that I would have would be this.  
If I were to set up a RAID with multiple partitions, including NTFS, formatted via the RAID controller, would I then be able to access the partition/disk via an NTFS writing capable system such as a computer running WinXP even though it is physically on the Ubuntu box? 
I have been crafting a server with Ubuntu with several Windows machines on the LAN and want to use a journaling type of file system, not FAT, being compatable with Windows.
I guess I am also asking if, and how I could share a drive/partition even though Ubuntu cannot write to it, if this is possible with the RAID being on the Ubuntu box and not being able to write to it.
   Thanks in advance,
   MT

---

### Post by strips on 2005-11-09
If I get youg question right. No.

On a server running Ubuntu or any other linux you only get read-only access to an NTFS partition. And the speed may be slow to.

But there is no need for NTFS if only the other computers are Windows. As long as you don't need physical access from a Windows computer to the disks you can go with a Linux based filesystem.

You want to be rock stable you go for ext3, you want a bit more speed and next to rock stable ReiserFS is a good alternative. There are other good FS to. The ones I mention are journaling FS.

Than you go with samba / windows shares to access the disks over LAN.

---

