---
title: "Printer CUPS, LPR - can't  install Brother MFC-420CN"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-06
I have a Brother MFC-420CN printer that I have over several weeks been trying to figure out how to install.  Supposedly, it is one that should work with Linux.  I downloaded the driver mfc420cnlpr-1.0.2-1.i86.deb and read over the instructions but apparently I am doing something wrong.  There is some mention regarding cups and lpr - I don't understand the merits of either.

Need some background and some help.

Thanks

Carl

---

### Post by yamawho on 2007-05-06
I have the same printer connected to a windows network with RJ45 cable.

I'm looking for help as well ...

---

### Post by yamawho on 2007-05-06
Anyone ?

---

### Post by freebeer on 2007-05-06
Have you treid to follow this HOWTO?  [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

It's not for the same model, but I think the principle is the same.  I followed this and it worked for my Brother MFC3420C (with appropriate changes for drivers, etc.).  It's been a while, so I forget the details.

---

### Post by cwmoser on 2007-05-07
> **freebeer said:**
> Have you treid to follow this HOWTO?  [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

It's not for the same model, but I think the principle is the same.  I followed this and it worked for my Brother MFC3420C (with appropriate changes for drivers, etc.).  It's been a while, so I forget the details.


Thanks.  I used the referenced URL and finally got my Brother MFC-420CN printer working - with a few additional steps too.  A summary of what I did was:


Brother MFC-420CN
---------------------------

Download Printer Drivers from [www.Brother.com](www.Brother.com)

mfc420cnlpr-1.0.2-1.i386.deb
cupswrappermfc420cn_1.0.0-1_i386.deb


Install csh &#8211; this is required:
----------------------------------

sudo aptitude install csh


Install LPR Driver:
-----------------------

TURN PRINTER OFF

sudo mkdir /var/spool/lpd
sudo mkdir  /var/spool/lpd/MFC420CN
sudo dpkg  -i  ./mfc420cnlpr-1.0.2-1.i386.deb


Install the CPUS Wrapper:
---------------------------------------

sudo  ln  -s  /etc/init.d/cupsys /etc/init.d/cups
sudo dpkg  -i  ./cupswrappermfc420cn_1.0.0-1_i386.deb

cp  /usr/share/cups/model/brmfc420cn_cups.ppd   /usr/share/ppd/
ln  -s  /u/share/cups/model/brmfc420cn_cups.ppd  /usr/share/ppd/brmfc210c_cups.ppd
chmod  g+w  /tmp
chmod  o+w  /tmp


TURN PRINTER ON


Final setup and Print Test Page:
-----------------------------------------------

System -> Administration -> Printing

Right-click the MFC210C and click &#8220;Properties&#8221;

    * Connection Tab: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-210C)
    * General Tab: Here I rename 'MFC210C' to 'Brother Printer'. Let's the whole family know the printer they're selecting.
    * Paper Tab: Ensure your local paper size is selected.
    * Advanced Tab: Review the choices and make appropriate adjustments.
    * From any tab: Click "Print a test page" to confirm all works well.

---

### Post by dsmturbo on 2007-06-05
cwmoser, I think you have hit the nail for me. I am running SimplyMepis 64bit and I am a real newbie. I could not follow the instructions on Brother web site, didn't work for me.  I have just followed your excellent how to, and I will check later to see if it printed in house (I am in garage right now, and 420CN is networked)  Yippee, it worked. cwmoser, you Rock. Do you mind if I posted your howto on Mepis forum? There are a couple other people having problems

---

### Post by dsmturbo on 2007-06-05
> **yamawho said:**
> Anyone ?

 yamawho, I notice you also on Mepis forums. I am running 64 bit and was having trouble installing 420CN, but this how to by cwmoser worked for me. My 420CN is networked.

---

### Post by dsmturbo on 2007-06-05
Sorry, I forgot. Have you had luck installing the scanner portion in 64bit?

---

### Post by prevail89 on 2007-10-06
I tried to install the cupswrapper file and it won't download. It says,

:~$ sudo dpkg -i ./cupswrappermfc420cn_1.0.0-1_i386.deb
dpkg: error processing ./cupswrappermfc420cn_1.0.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./cupswrappermfc420cn_1.0.0-1_i386.deb

each time I try.

---

### Post by stixguy on 2007-10-23
> **prevail89 said:**
> I tried to install the cupswrapper file and it won't download. It says,

:~$ sudo dpkg -i ./cupswrappermfc420cn_1.0.0-1_i386.deb
dpkg: error processing ./cupswrappermfc420cn_1.0.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./cupswrappermfc420cn_1.0.0-1_i386.deb

each time I try.

Brother has updated the CUPS wrapper since this how-to was written. If you've downloaded the latest and greatest from the Brother site you'll need to do this:

```
sudo dpkg -i ./cupswrapperMFC420CN-1.0.2-3.i386.deb
```

Make sure you execute the command from the directory that you downloaded the CUPS wrapper to.

Hope this helps!

---

### Post by y0diggity on 2007-10-29
I just wanted to post to say thanks to you folks for your help. I'm an absolute n00b to this (seriously, I don't have a clue what the commands meant that I used) and I was able to get my network-attached MFC-420cn up and running following the directions I found here.

---

### Post by bradleyds75 on 2008-02-08
this Forum helped a ton... thank you!  another forum i was in forgot to help me MKDIR...seems like alot of stuff on ubuntu is similiar to DOS with Cd and DIR and mkdir
stuff that I used to do alot of back in the days of wordperfect 5.1

---

### Post by Jewfro_Macabbi on 2008-02-08
I have this printer working. I've used it on multiple versions of Ubuntu/Debian and Fedora never with much difficulty. 

Here's my install instructions - which assume you've already downloaded the lpr and cups wrapper drivers from brother

sudo dpkg -i --force-all --force-architecture mfc210clpr-1.0.0-1.i386.deb

sudo dpkg -i --force-all --force-architecture cupswrappermfc210c_1.0.0-1_i386.deb

then launch your browser and goto:

[http://localhost:631](http://localhost:631)

for additional configuration - via usb you can print straight away - networked printers require a few additional configuration changes. See here:

[http://solutions.brother.com/linux/sol/printer/linux/cups_network.html](http://solutions.brother.com/linux/sol/printer/linux/cups_network.html)

---

### Post by Lokithor on 2008-04-15
I used **cwmoser**'s excellent directions and installed LPR driver.

However, when I tried to install the cupswrapper, 
I entered the command:  sudo ln -s /etc/init.d/cupsys /etc/init.d/cups  -no problem.
I entered the command:  sudo dpkg -i ./cupswrappermfc420cn-1.0.2-3.i386.deb
and got the following error:

"Setting up cupswrappermfc420cn (1.0.2-3).........  
Touch:  cannot touch '/usr/share/cups/model/brmfc420cn_cups.ppd"  :no such file or directory."

When I went to the /usr/share/cups/ directory there was no "/model" subdirectory.
When I did a search for "brmfc420cn_cups.ppd", there were 0 results.

Can anyone help?   TIA

---

### Post by mbunchj8 on 2008-04-18
Lokithor -

I am having the same error problem with the 420CN.  I cannot find the directory or the .ppd file.  I think when brother changed the CUPS Wrapper and Lpr file some errors are now there.  

Can anyone who has a working lpr and Cupswrapper please post them?  The one's on the Brother website don't seem to work.

Thank you -

---

### Post by mbunchj8 on 2008-04-18
I finally got it to work.  I found that I kept getting an error message about not be able to locate the brmfc420_cups.ppd file/directory.

The way I fixed it and got it to work is before you install the Lpr package and the Cupswrapper do the following:

Plug the printer in and "Turn it OFF"

sudo mkdir /usr/share/cups/model

Once I had created the model directory everything seemed to work.  I was able to install the lpr package using the instructions listed earlier:

sudo dpkg -i --force-all --force-architecture mfc420cnlpr-1.0.2-1.i386.deb

sudo dpkg -i --force-all --force-architecture cupswrapperMFC420CN-1.0.2-3.i386.deb


cp /usr/share/cups/model/brmfc420cn_cups.ppd /usr/share/ppd

Once it all finishes then Turn the Printer On and Print a Test page.

So far it has worked, of course I would run out ink just now so I have not seen the "test" page yet.

I did also install the scanner packages without any errors.

---

