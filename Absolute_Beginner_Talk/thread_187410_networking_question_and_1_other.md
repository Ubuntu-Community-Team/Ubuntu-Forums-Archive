---
title: "networking question and 1 other"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-06-02
I am running Ubuntu on a computer at my house. I also have Windows computers connected to the same network. Is there any way that a virus of any sort could travel from my linux machine to my windows machines. The windows machines have firewalls, but the linux does not. According to Ubuntu they don't need them. Any help is appreciated.

Second question.
Where can I insert a cvs code to make it download files. Sorry if this is kinda vague, I am a complete n00b.

---

### Post by Dr. Nick on 2006-06-03
If the virus is in .exe format you should be safe as it cant execute on linux. I cant think of a way that a file could execute on linux and spread to windows. It could be possible but I wouldnt worry about it since it would be rare if possible. It is even less likely if you dnt use samba, in that case the linux machine wont know any shares on the win computers to drop the virus. And I believe that the linux machine has a firewall built in, its just not a applicaition based like teh windows ones that show every program trying to connect.

The 2nd question may require more details

---

### Post by apollyonis on 2006-06-03
The first thing that comes to mind is an email attachment that you save on the Linux machine and send to your Windows machine to execute or view. Unless you're purposely trying to screw up your Windows machine from your Linux box, I don't see any other actual viable venues.

Are you trying to make cvs downloadable and running or...? Descibe a bit more of what you're trying to do. Are you talking about your browser to download files?

---

### Post by Dr. Nick on 2006-06-03
[quote=apollyonis]The first thing that comes to mind is an email attachment that you save on the Linux machine and send to your Windows machine to execute or view. Unless you're purposely trying to screw up your Windows machine from your Linux box, I don't see any other actual viable venues.
 [/quote]

True, If you get a email with a windows virus in linux and save it to a cd or usb and drop it in a windows computer and run it you will get a virus. But thier should be no way for a virus to go from linux to windows "behind the scenes"

---

### Post by tdrusk on 2006-06-03
What I want to do is download DC++ for Linux. EIther that or Valknut. Can someone link me to the package for Valknut or tell me the exact package that I need as far as which OS to pick. Ubuntu is not listed. I have been a Windows user for years and I am pretty good with it, but I do need some help obviously.

For installing DC++ I found [this]("http://www.ubuntuforums.org/showthread.php?t=28378") guide. Am I supposed to download a file before I start entering in 
> $ sudo cvs -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp login
   (leave password blank and hit enter)

$ cvs -z3 -d:pserver:anonymous@cvs.linuxdcpp.berlios.de:/cvsroot/linuxdcpp co linuxdcpp
And where do I enter that in at, the terminal? 

Well I guess Valknut would work. It seems to be the easiest to install. But either way any help is appreciated. Thanks!

---

