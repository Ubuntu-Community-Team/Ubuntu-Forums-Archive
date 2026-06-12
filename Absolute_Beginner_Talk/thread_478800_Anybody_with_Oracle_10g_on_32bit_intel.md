---
title: "Anybody with Oracle 10g on 32bit intel"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by s_raghu20 on 2007-06-19
Hi,

I am fighting with installation of oracle 10g on my 32bit pentium-4 laptop. (Dell Inspiron 5100).
 
Is anybody around here who has experience with this ?

please share.

regards,
raghav..

---

### Post by s_raghu20 on 2007-06-23
Dear Friends...

I am trying to install Oracle 10g on my Dell Inspiron Pentium-4. Initially I had hiccups with starting the installation itself. Later when I got through with that, I got into problems with make.

I got the thread at [http://ubuntuforums.org/showthread.php?t=437691]("http://ubuntuforums.org/showthread.php?t=437691")
and tried to follow... also worried that I am on a 32 bit intel arch.. eventually it did not completely work for me...

I tried to follow your suggestions, especially with respect to downloading extra packages from the repository. However, I did not find all the right packages mentioned by you. May be I am making some mistake, but neither I could find packages mentioned by you in synaptic package manager, nor the apt-get command work for me.

Could you please shed some more light on this for me. Also, will it make a difference that my system is a an intel based 32bit one, whereas your experience has been with a 64bit system. Just wondering, no knowledge.

Looking forward to ideas, suggestions etc.. Please...

regards
raghav..

---

### Post by heyhey on 2007-06-25
You didn't say which version of Ubuntu you were trying to install on.

I installed the 32-bit 10g R2 enterprise version on Ubuntu 7.04 32-bit desktop version, the machine is a HP - but that really shouldn't matter.

1. download the Redhat package from Oracle
2. make sure the system parameteres are right (semiphore etc)
3. make all kinds of changes to fake ubuntu so that it looks like Redhat to the installer.  Very important to have the right symbolic links etc.  You can find this info on several references.  
4. install all required packages - you can find a lot of references on this - the 64-bit doc had some libraries that don't apply to me.
5. try to install

You might have to do 3-5, especially 4-5 several times.

If you still couldn't get it right, post your error messages here I'll see if I can help.

---

### Post by heyhey on 2007-06-25
This is a good ref

[http://www.dizwell.com/prod/node/52](http://www.dizwell.com/prod/node/52)

Even though it was for Ubuntu versions prior to Feisty Fawn, you can pretty much use it for Feisty Fawn, just change some of the references accordingly.

The Oracle package I used is:

[http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux32.zip](http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux32.zip)

---

### Post by pwhite on 2007-07-26
> **heyhey said:**
> This is a good ref

[http://www.dizwell.com/prod/node/52](http://www.dizwell.com/prod/node/52)

Even though it was for Ubuntu versions prior to Feisty Fawn, you can pretty much use it for Feisty Fawn, just change some of the references accordingly.

The Oracle package I used is:

[http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux32.zip](http://download.oracle.com/otn/linux/oracle10g/10201/10201_database_linux32.zip)

I was using Oracle-XE and was getting sick of restarting JBoss/Oracle due to frequent T4 connection related errors with my current work project. After seeing the above "howto" I decided to give it a shot and it worked like a champ (all the errors are gone too). :-)

Thanks!
-Peter

---

