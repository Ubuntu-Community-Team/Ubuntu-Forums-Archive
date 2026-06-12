---
title: "DEB issues."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-02-03
I use suse at school, ubuntu at home. Because I started this new distro at school I wanted to learn how to install every package desirable. So the guinea pig program to me is the linux aim program straight from aim's web site.

I've downloaded deb and tar.gz, which from what I understand tar.gz is universal among all distros, right?

Both give me errors. I've searched and search on these forums and every thread that has been resolved is exactly the method I'm using, however I can't get it to work.

On AIM's web site I have a choice of Debian 2.1 or Debian 3+. I've tried both. Check this out.

The first section of coding is when I just typed the name in. The second is where I typed sudo dpkg -i and then dragged the package onto terminal. I get the same error for 2.1 and 3+. 





jason@jason:~$ cd Desktop
jason@jason:~/Desktop$ sudo dpkg -i aim_1.5.286-1_i386.deb
dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `aim_1.5.286-1_i386.deb' is not a debian format archive
dpkg: error processing aim_1.5.286-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 aim_1.5.286-1_i386.deb





jason@jason:~/Desktop$ sudo dpkg -i /home/jason/Desktop/aim_1.5.286-1_i386.deb
dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `/home/jason/Desktop/aim_1.5.286-1_i386.deb' is not a debian format archive
dpkg: error processing /home/jason/Desktop/aim_1.5.286-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /home/jason/Desktop/aim_1.5.286-1_i386.deb






Another question. I downloaded the tgz file just to try that out. When I download it, a folder appears on my desktop. I double click it and hit the exact button. Then, a folder appears on my desk that says "usr." Inside are two more folders, bin and lib. What gives? How do I finish installing this?

Essentially I'm trying to figure out how to install tgz and deb files on the ubuntu system. If anybody can tune in to how I install rpm's on suse that'd be great too...

---

### Post by meng on 2007-02-03
You have the right idea with .deb files, but the particular deb file you are trying to install just isn't playing nice. Forget about all of those! Why not just use gaim, it comes with Ubuntu by default.

---

### Post by taurus on 2007-02-03
You need to download the aim_1.5.286-1_i386.deb in binary mode, not ASCII mode as the error message implied.  

And for the .tar.gz, you just exact it from / so the binary would go into /usr/bin and the libraries would go into /usr/lib.  However, just to let you know that you will have a problem running aim because there is a missing library.  This problem has been discussed a few times here so good luck trying to get aim running.

---

### Post by glabouni on 2007-02-03
> dpkg-deb: **file looks like it might be an archive which has been**
dpkg-deb: **corrupted by being downloaded in ASCII mode**
dpkg-deb: `aim_1.5.286-1_i386.deb' is not a debian format archive

from this output it seems to me pretty clear that your deb files are corrupted.

I've been to aim linux download page to get the download url for debian 3+. try wgetting the file with :
```
wget http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
```

tar.gz is a compressed file format (tar'ed and gzipped). these usually are sourcesfor you to compile.

---

### Post by Roasted on 2007-02-03
How would I download it in binary mode? It didn't give me a choice. I just clicked and it was on my desktop. :confused:

---

### Post by Roasted on 2007-02-03
> **glabouni said:**
> from this output it seems to me pretty clear that your deb files are corrupted.

I've been to aim linux download page to get the download url for debian 3+. try wgetting the file with :
```
wget http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb
```



jason@jason:~$ wget [http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb](http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb)
--12:11:55--  [http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb](http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb)
           => `aim_1.5.286-2_i386.deb'
Resolving ftp.newaol.com... 205.188.226.57
Connecting to ftp.newaol.com|205.188.226.57|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,126,195 (1.1M) [text/plain]

100%[====================================>] 1,126,195    915.32K/s             

12:11:56 (913.00 KB/s) - `aim_1.5.286-2_i386.deb' saved [1126195/1126195]

jason@jason:~$ 




I guess it worked. That's great and all, but I want to know how to manually install these on my own.

---

### Post by taurus on 2007-02-03
Are you using firefox in Ubuntu?

p.s.  ```
sudo dpkg -i aim_1.5.286-2_i386.deb
```
And good luck.

---

### Post by Roasted on 2007-02-03
Yes, I'm using Firefox.




jason@jason:~$ sudo dpkg -i aim_1.5.286-2_i386.deb
dpkg-deb: file looks like it might be an archive which has been
dpkg-deb:    corrupted by being downloaded in ASCII mode
dpkg-deb: `aim_1.5.286-2_i386.deb' is not a debian format archive
dpkg: error processing aim_1.5.286-2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 aim_1.5.286-2_i386.deb
jason@jason:~$ 



See why I'm confused now, Taurus? I did exactly what I found on the search forums. Yet nothing works. :(

---

### Post by meng on 2007-02-03
.deb files for Debian do not ALWAYS work with Ubuntu. Sometimes they do, sometimes not. Still not interested in using gaim? Then look here for general instructions on installing from source (that's the .tar.gz file):
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

---

### Post by taurus on 2007-02-03
Before you plan to spend more time on this aim thing, will let you know that it is **not** going to run on your Ubuntu due to missing some old library.  So, perhaps you should spend that time trying to play with gaim.

---

### Post by taurus on 2007-02-03
> **meng said:**
> .deb files for Debian do not ALWAYS work with Ubuntu. Sometimes they do, sometimes not. Still not interested in using gaim? Then look here for general instructions on installing from source (that's the .tar.gz file):
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

This .tar.gz is a little different than the normal .tar.gz.  If you unpack it, you will get /usr with binary in /usr/bin, libraries in /usr/lib/, and a few others.  Therefore, there are no ./configure, make, and make install.  In other words, you have to move the .tar.gz to / and unpack it from there.  I already went through this whole thing not that long ago with another user and again, aim is not going to run on Ubuntu due to some missing library (old library).

---

### Post by meng on 2007-02-03
Sorry, good call taurus. I did read that but forgot by the time I posted the next reply.

---

### Post by Roasted on 2007-02-03
> **meng said:**
> .deb files for Debian do not ALWAYS work with Ubuntu. Sometimes they do, sometimes not. Still not interested in using gaim? Then look here for general instructions on installing from source (that's the .tar.gz file):
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

I said before bro, I'm doing this strictly to learn how to install these packages better. I have ZERO desire to use AIM. I've used GAIM ever since I can remember. I'm just using AIM as a learning tool.

But I guess I really should just use something else. I did however get AIM working on Dapper once - true story, but I completely forget what I did. It looked like something out of Windows 3.1 though. 

Maybe I should pick something else. But regardless, I AM doing everything right. Aren't I? It's just a corrupt package which is nothing I can change.

What about tgz files though? As I said, I have the folder. I extracted it, and another folder appeared. Now what??

---

### Post by meng on 2007-02-03
Bro: take note of what taurus said (and as your last post suggests), this is not a good package with which to be learning the principles of installing software. As my first post here said, you are on the right track with the dpkg command. Yes, you ARE doing everything right (for the general case).

---

### Post by Roasted on 2007-02-03
Now how can I take an rpm and use it with ubuntu? Limewire only has rpm's available, and I had limewire on dapper before I upgraded to edgy.

---

### Post by meng on 2007-02-03
If you navigate to the link I mentioned earlier, it explains how to use alien to convert rpm to deb. It's not a great solution, but it works most of the time. Also, be aware that there is frostwire, an alternative to limewire (and yes, you don't need to repeat that this is just a learning exercise for you, I understand that completely).

---

### Post by Roasted on 2007-02-03
Yeah. I already have frostwire. I'm just trying to think of another program I can download to test this with, and seeing as though limewire is rpm only and I'm out of ideas... blah...

And now that you mentioned Alien, I remember someone walking me through that which is where I got limewire from. I'll just let that idea pass.

But regardless, let me just get this down:

When installing Deb's, I typically want to cd Desktop (assuming that's where I downloaded the package to) and do a "Sudo dpkg -i *InsertNameOfPackageHere*" Done. Then I should be able to easily run the program I just downloaded.

When installing Tar.Gz's, I just use the Archive Manager which extracts them. Then, there's a readme inside. Now from experience, the readme's suck terribly. Is there a particular command to use, kind of like with Deb's where you'd use sudo dpkg -i?

---

### Post by meng on 2007-02-03
deb files: yes this is correct. Sorry I didn't make this clearer on the previous 2 occasions.
tar.gz: again this is mentioned in the link provided. The usual .tar.gz package requires you to unpack, configure, make, make install, e.g.:

cd Desktop
tar zxvf newpackage.tar.gz
cd newpackage [the extraction creates a new folder, you see]
./configure
make
sudo make install

---

### Post by Roasted on 2007-02-03
Ah, I always thought that with configure and make there was something to come after it. So I guess that's all you do, is just ./configure and make, install, BAM. Done?

---

### Post by meng on 2007-02-03
Yes.

---

