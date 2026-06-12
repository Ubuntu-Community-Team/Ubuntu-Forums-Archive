---
title: "[SOLVED] Open Movie Editor"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Ahunt on 2008-01-18
Hi everyone,

Here is an interesting problem. 

I have a bunch of 10 frames per second (fps) ".mov" QuickTime movies that I would like to edit. I thought I had found the best application for the job, Open Movie Editor. It will do everything I need and is easy to download from the Ubuntu Gutsy repositories.

The problem is that the Ubuntu repository version is 0.0.20061221 which is a very old version from December 2006. That version will will only handle 25 fps video. The current version of Open Movie Editor, which is 0.0.20080102,  new this month, apparently will edit 10 fps video, so obviously that is the version I need.

Unfortunately this version is available from the Open Movie Editor website [http://openmovieeditor.sourceforge.net/Downloads](http://openmovieeditor.sourceforge.net/Downloads) only as source code and therefore requires compiling to be installed. That is far beyond my skill level. 

I have searched this forum and also the web in general to see if anyone else has compiled the file for Gutsy Gibbon, but haven't found anyone who has.

I am hoping that someone can offer a useful suggestion on how to get the current version of Open Movie Editor.

Adam

---

### Post by smartboyathome on 2008-01-18
I normally don't recommend cross-distro installation of packages, but it seems that you can download the new version from the debian repos. You should be able to download it from [here]("http://packages.debian.org/sid/i386/openmovieeditor/download"), but I don't know if it will have all its dependancies satisfied.

---

### Post by loell on 2008-01-18
its in the repository

so to install, in the command line just type


```
sudo apt-get install openmovieeditor 
```


PS, tried it a couple of times, but it seems it is still buggy for now or atleast the version that is in gutsy.



--edit **v0.0.20080102** gutsy deb

[http://ubuntuforums.org/attachment.php?attachmentid=56988&d=1200788789]("http://ubuntuforums.org/attachment.php?attachmentid=56988&d=1200788789")

---

### Post by daengbo on 2008-01-19
The version for Debian Sid needs a newer libc6.

---

### Post by Ahunt on 2008-01-19
Hi everyone:

Thanks for all your replies on this subject. I appreciate you taking the time to respond.

I wanted to check with Ioell, who said above that it is in the repositories and to use an app get command to retrieve it. I just wanted to confirm that you are talking about a newer version there and not the same one that is available through the normal add/remove application or Synaptic. 

The current one available through add/remove and also through Synaptic is the older version 0.0.20061221, which is the version I have that won't handle 10 fps video. I am trying to get the current version which is 0.0.20080102 which apparently will handle video speeds other than 25 fps.

Adam

---

### Post by philinux on 2008-01-19
This link is from the site mentioned.

[http://http.us.debian.org/debian/pool/main/o/openmovieeditor/openmovieeditor_0.0.20080102-2_i386.deb](http://http.us.debian.org/debian/pool/main/o/openmovieeditor/openmovieeditor_0.0.20080102-2_i386.deb)

So just click it. Download to desktop.

Then double click the package and the package manager will install it for you correctly.

---

### Post by Ahunt on 2008-01-19
Thanks for your response on this. 

I also received a reply from the developer of Open Movie Editor, Richard Spindler. This may help others so I will repeat it here, copied from:

[http://www.openmovieeditor.org/board/viewtopic.php?id=775](http://www.openmovieeditor.org/board/viewtopic.php?id=775). 

He said:

"Hi,

Open Movie Editor Development happens very fast, and the Distributions are not always up to date, you can find information about how to compile Open Movie Editor for Gutsy here:

[http://propirate.net/oracle/archives/2007/10/19/open-movie-editor-weekly-news-6/](http://propirate.net/oracle/archives/2007/10/19/open-movie-editor-weekly-news-6/)

Cheers
-Richard"

That linked page shows how to get the latest version and how to compile it for Gutsy! I haven't tried it yet but will report back here to complete this post when I do so!

Adam

---

### Post by loell on 2008-01-19
like i said, open movie editor in gutsy is buggy  and naturally is an older version,

and the generic debian build v.0.0.2008  will yield a libc6 dependency.



attached is the deb package for gutsy  **v.0.0.20080102**

---

### Post by Ahunt on 2008-01-19
Thanks for your clarification!

I have the latest version 0.0.20080102 now and have it compiled, I am just working on trying to get it to install properly. I'll give a report here  if/when I get it figured out!

Adam

---

### Post by Ahunt on 2008-01-20
Hi everyone,

Thank you for your patience - I have the problem solved and I thought I would share the solution here for anyone else who would like to have the latest version of Open Movie Editor.

These instructions come from Richard Spindler and are a summary of the discussion that ironed it out at [http://www.openmovieeditor.org/board/viewtopic.php?id=775](http://www.openmovieeditor.org/board/viewtopic.php?id=775)

There is also a description of how to install the latest version at [http://propirate.net/oracle/archives/2007/10/19/open-movie-editor-weekly-news-6/](http://propirate.net/oracle/archives/2007/10/19/open-movie-editor-weekly-news-6/) 

BUT it contains an error that prevents it from working correctly, so don't use that method!

Here is the method that works:

First go to Ubuntu add/remove and install Open Movie Editor. This will get you version 0.0.20061221 which is an old version from December 2006, but it is the only one in the Gutsy repositories as of this date - 20 Jan 08

Once you have OME installed then go to [http://openmovieeditor.sourceforge.net/Downloads](http://openmovieeditor.sourceforge.net/Downloads) and download the latest version. Move it to your Desktop if it ends up elsewhere.

Then go Applications>Accessories>Terminal and cut and paste in the following commands one line at a time. After pasting in a line, hit enter to activate it. When the command has completed executing then cut and paste in the next line, etc.

sudo apt-get build-dep openmovieeditor
tar xzf Desktop/openmovieeditor-0.0.20080102.tar.gz
cd openmovieeditor-0.0.20080102/
./configure --prefix=/usr
make
sudo make install

Please note that if you download a different version than 0.0.20080102 that you will have to change the command to the correct file name!!

Also note that if you don't put the downloaded file on the Desktop then you will have to change the command to designate the actual location of it.

Once the last command is finished running you can open the application: Applications>Sound & Video>Open Movie Editor. If you check Help>About it should indicate version 0.0.20080102.

Adam

PS I wanted to thank everyone who helped out on this forum inquiry, as usual the Ubuntu Forum is full of helpful people! I would also like top thank the developer of Open Movie Editor, Richard Spindler for developing this useful application and also for his patience on his own forum explaining how to get the latest version to beginners like us.

---

### Post by Ahunt on 2008-02-09
Just to complete this story for anyone who wanders across it in the future: After using OME for a while I have written a review of it at [http://web.ncf.ca/adamandruth/ubuntu.html#OME](http://web.ncf.ca/adamandruth/ubuntu.html#OME)

There is also another video editing article that includes includes instructions for upgrading OME versions, too at [http://web.ncf.ca/adamandruth/ubuntu.html#VideoEditing](http://web.ncf.ca/adamandruth/ubuntu.html#VideoEditing)

Hope that is all helpful

---

