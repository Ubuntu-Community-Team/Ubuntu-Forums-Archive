---
title: "Not Possible to Use CD in Apt-Get After Upgrade?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by charbo on 2007-07-30
Hello all,

After upgrading the system (6.06 Server edition), I lost network connection. (Well, this is another big unresolved issue. [http://ubuntuforums.org/showthread.php?t=504827]("http://ubuntuforums.org/showthread.php?t=504827")) So, I would like to install some software from the install CD-ROM.  

When I issue the command sudo apt-get install build-essential, for instance, it tries to go out and look at all the sources listed on the /etc/apt/sources.list, and errors out.  Obviously, I would like apt-get to only look at the CD-ROM.  Is it possible, after the system had been upgraded through the internet?  If so, do I need to comment out other resources in the sources.list file?

Thank you for your help in advance,

Sadanori

---

### Post by jw5801 on 2007-07-30
Insert the install CD, then go to: System > Administration > Software Sources, and there's a section there for enabling the CD as a source. At least there is in Feisty. I'm sure there is in 6.06 but it might be called something different.

---

### Post by eldepeche on 2007-07-30
Do you have the CD for the release you're now using?

---

### Post by charbo on 2007-07-31
Yes, I have the CD.  

I could not do the "System > Administration > Software Sources", because the server does not have the X running.  But, there is a command line tool, that does the same: apt-cdrom add.

In this case the CDROM is already enabled.

---

### Post by eldepeche on 2007-07-31
You could try commenting out the internet repositories for the time being.

Did you remember to run "apt-get update"?

One issue you might run into is that the version of some package on the cd would require a specific version of some other package that has already been upgraded, and you might have a long string of downgrades to get something working. 

In this case, it might be easier to use [APTonCD](http://aptoncd.sourceforge.net/).


(Just trying to list everything I can think of that might be helpful.)

---

### Post by charbo on 2007-08-01
Thank you for your input.

I do not want to comment out the repositories, though I also thought that it may work.

Yes, I did run the apt-get update, but it fails.  I think it is precisely the issue that you are mentioning, where the database of the packages are already more recent than the CD, and having the inconsistency there.

APTonCD would probably be a solution.  I do not have the X windows on my machine, so I might not be able to do so for this time.  But I will certainly keep it in mind for the future.

Thank you very much for your support.

Sadanori

---

