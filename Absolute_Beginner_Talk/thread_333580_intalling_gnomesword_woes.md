---
title: "intalling gnomesword woes"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by JLD2509 on 2007-01-07
Hey guys,

I just downloaded and installed ubuntu and got it up and running online just yesterday.  I'm trying to install gnomesword without success.

I first tried manually (before I was online), and at some point in the terminal window, it told me I had some sort of C++ error.


2nd attempt, after I got the computer online, I went through the add/remove menu and I was given the error message that this software conflicts with other software, go to advanced mode?


3rd try, I went through the Synaptic Package Manager and when I tried installing it that way, it gave me this message:  Depends: libsword5c2a (>=1.5.8-7) but it is not installable
I search on the forums and find this thread: 
[http://ubuntuforums.org/showthread.php?t=296020&highlight=gnomesword]("http://ubuntuforums.org/showthread.php?t=296020&highlight=gnomesword")

I follow the advice and go to the link [http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8%2Bb1_i386.deb&md5sum=f5d3d7aa584860d23ed69055af815236&arch=i386&type=main]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8%2Bb1_i386.deb&md5sum=f5d3d7aa584860d23ed69055af815236&arch=i386&type=main")

and I get error 404 for all the mirrors.

Next, I find this site [http://packages.debian.org/stable/gnome/gnomesword]("http://packages.debian.org/stable/gnome/gnomesword")

and try downloading and installing from there.  Upon this attempt, it throws me an error: Dependency is not satisfiable: sword-text



So in short, what does a man have to do to get this application?  Anyone?

Thanks in advance,
Jim

---

### Post by mahy on 2007-01-07
there's apparently some problem with inconsistent package names. Unless they fix it, it's too difficult to install.

---

### Post by JLD2509 on 2007-01-07
So I'm stuck?  There's nothing I can do?

---

### Post by cbkouz on 2007-01-08
You can use BibleTime - it's the same software (except developed for KDE).  It worked just fine for me in GNOME.  Good luck and Godbless.

---

### Post by doobit on 2007-01-08
> **JLD2509 said:**
> So I'm stuck?  There's nothing I can do?

If you use the Ubuntu CE script, the Gnomesword installs easily.

[http://www.whatwouldjesusdownload.com/christianubuntu/2006/11/ubuntu-ce-v20-edgy-features.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/11/ubuntu-ce-v20-edgy-features.html)

---

### Post by chaplanger on 2007-01-08
I ran into the same problem:

If you are seeking to install GnomeSword2 in Ubuntu Edgy Eft you will run into an installation error because currently "Edgy" does not have the files Libsowrd5c2a. I have found only 1 active repository for this file and it is within Ubuntu itself -- follow this link to claim this file:

[http://packages.ubuntu.com/cgi-bin/d...i386&type=main](http://packages.ubuntu.com/cgi-bin/d...i386&type=main)

After installing this, you can then successfully install GnomeSword2.

God Bless!


BTW -- though BibleTime is the "same program" I could not get it to run properly (crashed when attempting to open any of the additional modules).  Don't know if this was because it was set up for KDE or not.

---

### Post by JLD2509 on 2007-01-09
chaplanger, I'd like to explore your solution, but the link is broke.  

Thanks,
Jim

---

### Post by JLD2509 on 2007-01-09
ahh... I found it in this thread.  Got it installed and apparently working. 

[http://www.ubuntuforums.org/showthread.php?t=285641&highlight=gnomesword](http://www.ubuntuforums.org/showthread.php?t=285641&highlight=gnomesword)


Thanks guys,
Jim

---

