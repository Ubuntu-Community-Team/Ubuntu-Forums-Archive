---
title: "Printer driver load problem"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Jimmy McKellar on 2007-06-21
Hi

I am running Ubuntu 7.04 and trying to install a Samsung driver for model SCX-4100.

Not easy!  I downloaded a file from:

[http://www.samsung.com/uk/support/productsupport/download/FileView.aspx?cttfileid=214860&type=&typecode=300600&subtype=&subtypecode=300601&cmssubtypecode=&model=SCX-4100&filetype=DR&language=](http://www.samsung.com/uk/support/productsupport/download/FileView.aspx?cttfileid=214860&type=&typecode=300600&subtype=&subtypecode=300601&cmssubtypecode=&model=SCX-4100&filetype=DR&language=)

With the name:

 	 20070425141808453_UnifiedLinuxDriver.tar.gz

Then I think I managed to get it to an area /dev  (I needed a root password to get it here and used the command line to cp it there.

I then tried to extract it  from "graphical"? (windows) view and got the following error:

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

Now I am lost - where do I go from here.  Do I have to use a command line?  Can I do it from the desktop?

Regards
Jimmy

---

### Post by Jimmy McKellar on 2007-06-22
> **Jimmy McKellar said:**
> Hi

I am running Ubuntu 7.04 and trying to install a Samsung driver for model SCX-4100.

Not easy!  I downloaded a file from:

[http://www.samsung.com/uk/support/productsupport/download/FileView.aspx?cttfileid=214860&type=&typecode=300600&subtype=&subtypecode=300601&cmssubtypecode=&model=SCX-4100&filetype=DR&language=](http://www.samsung.com/uk/support/productsupport/download/FileView.aspx?cttfileid=214860&type=&typecode=300600&subtype=&subtypecode=300601&cmssubtypecode=&model=SCX-4100&filetype=DR&language=)

With the name:

 	 20070425141808453_UnifiedLinuxDriver.tar.gz

Then I think I managed to get it to an area /dev  (I needed a root password to get it here and used the command line to cp it there.

I then tried to extract it  from "graphical"? (windows) view and got the following error:

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

Now I am lost - where do I go from here.  Do I have to use a command line?  Can I do it from the desktop?

Regards
Jimmy

Jimmy

I have cracked it.  I discovered the /cdroot dir/folder on my Desktop (note the capital "D") but was unable to run it (no permissions)  so I investigated and gave it all the read/write permissions - still no joy as it still said I had no permissions.  

I then went to Terminal and logged on as SU and used this command:

/home/jimmy/Desktop/cdroot/autorun 

This did not work at first as although I had turned the printer on I had not noticed it was still physically connected to the other PC (Note - try simple things first!)

I have printed!

If I can supply any other information to help others - just ask.

Regards
Jimmy

---

### Post by darren1270 on 2007-06-22
> **Jimmy McKellar said:**
> 
This did not work at first as although I had turned the printer on I had not noticed it was still physically connected to the other PC (Note - try simple things first!)

Congrats on being able to print.... I like to follow the KISS method of doing things... Keep It Simple Stupid.... it has pretty much worked when I get calls from customers or employees that say things like my sound is not working... 1 question I ask is are your speakers turned on....LOL

Have a nice day!

Darren

---

### Post by Jimmy McKellar on 2007-06-23
> **darren1270 said:**
> Congrats on being able to print.... I like to follow the KISS method of doing things... Keep It Simple Stupid.... it has pretty much worked when I get calls from customers or employees that say things like my sound is not working... 1 question I ask is are your speakers turned on....LOL

Have a nice day!

Darren

Jimmy

I think I deserve that - I will bear it in mind just the same.

Regards
Jimmy

---

### Post by 1oki on 2007-06-27
Ok I know this thread is old, but here goes. I used this howto to install my network printer in the past. Samsung SCX4100. It worked fine... I had a system failure and had to reinstall. Now my printer is not working... I go to print a test page and it just hangs there.   see picture.... any suggestions?

---

### Post by 1oki on 2007-06-27
nevermind I fixed it... used the SMB connection and its all honky dorie

---

