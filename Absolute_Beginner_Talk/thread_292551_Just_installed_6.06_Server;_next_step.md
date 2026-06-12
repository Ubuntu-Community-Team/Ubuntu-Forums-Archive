---
title: "Just installed 6.06 Server; next step?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by MikeSchinkel on 2006-11-04
Hi all! 

I'm looking for help getting my Ubuntu 6.06 server up and working as a LAMP server. Thanks in advance for any help you may be able to provide.

First, I'm a total n00b to Linux. I've been working with Windows Server (NT, 2000, 2003) for many, years (and DOS before that) and am reasonably capable. I'm more of a application and database developer than a network admin, so I struggle through the networking and administration part.

I decided to make the jump to Linux and set up a server at home so I could build and test web apps before uploading them to my hosted web site. Based upon the postitive things that Scott Hanselmen said about Ubuntu on his podcast at [http://www.hanselminutes.com/]("http://www.hanselminutes.com/") I chose Ubuntu, and here I am!

I decided to install Ubuntu 6.06 server running on WMWare. I chose the "Install a LAMP Server" option, and found [this article]("http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html") on DebianAdmin.com.  It was a good article and was great help, although he didn't mention a few steps and I had to really struggle through them, but that's ok.  

I now have Ubuntu 6.06 server up and running within VMWare, and here is the config I chose:

[LIST]
[*]320Mb RAM
[*]4Gb Hard Disk configured as:
[LIST]
[*]100Mb - /boot  (as per the article)
[*]1Gb   - /
[*]2.5Gb - /home
[*]640Mb - swap   (the article didn't explain this part!)
[/LIST]
[/LIST]

I have managed to stumble through learning how to chmod the the /etc/network/interfaces and /etc/resolv.conf files (also not discussed in the article) and how to use vi to edit them and then restart networking.  From one of my other VMs running Windows I am able to ping the IP address successfully.  

Here are some questions I have about what I've done so far to make sure I have done them correctly:

[LIST]
[*]chmod - I used 777 for those two files. Is that okay?
[*]vi - How do I get it to let me type ":" to get a prompt without inserting into the text?  I'm been typing F1 then colon, but that doesn't seem like it would be the standard way, or is it?
[*]resolv.conf - I learned you need to include a "server yourdomain.com" in the file, but I'm unsure of what "yourdomain.com" should be. I have a Windows Server Active Directory set up on my home network and assuming my AD is named "Foo.local" then I included "server Foo.local" in resolv.conf.  Is that correct?
[/LIST]

My second set of questions are:

[LIST]
[*]Samba - What do I need to do to get this machine to join my Windows AD so I can read/write files across my network (or should I even worry about it?)
[*]GNOME - How do I set it up (or for a server, should I?)  OTOH, some things are so much easier with a GUI.
[*]Apache - How do I go about configuring it?
[*]MySQL - How do I go about configuring it?
[*]CPanel - I use CPanel at my ISP and I know that it is a commercial product that I don't plan to buy for my home test machine but is there a free equivalent for my purposes so that when I'm developing on my Windows XP computer?  Yes, I expect someone might say "Do everything in Linux" but I'm currently a lot more comfortable and hence a lot more productive on Windows. Maybe I'll change to working in Linux eventually, but unfortunately I have to make a living and bill clients for real work so I don't have all the time in the world to learn this, even though I would like to. :)
[/LIST]

If you have specific tutorials on each of these you can point me to, that would be great. I've googled for these but there is such an overwhelming about of results that are not appropriate for my context from google's index that I got discouraged. I am hoping your experience can help me get to this machine up and ready to start building web apps sooner than later.

Again, many thanks in advance.

---

### Post by CatKiller on 2006-11-04
Welcome to the community. You might want to read these pages before you chmod any other files:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

I can't really answer any of your other questions, but there were some threads recently on lightweight server installs with GUI for when you want it. Possibly in the Desktop Environments forum?

Good luck.

---

### Post by MikeSchinkel on 2006-11-04
CatKiller: Thanks for the help you could give!

---

### Post by K.Mandla on 2006-11-04
Cheers, and welcome to the community! :D

Here are some Howtos that are in the FAQs and Howtos section, as well as the wiki. It's possible they don't directly apply to what you have in mind, but you're the best judge of that. ;) I'm guessing there are plenty of tips for configuring them, too.

Apache2 with Tomcat5: [http://www.ubuntuforums.org/showthread.php?t=219985](http://www.ubuntuforums.org/showthread.php?t=219985)

Samba peer-to-peer with Windows: [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

Setting up a LAMP server (MySQL + Apache + PHP): [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

LAMP servers for noobs: [http://www.ubuntuforums.org/showthread.php?t=223805](http://www.ubuntuforums.org/showthread.php?t=223805)

Again, I don't know if these would be of much help, but there's plenty to work with. I'm sure there will be little nuggets of wisdom here and there.

As far as I know, the only downside to using Gnome on a server is the drag on system resources. Your machine ends up minding the GUI while it fulfills its server responsibilities. I hear that equates to slow response times, etc. 

I seem to remember someone saying a GUI was a security risk too, although I don't know enough to say if that's true or not. 

Setting up the Gnome desktop for your server is as easy as *sudo aptitude install ubuntu-desktop*.

One last note: For a swap partition I usually use a space equivalent to the amount of memory in the machine. Back in the old days when I used Windows I used to need about double that amount, but it's a *very, very* rare occasion when any of my machines *start* swapping out, let alone fill a swap space. Just my $0.02 on that one, though. ...

---

### Post by MikeSchinkel on 2006-11-04
> **K.Mandla said:**
> Cheers, and welcome to the community! :D

Thanks for your help!  I'll check out your references and see if they solve my problem.

> **K.Mandla said:**
> Again, I don't know if these would be of much help, but there's plenty to work with.

Tell me about it!  Actually the problem I've had is not that there isn't enough to work with but instead narrowing it down to something that is relevent!!! That can take tons of time, as you may know. Frankly with all the different distros in Linux and all the different apps, I don't know how you guys all keep up. :)

> **K.Mandla said:**
> As far as I know, the only downside to using Gnome on a server is the drag on system resources. Your machine ends up minding the GUI while it fulfills its server responsibilities. I hear that equates to slow response times, etc.

For a web test machine, that's not a problem, and it will make it easier for me to learn the system if I can use CUI tools. BTW, any idea how much RAM GNOME requires?

> **K.Mandla said:**
> I seem to remember someone saying a GUI was a security risk too, although I don't know enough to say if that's true or not. 
Not a problem here as I don't intend to expose it to the internet.

> **K.Mandla said:**
> One last note: For a swap partition I usually use a space equivalent to the amount of memory in the machine. Back in the old days when I used Windows I used to need about double that amount, but it's a *very, very* rare occasion when any of my machines *start* swapping out, let alone fill a swap space. Just my $0.02 on that one, though. ...

I chose double because I saw several articles suggesting double and also some threads where people said that if Linux was locking up to increase the dize of the swap file to double.  I'd rather waste the space as I have it than have to deal with lockups.

> **K.Mandla said:**
> Setting up the Gnome desktop for your server is as easy as *sudo aptitude install ubuntu-desktop*. 

Well I tried that, but it **ran out of disk space.  <Sigh>**   

I guess what I need to do is:

[list=1]
[*]Delete the 2.5Gb partition, 
[*]Expand the 1Gb root "/" partition to 3.5G 
[*]Create another 4Gb VMware hard disk
[*]Configure the new hard disk as "/home", and 
[*]Re-run the "install ubuntu-desktop"
[/list]
Does that make sense?

If so, I have no idea how to do this except for the very last step.  Any chance you could list off the command I'd need to use to make these changes? 

Thanks again in advance.

---

### Post by 3rdalbum on 2006-11-04
Rather than apt-getting the ubuntu-desktop package, you could always try the gnome-core package.

```
sudo aptitude install gnome-core
```

However I don't know how much space this takes, or how much is left on your partitions.

---

### Post by MikeSchinkel on 2006-11-04
> **3rdalbum said:**
> Rather than apt-getting the ubuntu-desktop package, you could always try the gnome-core package.

```
sudo aptitude install gnome-core
```

However I don't know how much space this takes, or how much is left on your partitions.

Thanks for the suggestion.  Any idea how to clean up the failed install of the ubuntu-desktop package? I assume it didn't clean up after it failed, but I'm such a Linux n00b that I can't even figure out how to see how much disk space is available! :(

---

### Post by MikeSchinkel on 2006-11-06
Any help?

---

### Post by moffa on 2006-11-06
To see how much space you have left run "df -h".
Try running "sudo apt-get install -f" to fix installation problems. If that doesn't work try removing or reinstalling ubuntu-desktop.  You can reinstall using "sudo apt-get install --reinstall ubuntu-desktop"

---

### Post by BackInTimeMan on 2006-11-06
> **MikeSchinkel said:**
> Thanks for the suggestion.  Any idea how to clean up the failed install of the ubuntu-desktop package? I assume it didn't clean up after it failed, but I'm such a Linux n00b that I can't even figure out how to see how much disk space is available! :(

If the suggestion by moffa to clean up the ubuntu-desktop failed install didn't work out, you can remove/uninstall it with:

```
sudo aptitude remove ubuntu-desktop
```

Using "purge" instead of "remove" will delete all the config and data files too.

I don't know how much space the gnome-core takes up or what it gives you because I've never installed it on it's own, but I've just installed the Ubuntu server using the LAMP setup option and then added the ubuntu-desktop and found, similaly to you, that it takes up too much room on the small (2.98 GB) hard drive I'm using, ie. it fills it up!.

What I've done is to install the xubuntu-desktop which is pretty small and lean and leaves me a good amount of hard drive space. Then I installed Webmin to admin the server as I don't yet have the CLI skills to do it.

What I have now is a single partition of 2.82 GB with about 800 MB free space and a swap partition of 165 MB. This is on a machine with 256 MB RAM and a 1.4 GHz CPU. It's al running fine, quite snappy in fact.

---

### Post by MikeSchinkel on 2006-11-06
Thanks again for the replies.

> **BackInTimeMan said:**
> If the suggestion by moffa to clean up the ubuntu-desktop failed install didn't work out, you can remove/uninstall it with:

```
sudo aptitude remove ubuntu-desktop
```

Using "purge" instead of "remove" will delete all the config and data files too.

So if I do this:
```
sudo aptitude purge ubuntu-desktop
```
It will remove config & data files? Just for the desktop, or for more?

BTW, it looks like the install filled up my "/dev/sda2", whatever that is?

> **BackInTimeMan said:**
> 
What I've done is to install the xubuntu-desktop which is pretty small and lean and leaves me a good amount of hard drive space.
Sounds like a good idea. In a nutshell, what's the difference between the ubuntu and xubuntu?  And would I install using this?

```
sudo aptitude install xubuntu-desktop
```

And, may I ask, what exactly is aptitude and how does it work? Does it contact ubuntu.com and use web services to download things? Just trying to get my head around things as understanding them helps me fix my own problems w/o having to ask for help all the time.

> **BackInTimeMan said:**
> Then I installed Webmin to admin the server as I don't yet have the CLI skills to do it.

How would I install Webmin?

> **BackInTimeMan said:**
> What I have now is a single partition of 2.82 GB with about 800 MB free space and a swap partition of 165 MB. This is on a machine with 256 MB RAM and a 1.4 GHz CPU. It's al running fine, quite snappy in fact.

Well, you definitely wouldn't get "snappy" on that machine using Windows Server! (which is all I've used up until now, for the past 10 years...)

P.S. Since I'm doing this on a VMware virtual machine that has two each mirrored 70Gb and 500Gb hard disks, I'm thinking maybe I should just start over?

---

### Post by BackInTimeMan on 2006-11-06
> **MikeSchinkel said:**
> Thanks again for the replies.

> **MikeSchinkel said:**
> So if I do this:

```
sudo aptitude purge ubuntu-desktop
```
It will remove config & data files? Just for the desktop, or for more?

For everything in the ubuntu-desktop package.

> **MikeSchinkel said:**
> BTW, it looks like the install filled up my "/dev/sda2", whatever that is?


That's the partition/drive where you installed it. 

> **MikeSchinkel said:**
> Sounds like a good idea. In a nutshell, what's the difference between the ubuntu and xubuntu?

The desktop environment, Ubuntu uses Gnome and Xubuntu uses Xfce. Xfce is smaller and faster than Gnome.

> **MikeSchinkel said:**
> And would I install using this?

```
sudo aptitude install xubuntu-desktop
```


Yes.

> **MikeSchinkel said:**
> And, may I ask, what exactly is aptitude and how does it work? Does it contact ubuntu.com and use web services to download things? Just trying to get my head around things as understanding them helps me fix my own problems w/o having to ask for help all the time.

Aptitude is a package handling utility similar to apt-get, it is said that it handles dependencies more effectively than apt-get. Here's a link to a page that will explain more:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

This website is an excellent resource for learning about Ubuntu.

> **MikeSchinkel said:**
> How would I install Webmin?

You need to install it with a .deb (a software package for Debian based Linux OS's) from their website as it isn't in the Ubuntu repositories.

[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

You can just double-click on the downloaded file to install it. If the Webmin install package says it needs a particular Perl module, use:

```
sudo aptitude install name-of-package
```

to install it first.

> **MikeSchinkel said:**
> Well, you definitely wouldn't get "snappy" on that machine using Windows Server! (which is all I've used up until now, for the past 10 years...)

Lucky you! :)

> **MikeSchinkel said:**
> P.S. Since I'm doing this on a VMware virtual machine that has two each mirrored 70Gb and 500Gb hard disks, I'm thinking maybe I should just start over?

It's up to you of course, I just uninstalled the ubuntu-desktop and installed the xubuntu one and all is fine.

---

### Post by MikeSchinkel on 2006-11-08
> **BackInTimeMan said:**
> ...
Thanks for the clarification and all the help.

I'm going to try the purge route to see if I can make it work as I can always reinstall if not. A lot of what I'm wanting at this stage is opportunities to learn.  I'll let you know how it worked out.

---

### Post by BackInTimeMan on 2006-11-13
> **MikeSchinkel said:**
> Thanks for the clarification and all the help.

You're welcome.

> I'm going to try the purge route to see if I can make it work as I can always reinstall if not. A lot of what I'm wanting at this stage is opportunities to learn.  I'll let you know how it worked out.

Please do, I'm learning too  :)

---

### Post by Phantom784 on 2006-11-13
I never bothered to get used to using vi.  I'd suggesting using joe, it works pretty much like notepad on windows, except in the console.  You use ctrl key combiniations for commands, and there's even a help menu with ctrl+k then h.

```
sudo aptitude install joe
```

---

### Post by MikeSchinkel on 2006-11-13
So I tried to clean it up, but I ended up accidentally deleting every single file on the disk, Doh! :)  

Not a problem since I was just playing. So I then created an 8Gb drive and partitioned it like so:

[LIST]
[*]100Mb - /root
[*]2.5Gb - /
[*]4.5Gb - /home
[*]1Gb - swap
[/LIST]

Next I installed everything again, and then installed xubunutu.  But it took me FOREVER to find anything that told me how to actually LOAD the shell:

```

exec startxfce4

```

I then went about trying to figure out how to get VMware tools to work, and that took about two hours because I had to end up recompiling them. I wish I could remember all the steps, but unfortunately I don't. Still, it didn't give me what I was expecting which not having to press Ctrl-Alt to get the mouse to access the VMware menus, but no biggie.

Next step is to figure out Samba and installing some web apps like WordPress and Mediawiki, but I have to get back to doing some productive things for a while before I can afford the time to tackle that one.

---

### Post by MikeSchinkel on 2006-11-13
> **Phantom784 said:**
> I never bothered to get used to using vi.  I'd suggesting using joe, it works pretty much like notepad on windows, except in the console.  You use ctrl key combiniations for commands, and there's even a help menu with ctrl+k then h.

```
sudo aptitude install joe
```

Cool, thanks. I'll check out joe!

---

### Post by MikeSchinkel on 2006-11-15
> **Phantom784 said:**
> 
```
sudo aptitude install joe
```

I tried installing joe with that command but it told me:

```
Couldn't find any package whose name or description matched "joe"
```

Any other suggestions?  Thanks in advance.

---

### Post by MikeSchinkel on 2006-11-15
> **MikeSchinkel said:**
> I tried installing joe with that command but it told me:

```
Couldn't find any package whose name or description matched "joe"
```

Any other suggestions?  Thanks in advance.

Okay, I found Joe on sourceforge and downloaded the source to try and compile it, but Xarchiver in Xfce won't let me unarchive it to /usr/src because of permissions problems.  Thus far I've learned to use sudo on the command line, but how do I do the same within Xfce?

---

### Post by zenbuntu on 2006-11-15
I find nano much easier to use than joe/vi:

```
sudo apt-get install nano
```

---

### Post by CatKiller on 2006-11-15
> **MikeSchinkel said:**
> I tried installing joe with that command but it told me:

```
Couldn't find any package whose name or description matched "joe"
```

It's in the [Universe repository]("https://help.ubuntu.com/community/Repositories").

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Personally, I find nano fine for most things, too.

EDIT: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

