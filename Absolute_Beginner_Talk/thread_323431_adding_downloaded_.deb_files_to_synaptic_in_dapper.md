---
title: "adding downloaded .deb files to synaptic in dapper"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by uthpalawe on 2006-12-22
I successfully updated my off line dapper machine's package list and downloaded the some packages with dependencies.  How can I add the downloaded files to synaptic through the option add downloaded packages. It does not me to add .deb files directly. What should I do for the downloaded .deb files. (I would like to add these without burning them in a CD.)

Thanks

---

### Post by dckirba on 2006-12-22
Interesting, i dind't know you could do that. I've been installing packages and dependencies one by one on my offline machine.

---

### Post by uthpalawe on 2006-12-22
For the benifit of others I will tell how I did this.

I am using Ubuntu dapper and in our computer lab there are some computer that run Ubuntu hoary. I first selected the repostitory from which I wanted to install software. This are written to /etc/apt/sources.list file.

Then I copied /var/lib/apt/lists (this folder contians infromation where can a package be fetched) and /etc/apt/sources.list (here are the repositories you specify) from my dapper machine to the horary machine. (Do not overwrite the files rename the exitsting files and copy the new file). Then openning Synaptic order it to reload the package list. It will update   the /var/lib/apt/lists folder. Now you have the updated package list where you can copy to your machine.

---

### Post by uthpalawe on 2006-12-22
If someone knows the answer for my first question please post or direct me where I can find it. Also if you know how to get the security updates notify. Lastly dckirba you can now generated a script that can be run either on windows or any linux machine through the synaptic option generate download script after specifying the packages which you want to install. It will download all the packages with dependancies.

Then I am stuck. I do not know to port them into Synatics add downloaded packages option. If find it out please post a answer.

Thanks.

---

### Post by pandu.rs on 2006-12-22
assuming ~/debs is the directory containing ur deb files, u need to run the following command

dpkg-scanpackages ~/debs /dev/null | gzip > ~/debs/Packages.gz

to make use of the local repository u shld add the following line to /etc/apt/sources.list

deb file:/home/<username> debs/

Also u can have a look at my postings in this thread which describes how i managed offline installation.
[http://ubuntuforums.org/showthread.php?t=304746](http://ubuntuforums.org/showthread.php?t=304746)

Debian reference [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

---

### Post by uthpalawe on 2006-12-22
Thanks a lot. I think it will work. I am going home for holidays where I will not have a Internet connection. So I'll be offline for sometime. 
Bye.

---

### Post by uthpalawe on 2007-11-22
The easiest way to do this is copy all the debs into /var/cache/apt/archives. Then use synaptic or apt-get to install them all.In newer version of Ubuntu this is easy to do. The hard part is to update the lists file in your computer. Then there is a download script generation feature in synaptic which can be either downlaoded using wget on windows or in linux.

---

