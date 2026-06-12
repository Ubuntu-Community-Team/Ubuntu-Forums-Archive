---
title: "Asolute NEW to linux - Need help on installation"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Ionix on 2006-10-26
Hi people.

I am totally new to Linux. I am so used to the comfort of Windows GUI type of OS. But I will like to try and learn to use Ubuntu as my startup to linux please kindly aid me.

I have encounter some problem during my installation. I am currently installing Ubuntu Server on Windows Virtual PC Program.

I encounter this problem when I am trying to install Ubuntu Server.

Here is a screenshot of what happen after I select "Install to Hard Disk"

[IMG]http://sg.geocities.com/legendary616/screenshot.jpg[/IMG]

Please kindly teach me step by step on how to remedy the problem. Thanks in advance, help is appreciated.

---

### Post by magicfab on 2006-10-27
See:
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=unable+to+locate+RDSP](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=unable+to+locate+RDSP)

---

### Post by Ionix on 2006-10-27
:confused: :confused: :confused: :confused: :confused: :confused: 

Actually the google link comes back to ubuntu forum on another unanswered post regarding RDSP..
[http://ubuntuforums.org/showthread.php?t=267568](http://ubuntuforums.org/showthread.php?t=267568)

---

### Post by Ionix on 2006-10-27
Sorry help please... Cause I am seeing this thread keep pushing to the next page. I am getting worried. Mind a helping hand?

---

### Post by xtacocorex on 2006-10-27
I had this problem when I tried to install in MS Virtual PC. I was trying to install just for fun, but when the error hit, I realized that VMWare is probably a better virtualization program than MS Virtual PC.

There are numerous how-to's on Ubuntu in VMServer, which is free:
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

This is a how-to to put Ubuntu (Edgy Knot 3) on VMServer in XP:
[http://blandname.com/2006/09/26/install-ubuntu-edgy-eft-knot-3-on-vmware-server-with-ease/](http://blandname.com/2006/09/26/install-ubuntu-edgy-eft-knot-3-on-vmware-server-with-ease/)
This should apply to the release version of Edgy and I'm sure will work for Dapper.

---

### Post by Rackerz on 2006-10-27
Use VMWare, not Microsoft Virtual PC.

---

### Post by to4i on 2006-10-27
That's right. Use Microsoft only with Microsoft software :)

---

### Post by Ionix on 2006-10-27
Thanks all of your help is appreciated. Thanks again, I'll try out the VMWare.

---

### Post by kvonb on 2006-10-27
You can boot your main system from the Ubuntu CD, it is a "live" CD, which means that it will actually run a fully fledged, working copy of Ubuntu without installing it or messing with your system in any way.

This way you can get the feel of Ubuntu Linux and then decide whether you want to go further and do an install.

Regards,

Kev :)

---

### Post by Ionix on 2006-10-27
Ya... I had tried the live CD before. Actually I am intending to try Ubuntu Server now, that's the reason i used virtual PC

---

### Post by jd65pl on 2006-10-27
> **magicfab said:**
> See:
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=unable+to+locate+RDSP](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=unable+to+locate+RDSP)

It may be an idea to keep in mind who your audience is when posting, a begginer may not find a link to google so useful.

---

### Post by kvonb on 2006-10-27
WARNING WARNING WARNING humour follows......

Well there's your problem.......(see attached image)

Step-by-step guide on how to fix it:

1) Open a "command prompt" and type in "fdisk"
2) Delete ALL NTFS and Windows partitions, use your MS Windows CD as a frisbee (CAUTION: the dog might complain about the taste though, and it could be poisonous)
3) Place Ubuntu Edgy Eft CD in CD drive and boot
4) Install Edgy
5) Feel the peace man!



Keep smiling, Kev :D

---

### Post by Ionix on 2006-10-27
Hey come'mon... It's dangerous even to post the "humour" post and encourage people to fdisk.

You'll never know that there are beginners that dont know what is fdisk for. They might just format the system. Please restrain from posting such comment on threads, especially beginners... lol.

Well guys thanks the VMWare work like charm. I am currently running the emulated ubuntu desktop and I am posting this post through ubuntu firefox. I love ubuntu...!!! yeah... but I believe to continue to learn ubuntu I'll need more from help from the community. Thanks in advance.

---

