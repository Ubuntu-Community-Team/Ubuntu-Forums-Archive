---
title: "Install tar.gz rpm"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by cumptrnrd on 2006-05-09
How do you install a program that you downloaded?

For example, "AdobeReader_enu-7.0.5-1.i386.tar.gz"?

And can you install rpms in Ubuntu?

---

### Post by Koybe on 2006-05-09
It depends on the program. Most of the time instructions are in a INSTALL file in the .tar.gz. So you need to uncompress it and have a look on what's inside. Just double-click it... or go to a tarminal and use
```
tar zxf your_file.tar.gz
```

[https://wiki.ubuntu.com/rpm?highlight=%28rpm%29](https://wiki.ubuntu.com/rpm?highlight=%28rpm%29) : Here's a howto for the rpms. Anyway I think the better way is to get it trought the ubuntu (or debian) package management. What are you looking for that you find on rpm and not on deb?

---

### Post by aysiu on 2006-05-09
I don't see why you wouldn't just [enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo apt-get update
sudo apt-get install acroread
```

For more on installing software, read these two links:
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Koybe on 2006-05-09
Maybe i'm wrong but i think acroread is not the same version and is older. Anyway I'm using evince ;)

---

### Post by deadgobby on 2006-05-09
And can you install rpms in Ubuntu?[/QUOTE]

If you want to install a RPM on you Ubie system.  If you install the rpm package on you desk top. Open you terminal and type in cd Desktop. Then type ls. (LS) in lower caps. This will list what is on you desktop. Now type in you terminal
*sudo alien packagename.rpm*
The system will now make a rpm package into a debian. Now you can type into your term.
*sudo dpkg -i packagename.deb*
 You may notice that the rpm package now has a key lock next to the icon. To delete that lock icon type in your term.
*sudo chown system_username /location_of_files_or_folders*
Now you may delete the folder. Before you install any program on you Ubie system. Check your Synaptic.

TAR files from source
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)
Once agian check Synaptic before installing programs. If you do not meet any depends when installing from source or rpm.You will not be able to install the program. Synaptic will be your best bet first cause it will install any depends packs and libs.

---

### Post by aysiu on 2006-05-09
> **Koybe]Maybe i'm wrong but i think acroread is not the same version and is older. Anyway I'm using evince  said:**
>  Acroread is version 7.0.1 instead of 7.0.5: [quote]Package acroread

    * warty (text): Adobe Acrobat Reader: Portable Document Format file viewer [multiverse]
      5.09-0.0: i386
    * hoary (text): Adobe Acrobat Reader: Portable Document Format file viewer [multiverse]
      5.10-0.2: i386
    * hoary-backports (text): Adobe Acrobat Reader: Portable Document Format file viewer [multiverse]
      7.0-0.9~hoary1: i386
    * breezy (text): Adobe Acrobat Reader: Portable Document Format file viewer [multiverse]
      7.0.1-0.0.ubuntu1: i386
    * dapper (text): Adobe Acrobat Reader: Portable Document Format file viewer [multiverse]
      7.0.1-0.0.ubuntu1: i386 I always assume beginners don't know the easy way to install software unless they specifically say, "I know Acrobat Reader is available in the repositories, but I'm trying to install version 7.0.5 because I need ____________ feature. How do I install this .tar.gz?"

I just visited the Adobe website, and I don't see any references to features 7.0.5 has that 7.0.1 doesn't have.

---

### Post by nanotube on 2006-05-09
aysiu: yea, good assumptions. :)

cumptrnrd: for a good tutorial on the various ways to install software on ubuntu, check out the second link in my sig.

---

### Post by dfmalh on 2008-05-15
Hi, I have to install the Japanese font pack for Adobe Reader 8.1

This is the file, FontPack81_jpn_i486-linux.tar.gz ,but I have no idea how to go about adding it. I tried the fololwing:

tar zxf FontPack81_jpn_i486-linux.tar.gz 

I "think" something happened, but I do not know what. I still can't open Japanese PDF.

Any help would be greatly appreciated.

---

### Post by oninjao on 2008-05-15
tar zxf your_file.tar.gz
./configure 
make 
make install

or once untared if theres a file labeled install  double click and select run in terminal it should talk u through

---

### Post by dfmalh on 2008-05-16
Hi oninjao, thanks for your reply, I still have problems. Will explain:

tar zxf FontPack81_jpn_i486-linux.tar.gz 

- Works fine and unpack the font pack to dir "JPNKIT"

./configure

- I get the following output: bash: ./configure: No such file or directory

make

- I get the following output: make: *** No targets specified and no makefile found.  Stop.

make install

- I get the following output: make: *** No rule to make target `install'.  Stop.



or once untared if theres a file labeled install double click and select run in terminal it should talk u through

- I did this as well. I get to the point where it wants to know: Enter the location where you installed the Adobe Reader [/opt] 
- This is not the right location... 
- I found this link: [https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto](https://help.ubuntu.com/community/JapaneseInAdobeReaderHowto)
- my setup is in the /opt dir, so I don't know really what to do.

I also found a post about the language pack install, so I will post there aswell.

thanks for your help!

---

### Post by dfmalh on 2008-05-16
Solved it. thanks for the previous help.

---

