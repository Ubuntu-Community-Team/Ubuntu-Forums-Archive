---
title: "How Do I Install Files For Wireless Connection"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by bfitzsimons on 2006-10-12
I have some files for wireless connection that I have downloaded onto another iMac in the office. These were burned at slow speed to a CD and copied to my Ubuntu Desktop.

 My hardware is: 
 Apple iMac with 1GHz PowerPC G4 and 768 MB DDR SDRAM using dual boot: MacOSX 10.2.8 and Ubuntu 6.06 LTS;
 Apple Airport Extreme Base Station using Controller Broadcom BCM4306;
 I have wireless connection under the MacOS boot but not under the Ubuntu boot.

 At Terminal, the comand $ ls Desktop, results in:
 bcm43xx-20060125 [this is a folder with files in it], 
 bcm43xx-fwcutterorig [this is a folder with files in it], 
 bcm43xx-fwcutter-005 [this is folder with files in it], 
 bcmwls.sys [this is a file], 
 wl_apsta.0 [this is a file]

 I have tried at Terminal the command $ sudo apt-get install bcm43xx-fwcutter, but this results in: 
 Reading package lists ... Done
 Building dependency tree ... Done
 E: Couldn't find package bcm43xx-fwcutter

 I have tried variations on the path to the folder (e.g. Desktop/<folder_name_here>) and variations on the folder name (e.g. just bcm43xx-fwcutter, also bcm43xx-fwcutterorig) - all give the same result.

In another Thread I followed a reference to: [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)
and at Terminal entered the following commands with the results (->) as shown:
$ cd Desktop/bcm43xx-fwcutter-005
$ ls -> results in a list of files in that folder = bcm43xx-fwcutter.1, fwcutter.c, fwcutter.h, fwcutter_list.h, md5.c, md5.h, makefile, readme, and another folder svn which has more files in it.
$ ./configure -> no such file or directory
$ make -> command not found ... at this point, I even tried $ ./makefile -> command not found

How do I install these folders and files? From the info found on other threads, I believe that these files, once installed, will allow me to hookup to the internet on the Ubuntu boot.

---

### Post by PriceChild on 2006-10-12
You might like to follow this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

(section 1.2)

---

### Post by podunk on 2006-10-12
That package is in the repositories.
System
Administration
Synaptic Package manager

click the search button and type in the program. Right click and chose “Mark for install”

You may need to add the other repositories, see this page for how to do it:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I don't know if that help your wifi - but it will install the package. :-)

---

### Post by bfitzsimons on 2006-10-12
To PriceChild and Podunk:

Thanks for replying to me so quick.  It has taken me a little time to check on the info you each noted.  Here's what I found out:

1st To PriceChild:
Thanks for the link.  I actually had read it under a previous Thread and bookmarked it.  I went ahead and double checked the steps as follows:
Section 1.2: The result to $ lspci -v had too much info.  I used a variation of this command that narrowed the info down to Broadcom since it is the controller on the machine ... $ lspci | grep Broadcom -> resulted in this: 0001:10:12.0 Net controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller ( rev 02);

Section 1.2.1 Using the menu Applications, Accessories, File Browser, Search button I entered "ndiswrapper" and, later,  "wifi-radar" -> resulted in nothing being show => no conflicts to worry about;

Section 1.2.2.1 I had already downloaded and copied to the Ubuntu Desktop the file wl_apsta.o - this is noted in my original posting.  I checked under the menu System, Administration, Software Properties to make sure my Universe Repositories were enabled - they were. The command $ sudo apt-get install bcm43xx-fwcutter -> still gives the results noted in my original posting: "E: Couldn't find package ...".  When I do a search under the File Browser, Search button for anything bcm43xx all the different files and folders are displayed.

Now to Podunk:
Thanks for the link. I have it bookmarked to read some other things that are noted on that website. As to your suggestion, Synaptic Package, Search button does not show any package by the name bcm43xxx... or by any variation of the name. This seems to be the problem.  The files and folders are there and can be displayed under File Browser, but are not viewed as packages and thus cannot be installed by apt-get or aptitude.  In addition, when I read the "Install Software" and "Extra Repositories" tabs of that website, I get the distinct feeling that apt-get and aptitude are for DOWNLOADING and installing.  My problem is I can't get to the Internet under the Ubuntu boot to do any downloading.  I am stuck downloading on another machine, burning to CD, and copying to the Ubuntu Desktop - with the result that the downloads are viewed as files and folders and not packages.

It appears to be quite a little "Catch 22" problem.  Either I need to find a way to turn them back into packages for use by apt-get or aptitude OR I need a way of installing files and folders at the Terminal.  Hence my original question: How do I install files?  Which then takes me to the other problem I noted in my original post: the command $ make -> results in command not found !!  Any idea why that is happening ?

If you have any other suggestions or links - keep them coming !! I am willing to try anything to master this.

---

### Post by bfitzsimons on 2006-10-12
Follow up to Podunk:

I just came across the following quote from the link that you gave me.  It's at the end of the Install Software tab ( [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) ):

"There's also Checkinstall: Once checkinstall is installed, instead of typing sudo make install you type sudo checkinstall -D and the program creates a .deb file which is then installed. This makes removing any program compiled from source extremely easy. For more details see the Wiki: [https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall). "

I will check on this tonight and see what comes of it...

Thanks again to PriceChild and Podunk for your replies so far.  If there is anything else you can think of let me know.

---

### Post by bfitzsimons on 2006-10-13
Final Post To This Thread:

I did the follow up with CheckInstall - looked good but the command $ sudo apt-get install checkinstall -> "E. Couldn't find package ..."

The instructions "Installing from source" at [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) looked useful but they required build-essential and I got the same "E. Couldn't find package .. " result.

I have finally relooked at how I was downloading. I went back to the original site where I did my initial downloading: [http://packages.ubuntu.com](http://packages.ubuntu.com)

Under the "Search" Section, typed in "bcm43xx", clicked on the link for "powerpc" and tried each of the mirrors for North America until I reached the last one "ubuntu.secs.oakland.edu".  This finally downloaded a .deb package for bcm43xx.  Evidently, I had originally downloading .tar files, unpacking them, and copying the unpacked files to CD.  Anyway, I now did the same for further research for "checkinstall" and "build-essenial".  These .deb packages were then burned to CD and copied to the Ubuntu Desktop.

The instructions found under the Section 2. Reader Comments, the 12th entry of: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)  were followed AND IT WORKED !!

---

