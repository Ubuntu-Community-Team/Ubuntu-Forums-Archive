---
title: "Apache PNG support"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by mrsticks on 2007-09-20
I am scheduled to give a small talk to some high school kids on Linux, and plan on using Ubuntu as the distro of choice.  The teacher is going to have us use the LiveCD for demo purposes, rather than install over the school's hard drives.  Fine with me.  So I was playing around with the LiveCD today.

One of the things I am going to do is show them how to make a LAMP server.  I am able to install everything I need from the LiveCD ( Desktop Edition ).  I logged into phpMyAdmin, and noticed the icons ( "Structure, SQL, Search... " ) don't show up.  After a few mins checking to make sure the icons were actually there, and worked, I moved on, but it was really bugging me. The images were PNGs, I wondered if that was it.

I downloaded a random PNG image from google, and placed it in the root dir.  Sure enough, when I browse through the apache2-default/ in Firefox and click on the image name, the image doesnt display, it just prints the full location of the file in the page

```
http://localhost/apache2-default/image.png
```

Yet the same browser is capable of displaying PNGs from other web sites across the net, which leads me to believe there is something wrong with my apache config.  I have restarted apache several times, to get php and mysql working, and they both work fine.

Thanks for any help.

-peter

---

### Post by enigma83 on 2007-09-21
I'm having the same issue.  Apache log files appear to have nothing wrong.  If I use wget, I get " Connection closed at byte 0. Retrying"

Tips?

---

### Post by FAo10rK on 2007-11-25
The answer of this problem is here :
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393)

You just have to add this line in /etc/apache2/apache2.conf :
EnableSendfile Off

And it works !

Thanks a lot, bapoumba !

---

### Post by benrboone on 2007-11-26
I am also having what appears to be a similar issue.  I have installed lamp and can view jpg or bmp images just fine however png images only show the text description
including the this "EnableSendfile Off" in the above file didn't fix the issue

---

### Post by benrboone on 2007-11-26
found my problem, the website created by another person, did not differentiate the CAPITALS from lowercase.  all the file extensions on the png images where .PNG while the html documents had the file extensions as .png

---

