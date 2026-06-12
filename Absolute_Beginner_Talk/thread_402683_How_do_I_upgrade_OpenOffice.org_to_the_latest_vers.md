---
title: "How do I upgrade OpenOffice.org to the latest version"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-06
OpenOffice.org 2.2 is out.

I just downloaded the .tar.gz file, but is their an easier way to update OOo than installing it from source?

---

### Post by tchoklat on 2007-04-06
aptitude install 'program_name"

---

### Post by wersdaluv on 2007-04-06
> **tchoklat said:**
> aptitude install 'program_name"

So even if I have OOo installed, that code will just upgrade the present OOo installed?

---

### Post by tchoklat on 2007-04-06
that's my understanding,
 
do a;
 
sudo aptitude update 
 
first though!

---

### Post by tchoklat on 2007-04-09
read this
 
[http://trustworthy.net/blog/2007/01/openoffice-21-on-ubuntu/](http://trustworthy.net/blog/2007/01/openoffice-21-on-ubuntu/)

---

### Post by Bachstelze on 2007-04-09
No, it won't upgrade your OOo. THe two nly ways you can upgrade your OOo to 2.2 are building it from source and upgrading to Feisty.

---

### Post by computerease on 2007-04-11
If it is inappropriate to extend the beginning question in this thread, I apologize:  However:  Is there a reason why the upgrade of OO 2.1 or 2.2 does not appear in the repository lists in Synaptic for 6.06 (LTS)?  Due to potential issues of conflict or incompatibility some have become retiscent to update by either direct download from OO or from a converted RPM.  The issue here is whether or not there are (Ubuntu) flavor-specific issues to consider in upgrading to 2.1 or 2.2 which are the underlying reasons it is not directly available through Synaptic or Apt.
Thank you in advance for any feedback.

---

### Post by Michaelt74 on 2007-04-11
This is a great howto:

[http://ubuntuforums.org/showthread.php?t=398074&highlight=open+office+2.2](http://ubuntuforums.org/showthread.php?t=398074&highlight=open+office+2.2)

---

### Post by silkstone on 2007-04-11
This worked fine for me, and is taken from other posts here...

INSTALL OPEN OFFICE 2.2 ON UBUNTU EDGY
---------------------------------------------------

1) If Alien is not already installed, then...

```
sudo apt-get install alien 
```

(Or install Alien from Synaptic, which is probably easier.)

2) Download OO 2.2 from openoffice.org and unpack the tar file.

3) Remove the Ubuntu version of open office ...

```
dpkg -l | grep -i openoffice | cut -d " " -f 3 | sudo xargs apt-get -y --purge remove
sudo apt-get autoremove 
```

4) Convert the downloaded Open Office files from rpm to deb...

```
cd directory_where_you_extracted_the_OO_compressed_file
cd RPMS
sudo alien --scripts --keep-version *.rpm 
```

(This can take quite a while.)

5) Install the new version of openoffice...

```
sudo dpkg -i *.deb
cd desktop-integration/
sudo dpkg -i *.deb 
```

The new version should then be listed under Applications > Office, and you can add the various components (Writer, Calc, Impress, Base) to a toolbar for quick launch if you like.

PLEASE NOTE: Although this procedure has worked for me and other people, I strongly recommend that you make a backup of your system files before trying it, just in case.

------------------------------

---

### Post by frrobert on 2007-04-11
I used the following method for installing 2.2 the topic says intalling 2.0 but works for 2.2

I likeit because it doesn't remove the old version so if something happens you  still have the old version

[http://www.oooforum.org/forum/viewtopic.phtml?t=26173](http://www.oooforum.org/forum/viewtopic.phtml?t=26173)

---

