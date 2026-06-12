---
title: "Complete noob here.. have a few questions"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by keas on 2007-01-14
I recently installed Ubuntu.  The instalation went well but there are a few poiblems I have encounted.

1.)  My hard drive is partitoned into two parts, 10gig and 65gig, I formated my 10gig partition to install Ubuntu and that seems to of went well but when i want to acess my other partition witch it named hda5 I get this message "You do not have the permissions necessary to view the contents of "hda5"  When I go to the propeties and to the "Permissions" tab it says that the owner is root.  So I tried to log on as root but it said I can not log into root.  Basically my question is how do I acess the files on the other partition.

2.)  I had to install using a old 5.10 disc I had.  I rember reading that it was possible to upgrade from diffrent versions without haveing to go through much hassle.  Would it be possible for someone to point me in the direction of a page that could provide more info on this?

3.) Whats a good media player to use?  I really don't want anything fancy it just needs to be able to play music files over a network (all my music files are stored on another computer)

Thanks in advance for any help you all can provide.

---

### Post by riven0 on 2007-01-14
1) How about browsing through nautilus? Can you do that?:

> gksudo nautilus

Otherwise, someone more knowledgeable will have to help you on that.

2) If you do **sudo update-manager -c -d** you should get the option to upgrade your distribution.

3) I've heard Amarok and Banshee are good. But you may want to try Exaile, too.

---

### Post by Fahuadai on 2007-01-14
3)  About media player over a network share:
I use Amarok (local files only) and absolutely love it.  [This]("http://amarok.kde.org/wiki/Dynamic_Collection") page has some information about Amarok using a dynamic collection which has support for accessing shared files with NFS and SMB. (NFS for Linux and SMB for accessing windows shares)

do a search for Samba if in doubt how to get windows shares working.
I find this a really helpful guide: [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Hope this helps

---

### Post by mykalreborn on 2007-01-14
1. do you by any chance have a ntfs partition? of so you should visit this thread to help you out:[link]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs")
you can't login as root because of safety issues. you can really mess up your computer, especially if you don't know all that much of what's happening.
3.i think some install links should be good.
amarok: Applications>Add/remove programs>multimedia>amarok
exile:[link for dapper]("http://www.exaile.org/files/exaile_0.2.8_i386dapper.deb") or [link for edgy]("http://www.exaile.org/files/exaile_0.2.8_i386.deb")
Songbird is a pretty cool media player:[link]("http://ubuntuforums.org/showthread.php?t=238328&highlight=install+songbird")
also, you should check this out :[link for beginners]("http://www.ubuntux.org/")

---

### Post by keas on 2007-01-14
Thanks to everyone who replied.  I think I got it all sorted out.

---

### Post by keas on 2007-01-14
Seems I spoke to soon.  I can't seem to acess the files on my Unbuntu computer with my other computer that has windows installed.  It gives me a error saying that I might not have premission and that The network path was not found.

---

### Post by riven0 on 2007-01-14
This is after you've set up Samba? 

BTW, to read and write NTFS files [look at this guide]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read+write").

---

### Post by old_geekster on 2007-01-14
Here is a link to a guide that I used to install "Ubuntu 6.10", yesterday:  [http://www.pcmech.com/show/os/903/](http://www.pcmech.com/show/os/903/).  I worked like a charm.

Hope it helps!

---

