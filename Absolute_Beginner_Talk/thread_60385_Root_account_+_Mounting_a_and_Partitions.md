---
title: "Root account + Mounting a:\ and Partitions?"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2005-08-27
Hi I've decided to get serious this time at learning Linux.  So I'm having major trouble getting my **Firefox bookmarks** to move from my Windows XP to my Ubuntu.
**1.** So I've tried to use the **a:\ **diskette drive but I can't see any files that's on the disk?

**2.** I also want to mount my NTFS drive (36 Gb) into Ubuntu (1 Gb), but I've read in the NEWBIE sticky that mounting a FAT/NTFS requires that EXT2/EXT3 is equal or larger than the FAT/NTFS partition.  Is that true or don't I necessary have to copy the entire Windows NTFS partition into Linux partition??

**3.** Last question, I'm told that in order to** mount partitions** I've got to be **ROOT**?
When installing Ubuntu I was only asked to create a 1:st user account, I was never asked to create a Root account nor was I asked to type in a password for Root.  How do I create Root in this case with my fresh Ubuntu?

---

### Post by Kapre on 2005-08-27
[QUOTE=jingo811]Hi I've decided to get serious this time at learning Linux.  So I'm having major trouble getting my **Firefox bookmarks** to move from my Windows XP to my Ubuntu.
**1.** So I've tried to use the **a:\ **diskette drive but I can't see any files that's on the disk?

**2.** I also want to mount my NTFS drive (36 Gb) into Ubuntu (1 Gb), but I've read in the NEWBIE sticky that mounting a FAT/NTFS requires that EXT2/EXT3 is equal or larger than the FAT/NTFS partition.  Is that true or don't I necessary have to copy the entire Windows NTFS partition into Linux partition??

**3.** Last question, I'm told that in order to** mount partitions** I've got to be **ROOT**?
When installing Ubuntu I was only asked to create a 1:st user account, I was never asked to create a Root account nor was I asked to type in a password for Root.  How do I create Root in this case with my fresh Ubuntu?[/QUOTE]
 Jingo811 - Welcome to Ubuntu. 

1. You cannot see any files on the diskette - try to mount your floppy 1st (click into your "computer" and then look for then look for the floppy drive) and then you can browse the files on it. 

2. Try to read this [www.ubuntuguide.org/#mountunmountntfs](www.ubuntuguide.org/#mountunmountntfs)

3. You can be root by typing "su" (w/o quote) on the terminal. Just type in the password that you created on your user acct.

---

### Post by edwina on 2005-08-27
Hello. I hope that I can help to elaborate on Kapre's answers. Sometimes a few options makes it easier to get used to Ubuntu. Mind you, I'm pretty useless at anything harder than point and click.

If your floppy is not mounted, then you can't see files. You can sort this out simply by adding "Diskmounter" to one of your Gnome panels. Just right click on a panel, go to "Add" and choose Diskmounter. Your available drives/partitions can then be mounted/unmounted from the panel very quickly and easily.

My Ext3 Ubuntu partition does not appear to have a problem with mounting a larger NTFS partition with XP on it. 1Gb is not a very large partition for Ubuntu - I think that about 3Gb is recommended. You could pick up an extra 5Gb drive for not much money. Setting up your fstab file properly is probably the trickiest bit as it has several variables. Have a look at my posts if you'd like to see how I did it, for a bit of help (there's one called "HowDone - installed Ubuntu" or something).

Not sure about root passwords. I can't remember how mine was set up. Certainly it is probably the same as the password you typed in during installation, if you can only remember doing it once.

Hope that helps. Good luck and have fun!

---

### Post by racecat on 2005-08-27
If I may expound a bit on #3. In your terminal, type sudo (superuser do) before any command requiring root permission. After you hit enter, you will be asked for your password. The password is the password you entered upon installing the software.

Here is an example from my system opening Synaptic:

bill@ubuntu1:~$ sudo synaptic
Password:

Hope this helps

---

### Post by nERDboY on 2005-08-28
[QUOTE=racecat]If I may expound a bit on #3. In your terminal, type sudo (superuser do) before any command requiring root permission. After you hit enter, you will be asked for your password. The password is the password you entered upon installing the software.

Here is an example from my system opening Synaptic:

bill@ubuntu1:~$ sudo synaptic
Password:

Hope this helps[/QUOTE]
 If you want to only view your ntfs drives [www.ubuntuguide.org/#mountunmountntfs](www.ubuntuguide.org/#mountunmountntfs) is great and i used it but to write you need some program called capture or captive or something. Hope this helps

---

### Post by jingo811 on 2005-08-28
Tnx for all your help I think that I know what to study up on now! 
I went the **EDWINA**-way so now I can access: floppy and CD-rom drives with ease.
> 1Gb is not a very large partition for Ubuntu - I think that about 3Gb is recommended.And I was considering installing Ubuntu on my old **i486 (270 Mb)**  :? If everything goes well on my brand new PC.
Well, it's actually 2 Gb (/home) and 1 Gb (/swap).  But I have 1 Gb to play with, besides I made it so small just to experiment, not sure yet that Ubuntu will ever handle all my routines that I do in Windows.

**4.** How do I determine if my login account is root or not?
B'coz I shouldn't use root account for daily routine work for the sake of security right?

---

### Post by racecat on 2005-08-28
In Ubuntu, your login account password is the root password. It is rather odd, but it's one less password to remember. When you loaded the system, the same password was applied to your user name and root, or superuser. When you logged in with that username and password, you do not have root permissions. That is until you enter the passwword where prompted for superuser permission, like the example in my earlier post.

Hope this helps. Good luck and have fun.
Bill

---

