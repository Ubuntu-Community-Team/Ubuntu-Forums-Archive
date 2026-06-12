---
title: "Having various problems working with Ubuntu as headless downloader.  Please, help?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-09-01
I'm trying to install azureus on Ubuntu 6.06 LTS.  I'm mainly following this [guide]("http://nerdica.com/?p=30").  My ultimate goal is be able to log into my Ubuntu box with my Macbook running Tiger.

The list of problems I've already encountered: 

    * Format the 120 GB HDD to a format that both Ubuntu and OS X can read/write to
    * Mount said drive
    * Share said drive on Ubuntu
    * Mount said drive on OS X
    * Install Azureus
    * Set Up Azureus to have scheduled downtime between 3pm and 10pm

I haven't been able to get any of these things to work, so far.  The HDD comes up when I go to Places/Computer, but it won't mount.  Right now it is formatted to jfs.

When I tried to install azureus using the instructions from the guide, I was told that "E: couldn't find package sun-java5-jre"
So then I tried sudo apt-get install azureus and got the same "couldn't find package" error.

Can anyone help me with this?  

I'm sorry to have created two threads in such rapid succession, I just figured I would condense all my problems to this one thread.

Russ

---

### Post by iamhugeinjapan on 2007-09-01
To install Java on 6.06, see this page:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

After that Azureus should behave itself.

It shouldn't matter too much what file system you format your partions in because I assume you'll be accessing them from OS X via a Samba (smb) share.

---

### Post by dmber on 2007-09-01
i followed the directions for installing the repositories.  that (seems to have) worked.  that's where i stopped being able to follow the directions.  it seems that my next step is "Installing Sun Java Ubuntu 7.04

    *

      Sun Java6: sun-java6-bin, sun-java6-jre
    *

      Blackdown Java2 1.4: j2re1.4

Ubuntu 6.06 / 6.10

    *

      Sun Java5: sun-java5-bin, sun-java5-jre
    *

      Blackdown Java2 1.4: j2re1.4


I have 6.06.  I have no idea what I'm supposed to do now.  I'm ready to copy/paste whatever needs to be done, but I don't see anything that's copy/pastable.  

I don't get it.  I just don't get it.  It won't mount my jfs formatted hard drive.  it can't find any packages.  what did i do wrong?

---

### Post by iamhugeinjapan on 2007-09-01
```
sudo apt-get install sun-java5-bin
```

That should do it. If not try:

```
sudo apt-get install sun-java5-jre
```

If your jfs partition is not auto mounting, you'll need to tell the /etc/fstab file about it. Are you familiar with editing that file?

---

### Post by dmber on 2007-09-03
ok, using add/remove applications, i got azureus and java re 1.4 installed.  now i need to get my storage HDD mounted and shared on the network and i'll be good to go.  

i'm still getting the "can't mount" error on my jfs-formatted drive.

any ideas?

---

### Post by dmber on 2007-09-03
ok, now i actually got the sharing figured out on my own.  now all i need is to get this extra hard drive mounted.  

should i take some screen shots?  

[[IMG]http://img297.imageshack.us/img297/1398/picture1en1.th.png[/IMG]](http://img297.imageshack.us/my.php?image=picture1en1.png)

[[IMG]http://img297.imageshack.us/img297/1654/picture2fu7.th.png[/IMG]](http://img297.imageshack.us/my.php?image=picture2fu7.png)

[[IMG]http://img528.imageshack.us/img528/1376/picture3qo6.th.png[/IMG]](http://img528.imageshack.us/my.php?image=picture3qo6.png)

[[IMG]http://img528.imageshack.us/img528/8093/picture4vu6.th.png[/IMG]](http://img528.imageshack.us/my.php?image=picture4vu6.png)

---

