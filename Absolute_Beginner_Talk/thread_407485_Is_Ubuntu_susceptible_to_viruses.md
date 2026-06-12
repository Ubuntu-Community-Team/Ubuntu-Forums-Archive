---
title: "Is Ubuntu susceptible to viruses ?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by DrtBikDave on 2007-04-12
Is Ubuntu susceptible to viruses? If so are there any websites that can explain how to be secure. and Lastly If I get a virus in Ubuntu will it corrupt my windows instalation that is on the same hard drive different partition.

---

### Post by garrido on 2007-04-12
Basically: no.

The only way a  virus in ubuntu might affect your windows installation is if you store an infected file in your Linux partitions, for instance, something you got from aMule, and open this file in Windows.  In Ubuntu, you will never have any side effects, but if you access your Linux partitions from Windows and open the file, you will be infected just as if that file was in your Windows partition.

---

### Post by eljalill on 2007-04-12
Ubuntu is not very likely to get viri, for at least two reasons:
Many viri are not written for Linux, but for Windows. If they are an .exe file or so, Linux can simply not open this file that easily.
Secondly, any installations or other changes to the system require superuser (root) rights. Since you are usually looged in as a user, any virus would have to cope with the rights you have... Or would prompt you for the password. This way nothing can really happen without you noticing it.

Furthermore as far as I know, Ubuntu does not have part open by default, which makes it again harder to intrude.

And lastly there are antivirus programs, which you can install, clamav e.g. Just earch synaptics.

And depending on what a virsu does, it could corrupt your windows installation, if you ever do get a virus, But then I think it would have to know, that it is on a Linux system, or just be very destructive, e.g. just erase everything.

Hope this helps!
If you search the fora, there is certainly more on this topic.

---

### Post by Malakia on 2007-04-12
As of right now there are only about 3 linux virii in existence. No Ubuntu isn't susceptible to viruses and you shouldn't have worry about the virii affecting Windows as long as your  using Ubuntu. If you are still paranoid than you can use AVG for linux. Here is the link to install AVG and it even explains it a little better than I can.

[http://doc.gwos.org/index.php/Install_AVG_Anti_Virus]("http://doc.gwos.org/index.php/Install_AVG_Anti_Virus")

---

### Post by Kay The Bantu on 2007-04-12
linux lacks high virus exposure unlike windows since most viruses target ms. but thinking its free from infections would be foolhardy. there are a couple of sites with how tos and even firewalls here are a couple i managed to dig up from google

[www.fs-security.com/]("www.fs-security.com/")
[www.smoothwall.org/]("www.smoothwall.org/")
[www.linuxjournal.com/article/1204]("www.linuxjournal.com/article/1204")
[security.linux.com/security/04/10/11/2030249.shtml?tid=100&tid=35]("security.linux.com/security/04/10/11/2030249.shtml?tid=100&tid=35")


hope this helps

---

### Post by 3rdalbum on 2007-04-12
I'll link you to a website that will illuminate the Linux viruses situation for you.

[http://linuxmafia.com/~rick/skoll/anti-virus.php]("http://linuxmafia.com/~rick/skoll/anti-virus.php")

The answer to your second question is "It's theoretically possible", but it would involve you actually GETTING a Linux virus in the first place. I'd be much more worried about getting a Windows virus that will corrupt your Windows partition.

---

### Post by freebird54 on 2007-04-12
If you want a more in-depth discussion of how hard it is to get a virus to RUN on Linux, let alone catch it try this link:

[http://linuxmafia.com/~rick/faq/index.php?page=virus#virus](http://linuxmafia.com/~rick/faq/index.php?page=virus#virus)

Takes a while to read it all, but a scan through should increase your understanding of the difficulties a virus writer would face - especially in transmission!

---

