---
title: "Sharing /home across multi Linux OS"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-07-06
Hi there

After playing with and enjoying Unbuntu (7.04) multi-booting with WinXP, I am now experimenting adding a third OS - Fedora 7.

Here is how my system (with 2 hard drives) is set up

Drive 1 - NTFS just one partition with WinXP and some files

Drive 2:
Partition 1 - NTFS - nothing on this, but maybe another Win system sometime
Partition 2 - ext3 - /home for my Ubuntu OS with tons of files and documents
Partition 3 - extended with 3 sub-partitions (4,5 and 6 all ext3)
Partition 4 - swap
Partition 5 - / for Ubuntu 
Partition 6 - / for Fedora 7
Partition 7 - not currently used, but planned as space for another Linux system

I loaded Grub for both Ubuntu and Fedora on their respective / partitions.
I think the Grub on drive 1 MBR points to the Ubuntu Grub because that is the menu.lst that includes Win, Ubuntu and Fedora.
Multi boot seems to be working just fine - so I can opt for whichever OS I want at boot time.

Now, here´s my question...

When I first set up this partitioning I planned on giving each Linux OS the same /home partition - i.e. Partition 2 on the second drive. I had read somewhere that having a shared /home for multiple Linux OS meant that they all share the same Settings/Preferences, as well as shared files - and upgrading or installing new OS would not mean having to re-set preferences, bookmarks etc.

So I installed Ubuntu first and all was OK.
But later, when I installed Fedora and selected Partition 2 for /home in Fedora as well, things started to get messy. From Ubuntu I could still access the files on Partition 2 (/home) OK, but from Fedora the /home directories and files were locked (ie read only).  And there were other strange things when using Fedora and trying to access files and directories.

So I decided to re-install Fedora, and this time just left everything in the root (/) on partition 6.
This works fine, but I had to re-setup preferences, bookmarks etc for Fedora.

QUESTION:
Is there a way that I can easily have Ubuntu and Fedora share /home on partition 2 - so the settings/preferences/bookmarks and documents and files are shared with full read-write-execute access from both op systems? Can it be done without having to re-install the OS?

Thanks for any help you can offer.

KiwiPete

---

### Post by bruban on 2007-07-06
Pete,

I suspect that your problem may have been that you had a different userid in both Fedora and Ubuntu.


Before you do any of the following, make sure that you have a backup of your data.


Boot into each distribution in turn, and from a terminal window type in:

grep <your user name> /etc/passwd

you should get something like the following returned:

bruce@zircon:~$ grep bruce /etc/passwd
bruce: x:1000:1000:bruce,,,:/home/bruce:/bin/bash
bruce@zircon:~$

The third field in the response should be your userid, the next field is your group id. Using the example above:

1000:1000


If the userid and group id are not the same in both distributions you will not have write access to the /home file system when mounted from the other distribution.

For reasons I'll cover below, I'd change your Fedora userid and group id to match your Ubuntu one AFTER you have made sure that the user id and group id is not already being used by Fedora. If they're being used, select a pair of numbers unique to both systems.

You can edit /etc/passwd as root directly using vi or similar.



Next mounting your Ubuntu /home in Fedora:

The reason I'd recommend going this way is that your Ubuntu /home is in its own file system and you will be able to mount it separately.


First, backup any files that you have in your Fedora /home as they will not be accessible once the following is done.


In Ubuntu check your fstab file for mount details for /home 

In a terminal type:

grep /home /etc/fstab


I get the following, yours will be different.
 
bruce@zircon:~$ grep /home /etc/fstab
/dev/mapper/raid-home /home           ext3    defaults        0       2
bruce@zircon:~$


In the place of /dev/mapper/raid-home you will probably have something like /dev/hda5


Make a careful note of the details returned. You will need to append this info to your /etc/fstab in Fedora.

 In my case I'm concerned with:

/dev/mapper/raid-home /home           ext3    defaults        0       2


Give this a try. It may help.

Bruce

---

### Post by kosmic on 2007-07-06
To solve this both users (in ubuntu and fedora) MUST have the same UID and GID :)

---

### Post by KiwiPete on 2007-07-06
Thanks for those suggestions, Bruce.

I used the grep <username> /etc/passwd command in Terminal of both Ubuntu and Fedora and as you predicted the user id:group id were different - Ubuntu was 1000:1000, Fedora was 500:500.

So after checking there were no other 1000:1000 entries in the /etc/passwd file in Fedora I changed it to 1000:1000 to match Ubuntu.

I then went back into Ubuntu and typed grep /home/etc/fstab
The result was as follows:

UUID=a78c3048-51f6-450f-ae59-8d84741fcf22 /home ext3 defaults 0 2

I then exited Ubuntu and went to get back into Fedora..

PROBLEM!
I could not log on to Fedora - after entering my username and password, message said something to the effect of /Home could not be accessed and would be ignored.
It then presented the option to Log Off or Continue.
When I chose Continue, another message displayed saying access was denied.

It looks like I may have to re-install Fedora to fix this.
And then next time I&#314; try changing the /etc/passwd file and the /etc/fstab at the same time.
Will that avoid the problem?

Or would you suggest something else?

KiwiPete

---

### Post by bruban on 2007-07-07
Hello Pete,


Sorry for the delay, I've just found your thread among the many posts.

Do you have the ability to log in as root under Fedora, or are you using sudo there as well.

If not, you may well have to reinstall.

If you do, login as root and restore your userid and groupid to 500.



I'm sorry, I haven't used Red Hat derived distributions for about six years. So I can't offer much more help here.

It seems to me that your Fedora installation is using a more sophisticated authentication scheme than is standard on many distributions.

I suspect that Fedora authentication may be occurring via an LDAP directory. There may also be some issues relating to SELinux. I recall reading that Redhat were working with it.

I suggest that you post a similar query on a Fedora Forum to see what comes out. There will probably be a tool that you will need to use to change your IDs.

Good Luck,

Bruce

---

### Post by KiwiPete on 2007-07-08
Thanks Bruce.
No, can't log in as user in Fedora either.
I'll post in one of the Fedora forums and if a solution is found will re-post it in this thread.
Cheers
KiwiPete

---

### Post by CraigInParadise on 2008-06-27
I doubt KiwiPete is still waiting for an answer, but if anyone else is encountering this problem:

At the Fedora login screen, press Ctrl Alt F5 to switch to a non-gui runlevel.  You can then login to root to a console.  

Use usermod and groupmod to change the uid and gid to match Ubuntu.

You'll also need to change ownership of your files in Fedora.  Use chown with the from=owner:group and recursive parameters to change both the owner and group ids on all your files - check the man pages for syntax.  Start at /, not /home or you'll find problems.

---

