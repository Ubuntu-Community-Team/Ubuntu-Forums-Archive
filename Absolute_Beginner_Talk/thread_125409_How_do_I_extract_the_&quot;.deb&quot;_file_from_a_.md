---
title: "How do I extract the &quot;.deb&quot; file from a &quot;.tar.gz&quot; file?"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-03
I have downloaded a ".tar.gz" file containing a Linux LAN driver for My Intel PERL Motherboard.

Internet Source:
[http://www.intel.com/design/motherbd/rl/rl_drive.htm#suse](http://www.intel.com/design/motherbd/rl/rl_drive.htm#suse)

The File looks like this:
LAN: Linux Driver [NETWORK_1.3_NLD9_SP2_X86_64.TAR.GZ]

What sudo command do I type to create the ".deb" file from the above ".tar.gz" file?

And, after I install the ".deb" file with:

sudo dpkg -i /directory/of/driver/name_of_driver.deb

How do I verify that the Driver was installed successfully?

Thank you for your time!
Please be descriptive because I am new in Ubuntu.

---

### Post by krusbjorn on 2006-02-03
tar.gz-files are merely compressed archives, like zip- or rar-files. To extract the content of the file, type "tar -xzf filename.tar.gz"

If you get no error message when installing the deb, all is well :)

---

### Post by warleggon on 2006-02-03
There is a little app called checkinstall that will create a .deb file for you.

sudo apt-get install checkinstall

As far as creating the .deb file, the short answer is, that if you can get to the point with configuring the app ('./configure') that you are ready to 'make' the app, after you run make then run:

sudo checkinstall

from the directory that you are running make. IF all goes well you will find a .deb file in that same direcory.

---

### Post by dvarsam on 2006-02-04
So basically, if I get it right, the app "Checkinstall" is within Ubuntu Linux.
I do not have to make a separate installation, do I?

Then, to create the ".deb" file, I type:

        sudo apt-get install checkinstall

But in the above command, there is no filename!
How is sudo going to understand, on which filename it has to work with?
Do I have to be on the same Directory the ".tar.gz" lies, to type the sudo command?

So, basically, to change ".tar.gz" into ".deb", I type:

        sudo apt-get install checkinstall
        ./configure
        make
        run
        sudo checkinstall

And, then I install the ".deb" file with:

        sudo dpkg -i /directory/of/driver/name_of_driver.deb

And, if I get NO error message when installing the ".deb" file, it means that the Driver was installed successfully…

---

### Post by nik on 2006-02-04
[QUOTE=dvarsam]So basically, if I get it right, the app "Checkinstall" is within Ubuntu Linux.
I do not have to make a separate installation, do I?

Then, to create the ".deb" file, I type:

        sudo apt-get install checkinstall

[/QUOTE]
Not quite... This one is to install checkinstall with, and you only have to do this once. I think you got the rest... :)

---

### Post by engla on 2006-02-04
No, there are many misunderstandings.

First: your .tar.gz file is a compressed **archive of source code **

You want a .deb file of a binary product

To get from source to binary product we have to do the dreaded *compilation* of source code. 

In theory this is simple.
You extract the source code (in italic is filenames you have to find out which they are for youself)
tar xfvz *source-archive-file*.tar.gz
You enter the new directory
cd *source-archive-directory*
and you compile it with 
[B]./configure
make
sudo make install[/B]


That would compile and install it for you.
Making a deb file is great, as it simplifies uninstallation. It doesn't really affect installation, other than you don't have to do all the ./configure and make again.
So to make a .deb file, you instead of **sudo make install** do **sudo checkinstall** This creates and simultaneously installs the driver for you, if no errors are given.


And note what the line 'sudo apt-get install checkinstall' means: This is used to install the software called 'checkinstall', because we need to use it. This only needs to be done once ever on each computer, but you need to do it before using it to make a deb file.

---

