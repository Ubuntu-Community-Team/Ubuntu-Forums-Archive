---
title: "Help me install a redhat/suse .bin package"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by maxxum on 2007-07-12
I have bought a software that the makers support only for Redhat and SUSE. I wish to install it on ubuntu (edgy). It is a .bin file that I am supposed to simply change permissions and run as executable. However it fails since ubuntu does not know rpm etc. can anyone help me convert it or get libraries etc so that I don't have to install redhat on this machine..

When I run the binary file, I get this: 
./install.sh: line 164: rpm: command not found

Now I can't even get to the install.sh to be able to look at it and possibly change it. Its all hidden in the .bin file I guess.

---

### Post by zvacet on 2007-07-12
In synaptic install **alien**.Then type in terminal

```
sudo alien package.rpm
```

 package.rpm is exact name of file you want to convert.

---

### Post by maxxum on 2007-07-12
Thanks, but I do not have a rpm package. I have a .bin file that has everything hidden inside it, it seems. It runs as a script and the rpm comes up.  There is also an install.sh that runs and tries to install the rpm, but obviously fails.

---

### Post by Hendrixski on 2007-07-12
it's probably an archive ... so try opening it with archive manager  (right click on it and try the "extract" option).

You mentioned that you bought this software.  Was the company courteous enough to provide a manual for how to compile it yourself?

---

### Post by Hendrixski on 2007-07-12
you have googled this right?

Heres a video to help you install a .bin in Ubuntu
[http://www.youtube.com/watch?v=E8VmernM4qM](http://www.youtube.com/watch?v=E8VmernM4qM)

I just googled for "ubuntu .bin files"

---

### Post by GMachine_24 on 2007-07-12
Once again kill me for asking a simple perhaps lame question, but WHAT IS THE NAME OF THIS MYSTICAL PROGRAM?

Does it have a name? If so, can you tell us what the name is?

And . . . since this is a .bin file I don't think alien will work... as I believe that is for converting rpm files to deb files.

What you need to do is change the permissions on the .bin file to make it executable:

user@computer:~$ chmod a+x yourmysteryprogram.bin

You will more than likely need to be root to run this change so in that case:

user@computer:~$ sudo chmod a+x yourmysteryprogram.bin
password: xxxxyourpasswordxxxx

For example: Java for Linux can be downloaded in a couple formats but I've always used the .bin file and followed the instructions listed here:

[http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)


You should search around if you need more instruction than that. I could do it ... but searching and learning are part of the Linux way.

If you need to know more about 'chmod' then at a command prompt type in

"man chmod | more"

without the quotations. It will explain the a+x modifier and a lot more.




Re: .bin files:

What is BIN files? BIN files is one of CD/DVD image formats. BIN file is a binary copy of an entire CDs/DVDs disc. BIN file contain ALL the data stored on the original disc including not only its files and folders but also its system-specifics information, for examples, bootable information, volume, volume attributes and any other system-specific data. Actually, BIN image file is not a collection of files or folders but is an exact duplicate of the raw data of the original disc, sector by sector.

MagicISO is also a BIN extractor. MagicISO allows the users to open/edit/extract bin files. Just like processing ISO image file. and MagicISO also has ability to burn BIN file to CD-R/RW. If you are willing,  you can convert BIN file to standard ISO image file.


the above taken from [http://www.magiciso.com/tutorials/miso-whatsimage.htm](http://www.magiciso.com/tutorials/miso-whatsimage.htm)

Ok, and ONE MORE link [http://linux.die.net/man/1/alien](http://linux.die.net/man/1/alien) from Linux Man pages re: alien

in which it states:

"DESCRIPTION 
alien is a program that converts between Redhat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats. If you want to use a package from another linux distribution than the one you have installed on your system, you can use alien to convert it to your preferred package format and install it. It also supports LSB packages."


good luck.

--gm

---

