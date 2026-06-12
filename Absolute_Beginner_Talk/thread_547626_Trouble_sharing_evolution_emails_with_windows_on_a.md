---
title: "Trouble sharing evolution emails with windows on a FAT32 partition"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by castawaybcn on 2007-09-10
Hi there,
I was trying to change the default location of my evolution messages, tasks... in order to access the same files in windows and ubuntu. I know it may not be the neatest trick ever, but there's certain programs that, for the time being, won't allow me to completely remove windows from my pcs.

I've unsuccesfuly looked for documentation over the internet on the matter. Perhaps I could have done better searches, but trust me I have tried for a few days now.

After reading a bit on the subject I decided to make a try by moving the 'mail' folder on /home/MyUserName/.evolution/ to my desktop and create a link to it. It worked just fine, so I thought that would be an easy way to do it.

Next step was reproducing the trick, but this time I tried moving the mail folder onto a FAT32 partition and could not. The error message I got from ubuntu was:
[SIZE="1"]Error "Invalid parameters" while copying "anyofthefileslistebelow".[/SIZE]

I thought perhaps evolution was locking some of the files but it didn't seem to be the case since when I tried copying the same folder from windows I got a similar error message:
[SIZE="1"]"Can't copy _home_MyUserName_: The file name, folder or volume label is not valid"[/SIZE]

Since some of the files where copied and some where not I looked for the ones that could not:
[SIZE="1"].evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#._23evolution_Junk

.evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#._23evolution_Trash

.evolution/mail/config/.evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#Drafts

.evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#Inbox

.evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#Inbox_I_P14

.evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#Inbox_Vivendes

.evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#Outbox

.evolution/mail/config/et-expanded-mbox:_home_MyUserName_.evolution_mail_local#Sent



.evolution/mail/views/current_view-mbox:_home_MyUserName_.evolution_mail_local#Inbox.xml

.evolution/mail/views/current_view-mbox:_home_MyUserName_.evolution_mail_local#Inbox_I_P14.xml

.evolution/mail/views/current_wide_view-mbox:_home_MyUserName_.evolution_mail_local#._23evolution_Trash.xml

.evolution/mail/views/current_wide_view-mbox:_home_MyUserName_.evolution_mail_local#._23evolution_Trash.xml

.evolution/mail/views/current_wide_view-mbox:_home_MyUserName_.evolution_mail_local#Inbox.xml

.evolution/mail/views/custom_view-mbox:_home_MyUserName_.evolution_mail_local#Inbox.xml

.evolution/mail/views/custom_view-mbox:_home_MyUserName_.evolution_mail_local#Inbox_I_P14.xml

.evolution/mail/views/custom_wide_view-mbox:_home_MyUserName_.evolution_mail_local#._23evolution_Trash.xml

.evolution/mail/views/custom_wide_view-mbox:_home_MyUserName_.evolution_mail_local#Inbox.xml

[/SIZE]
I have tried in both my desktop and laptop with the same results.

My OSs details are the following (let me know if you need further details):
Desktop:
[SIZE="1"]	MS WinXP H (in spanish) on a NTFS partition. I have Ext2IFS_1_10c installed which allows me to access my ext3 partitions
	Ubuntu FF 7.04 (in us english, how do I change it to GB btw?)[/SIZE]
Laptop:
[SIZE="1"]	MS WinXP Pro (in spanish) on a NTFS partition. I have Ext2IFS_1_10c installed which allows me to access my ext3 partitions
	Ubuntu FF 7.04 (in us english, how do I change it to GB btw?) with ntfs-3g installed[/SIZE]

This the first time this is happenig to me, I have previously opened and saved files from either Ubuntu or Windows without any problem at all on that same partition. As you will understand this is obviously a major inconvenience, and I wouldn't like this happening to more sensible files. Could this be a problem caused by having the operating systems in two different languages? fstab settings perhaps?

Any help would be highly appreciated. It does not need to be exactly the path I am following as long as it provides some light on how to share the same emails in windows and ubuntu.

Thanks a lot in advance
PS Previous to everything I explained above I gathered information from the following links, please refrain from suggesting them ;)
[http://shellter.sourceforge.net/evolution/](http://shellter.sourceforge.net/evolution/) (evolution for windows, which I didn't install yet)
[ http://www.gnome.org/projects/evolution/]( http://www.gnome.org/projects/evolution/)  (homepage for the gnome evolution project)
[ http://www.go-evolution.org/FAQ]( http://www.go-evolution.org/FAQ)  (evolution FAQ, I got the information of where all evolution files are stored)
[ http://ubuntuforums.org/showthread.php?t=274560]( http://ubuntuforums.org/showthread.php?t=274560)  (rather old and unresolved post where someone was trying just the same thing, the only one I found)

---

### Post by anaconda on 2007-09-10
I have done the same with thunderbird in the past. (I didn't even know that there is evolution for windows)

And it worked.

So I suggest you try it with thunderbird.

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

---

### Post by castawaybcn on 2007-09-10
Thanks but I didn't choose evolution at random. And Thunderbird is not an option for me, I'm afraid. 
However, even if I followed the instructions in the link you provide I guess I would be having the problem: copying the files. 
You just provided the right answer, but not for my question ;)
thanks anyway

---

### Post by anaconda on 2007-09-11
This doesn't look like a valid fat32 filename to me:
et-expanded-mbox:_home_MyUserName_.evolution_mail_local#._23ev olution_Trash

could it be the "#"

Have you tried to rename it to something simpler and then making a symbolic link to that. (You can have the name of the link to be the orginal name..)
 
You could also try ext3 filesystem and use fs-driver in windows to access it.

---

### Post by castawaybcn on 2007-09-11
excellent! will give it a try during the day and will let you know if it worked out ;)
Stupid question: a symbolic link is what you create when dragging a file with middle mouse button and then choose "create link"? I'm rather new to linux as you can see...
and another for the road: what advantage would it be in having ext3 instead of FAT32?
thanks

---

### Post by castawaybcn on 2007-09-11
well I seem to have changed the default directories to the FAT32 partition, but so far I just tried it in linux, so I still have to check if sharing with windows will work. Looks promissing though!!
I still don't know of the advantage of ext3 over fat32 though.

Thanks a bunch

---

### Post by mlentink on 2007-09-11
> **castawaybcn said:**
> I still don't know of the advantage of ext3 over fat32 though.

ext3 is a more advanced, journaling, file system. FAT32 is more rudimentary and has some limits, such as that your files cannot be larger than 4GB

---

### Post by castawaybcn on 2007-09-11
well, I guess a symbolic link is not what I tried since evolution overwrote all of them and replaced them with the original files...
One step back :(
I will give it a further try using some symbolic links code creation I found on this forum.
In the meantime any tips are more than welcome.

---

### Post by hyper_ch on 2007-09-11
Why don't you use the ext3 partition and make it available in windows? --> [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by castawaybcn on 2007-09-12
hyper_ch, what you say makes a lot of sense. And I already have the latest Ext2IFS installed.
But the thing is I am the kind of guy that likes messing around with things -otherwise I would have never considered installin gnu/linux- and having my own files where I want (never used My Documents folder in windows). Most of all I find quite convenient having important files in a partition other than the one the OS is. I could format the partition I want to use to ext3 in my new laptop quite easily, but it would be a great pain having to do so on my desktop pc.
I will give symlinks a try and let you know what happened.

Thanks

---

### Post by hyper_ch on 2007-09-12
I just think fat32 causes too much trouble compared to installing the ext2/3 drivers.

---

### Post by castawaybcn on 2007-09-12
it is not about installing it, I already mentioned I had it installed before posting. The trouble comes to keeping all links to the files I already have in my FAT32 partition.
what is the trouble FAT32 would cause, btw? you may even convince me finally, just now that I managed to symlink all the files in evolution ;)

---

### Post by hyper_ch on 2007-09-13
Hmm, limited disk capacity, limited file size (up to 4 GB), no journaling....

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

