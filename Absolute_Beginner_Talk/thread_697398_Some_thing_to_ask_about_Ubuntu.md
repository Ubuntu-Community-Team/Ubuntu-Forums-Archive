---
title: "Some thing to ask about Ubuntu"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-02-15
Hi to all.
2day i install Ubuntu desktop edition 7.10.
I really impressed by the installation process,how easy and easy it was.
No headache like windows.

So to the main points now:
I am going to ask some thing old and may be some expert will say "its already psted here".
I install ubtuntu and sit in front of it for a while to move aorund.
i want to know some things from experts,Hope they will guide newbie.

1- I am a programmer using PHP,mysql,apache(XAMMP) in windows before,
how can i install this package in ubuntu.

2- Is there any antivirus software for ubuntu,Is it secure from web attacks.

3- I want to make 3 partition on 160GB HD while installing Ubuntu,how could i do that.

4- If i want to install a software from USB.How could i use terminal properly for that software.OR i have to copy it to HD.

5- i was trying to run video file.i cant open it,saying "No proper format found".file format was .DAT .how could i install a pacakge like K-Lite(windows) to have every format in ubuntu.

Main thing i forgot to mention is i have no internet connection on that PC.

Hope some one will guide me.
Thanks in advacne.

---

### Post by kesman on 2008-02-15
You will need a working internet connection to be able to get updates and software for your ubuntu.
Almost all software you will ever need is found from applications -> add/remove programs. Just select "all available applications" from the drop-down list from the top-right corner, and search for apache, php, mysql, whatever you need.
Ubuntu automatically downloads and installs these software from Internet, place called a repository, which contains thousands of applications that are supported by the ubuntu community, and designed to work with your version of ubuntu. Any other method of installing applications may cause problems, and without internet connection, it's very difficult to install nearly anything in your box.

For the partition, when you insert your ubuntu cd in, and boot up your pc, it launches the Lice session, in which you may install the "real" system. During the installation, it asks you how you would like to partition your disks. You can there create partitions as you like.

---

### Post by kpkeerthi on 2008-02-15
While more responses pour in... spend some time reading

[http://www.ibm.com/developerworks/linux/library/l-roadmap.html](http://www.ibm.com/developerworks/linux/library/l-roadmap.html)
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by talsemgeest on 2008-02-15
1 have no idea.
2 No antivirus software is needed as linux is built around security and has no known viruses.
3 To make partitions boot off the live cd and go to system>administration>Partition editor.
4 In linux all devices are mounted somewhere in the filesystem, so you shouldn't have to copy anything.
5 It depends what video player you are trying to open it in.

---

### Post by jan quark on 2008-02-15
> 1- I am a programmer using PHP,mysql,apache(XAMMP) in windows before,
how can i install this package in ubuntu.

go to system > administration > synaptic

and type into the search field the application you want to install

make sure you have enabled all the sources in 
system > administration > software sources


> 2- Is there any antivirus software for ubuntu,Is it secure from web attacks.

you do not need and anti virus software in linux :) there are a handfull of viruses and the updates are too fast that any could damage your system, furthermore no application cannot run on your system without your permission

so use the resources in a better way


> 3- I want to make 3 partition on 160GB HD while installing Ubuntu,how could i do that.


during the ubuntu instalation you have to choose the manual partition option

see here
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

> 
4- If i want to install a software from USB.How could i use terminal properly for that software.OR i have to copy it to HD.

you can access and mount usb drives in ubuntu without problems


> 5- i was trying to run video file.i cant open it,saying "No proper format found".file format was .DAT .how could i install a pacakge like K-Lite(windows) to have every format in ubuntu.

Main thing i forgot to mention is i have no internet connection on that PC.


ouch without internet it will be fun to install applications because many programs have dependencies which are installed with them 

hmm let me think

---

### Post by oedha on 2008-02-15
1. you can search on application - Add/Remove
2. yes,...there is AV but no need to use it...since...this is linux
3. maybe you have to check:==> [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
4. what software ? we can install from *.deb or *.tar.gz and it can be done from usb. And linux is different kind of installation since you have to pay attention to the dependencies.....not a big single file
5. you need all gstreamers or ubuntu-restricted-extras to play all media files

---

### Post by hyper_ch on 2008-02-15
> **mmarif4u said:**
> 1- I am a programmer using PHP,mysql,apache(XAMMP) in windows before, how can i install this package in ubuntu.
Those are multiple packages.

> **mmarif4u said:**
> 
2- Is there any antivirus software for ubuntu,Is it secure from web attacks.
No AV needed.

> **mmarif4u said:**
> 
3- I want to make 3 partition on 160GB HD while installing Ubuntu,how could i do that.
Select manual partitioning

> **mmarif4u said:**
> 
4- If i want to install a software from USB.How could i use terminal properly for that software.OR i have to copy it to HD.
sudo dpkg -i package.deb

---

### Post by sigge on 2008-02-15
> **mmarif4u said:**
> 
1- I am a programmer using PHP,mysql,apache(XAMMP) in windows before,
how can i install this package in ubuntu.
2- Is there any antivirus software for ubuntu,Is it secure from web attacks.
3- I want to make 3 partition on 160GB HD while installing Ubuntu,how could i do that.
4- If i want to install a software from USB.How could i use terminal properly for that software.OR i have to copy it to HD.
5- i was trying to run video file.i cant open it,saying "No proper format found".file format was .DAT .how could i install a pacakge like K-Lite(windows) to have every format in ubuntu.
1: ```
sudo apt-get install lamp
```
2: Yes. And the coolest one is ClamAV. Look for it in synaptic if you wish...
3: Manual Partitioning gives full freedom during install. It's also fairly easy
4: Don't. It's fully possible, but gives you trouble down the road.
5: You should move the computer fysically to an internet connection, and fully install it while connected. Get all updates and all apps and such that you need, then disconnect and move the box back where you want it. this sounds stupid, but will likely be a lot less hassle than the usb alternative... :)

---

### Post by Trail on 2008-02-15
By the way, the Ubuntu server edition can "pre-install" a LAMP combo by itself. The server edition does not include a GUI, thought, but you can install it with "sudo apt-get install [k]ubuntu-dekstop, but you normally need internet connection for that (maybe you can set it to read from a desktop edition CD, haven't tried).

In any case, installing LAMP should not be hard at all, but the configuration will, of course, require some work.

---

### Post by Buffalo Soldier on 2008-02-15
Generally you have the, Official Resource:
- [https://help.ubuntu.com/7.10/](https://help.ubuntu.com/7.10/)

Unofficial Resources:
- [https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)
- [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)
- [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
- [http://doc.gwos.org/doku.php/doc:ubuntu](http://doc.gwos.org/doku.php/doc:ubuntu)

There are many more out there, but those are the ones that I regularly go to. Now, for the specific questions...

> 1- I am a programmer using PHP,mysql,apache(XAMMP) in windows before, how can i install this package in ubuntu.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

> 2- Is there any antivirus software for ubuntu,Is it secure from web attacks.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

> 3- I want to make 3 partition on 160GB HD while installing Ubuntu,how could i do that.

[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)
[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

> 4- If i want to install a software from USB.How could i use terminal properly for that software.OR i have to copy it to HD.

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

> 5- i was trying to run video file.i cant open it,saying "No proper format found".file format was .DAT .how could i install a pacakge like K-Lite(windows) to have every format in ubuntu.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> Main thing i forgot to mention is i have no internet connection on that PC.

[https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by mister_pink on 2008-02-15
> **mmarif4u said:**
> 
2- Is there any antivirus software for ubuntu,Is it secure from web attacks.
...
Main thing i forgot to mention is i have no internet connection on that PC.

Just thought I ought to answer this question the obvious way: it's extremely secure against web attacks whilst not attached to the web! :)

---

### Post by mmarif4u on 2008-02-15
I really appreciate all the members here for thier replies.
Thanks you again.

I find all the doc and links very useful.

@Mister_pink
> it's extremely secure against web attacks whilst not attached to the web!

HAHA,you are right.but i am going to install it on my office PC,where i have internet.I ask this question,because now on PC which i install Ubuntu i dont have internet access.

"ONE LAST Q"
i have window Xp on my PC,while installing Ubuntu can i format all drives and then change the format from ntfs to ext3 OR ext2.

---

### Post by kesman on 2008-02-15
Yeah, but you should know that this erases ALL data from the disks.

---

### Post by mmarif4u on 2008-02-15
Thank you for reply.
Yeh i know that it will remove all the data.i will make backup of my data before doing this.

---

### Post by rug77 on 2008-02-15
It may be better to buy a new disk for the machine and install Ubuntu on that.  This means that you can still access all the data you had.  You won't miss any 'vital' applications from your XP machine, and you can then migrate the data you need across more slowly - making sure you have all you need.  Once you're completely happy with Ubuntu, remove the XP and format the disk for Ubuntu to use.

I know that whenever I've formatted disks I always seem to miss something in the backup process ...  or I can't read old emails with the new system ... whatever.

Disks are cheap.

Matt

---

### Post by talsemgeest on 2008-02-15
> **mister_pink said:**
> Just thought I ought to answer this question the obvious way: it's extremely secure against web attacks whilst not attached to the web! :)
Theres always the sneakernet!

---

