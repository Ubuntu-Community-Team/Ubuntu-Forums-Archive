---
title: "Cannot run ./configure"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by tjasko12 on 2007-09-23
Hi guys,
I have a VMware-workstation-6.0.1-55017.i386.tar.gz file on my desktop now. I am planning on installing Win-XP on it. 

I have to run the command(s):
1. tar fxz VMware-workstation-6.0.1-55017.i386.tar.gz
2. cd vmware-distrib)
4) ./configure --This is where the error occurs

If can get past the error, then I can run these.
5) Run make
6) Run sudo make install

When I run ./configure, it says there is no file or directory
tj@tj-laptop:~$ tar fxz /home/tj/Desktop/VMware-workstation-6.0.1-55017.i386.tar.gz
tj@tj-laptop:~$ cd vmware-distrib
tj@tj-laptop:~/vmware-distrib$ ./configure
bash: ./configure: No such file or directory

Can you guys help me?

To bad they don't supply a DEB file... :mad:


Thanks,

Taylor

---

### Post by Maestro23 on 2007-09-23
Need build-essential installed.

> sudo apt-get install build-essential

---

### Post by tjasko12 on 2007-09-23
Ok. I will try that.

Thanks,

---

### Post by paulr on 2007-09-23
I don't think VMWare is installed via the usual ./configure ; make ; make install.  It didn't in VMWare 5.

There is a script in the directory called something like vmware-install which does all this semi automatically. Have a look for a file called README or INSTALL to view in a text editor in the archive.

---

### Post by Maestro23 on 2007-09-23
> **paulr said:**
> I don't think VMWare is installed via the usual ./configure ; make ; make install.  It didn't in VMWare 5.

There is a script in the directory called something like vmware-install which does all this semi automatically. Have a look for a file called README or INSTALL to view in a text editor in the archive.

Good call.  I just assumed the OP was following the README/INSTALL doc. ;)

---

### Post by tjasko12 on 2007-09-23
I'll look for it..

All I see is vmware-install.pl.

How do I run it?

---

### Post by tjasko12 on 2007-09-23
Looks like I need to use something called Perl.

[http://www.fileinfo.net/extension/pl](http://www.fileinfo.net/extension/pl)

Tell me how please. :)

---

### Post by tjasko12 on 2007-09-23
Bump.

Anyone?

---

### Post by odiseo77 on 2007-09-23
I'm not sure, but maybe ***perl vmware-install.pl*** is the way to do it? (you need to have perl installed first, so ***sudo apt-get install perl*** ).

Anyway, is highly recommended that you read the README and INSTALL files, since you'll probably get dependency issues.

---

### Post by tjasko12 on 2007-09-23
There is no readme, or install files....

---

### Post by tjasko12 on 2007-09-23
It looks like Ubuntu already has Perl on it. So, how do I install it?
Why can't there be a debian installer file... That would make this a whole lot easier.

---

### Post by tjasko12 on 2007-09-23
I did it.

You need to run sudo ./vmware-install.pl.

Thanks anyways,

Taylor

---

### Post by pheeror on 2007-09-23
Installing with ```
make install
``` was _not_ recommanded even in linux prehistoric age. And now in age of linux trying to be as stupid friendly as possible is still _very_ bad practice. DONT DO IT! 

There is awesome build system in every linux distribution and you still need to abuse it. 
If you ignore build system of you distribution and finally persuade vmware workstation to compile and install, you end up with one big mess instead of superb clean system you have now.

---

### Post by Maestro23 on 2007-09-23
> **tjasko12 said:**
> I did it.

You need to run sudo ./vmware-install.pl.

Thanks anyways,

Taylor

Good deal.  See what happens when you read the docs. :smile:

Make sure to mark this thread SOLVED.

---

### Post by tjasko12 on 2007-09-23
Actually, I didn't read any docs. Just used common linux sense...

---

### Post by Balt603 on 2007-09-28
OK, I"m going to post in this thread as my issue seems to be quite similar.

As the OP, trying to install VMware, following the instruction at [http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

As the OP, get to trying to run the vmware-install.pl, gives me the error "sudo: ./vmware-instal.pl: command not found"

I opened up the perl script, and found the first line is "#!/usr/bin/perl -w", so to be safe went to check this out and found that I had no /usr/bin/perl at all. So I went into Synaptic to see whether perl was fully installed and found that perl, perl-base and perl-modules were all installed. As is build-essential.

I am assuming that this means that perl is not functioning on my machine, but I'm not good enough a linux user to go fumbling around in the depths of my install...

Any help would be greatly appreciated.

---

### Post by odiseo77 on 2007-09-28
Weird. If you have all those packages installed on your machine, you should already have perl installed (try ***whereis perl*** to see if you already have it). Did you make sure you're on the directory where the vmware-install.pl script is when you run 'sudo ./vmware-install.pl'? (try ***cd /path/to/vmware-install.pl*** before running the script)

EDIT: I also noticed that you seem to be running 'sudo ./vmware-instal.pl' and the proper command would be ***sudo ./vmware-install.pl***, I guess (note the difference between 'instal' and install')

---

### Post by Balt603 on 2007-09-29
I would have sworn that I tried that file name many times and didn't mis-spell it, but when I just tried then it ran and VMware is now installed. So I guess I'm a fool :-) In my defence, it was after midnight...

I did what you suggested with the "whereis perl" and it showed a path that included /etc/bin/perl, but when I checked, it still isn't there. 

Seeing as the script ran though, I think I can assume perl is functioning anyway, so I'm not going to complain. 

Thanks for the help. That includes everyone else who's written howtos and tips that got a baby linux user up and running. This distro and community are damn fine!

---

