---
title: "Playing Mp3"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by Maccabee on 2005-12-26
hi,
    Anyone plz tell me what the easiest way to play mp3 in ubuntu without a net connection?

---

### Post by 23meg on 2005-12-26
Download the deb file for gstreamer0.8-mad from [http://packages.ubuntu.com](http://packages.ubuntu.com) on a computer with a net connection, transfer it to the one without the connection and type ```
sudo dpkg -i /path/to/deb/file
``` to install.

---

### Post by Maccabee on 2005-12-27
I couldnt find any package named gstreamer0.8-mad.deb instead i
got this page 
> 
[http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad](http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad)

Here i  found only this file 
> [http://archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gst-plugins0.8_0.8.11.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gst-plugins0.8_0.8.11.orig.tar.gz)

and i downlaoded it

Will it be sufficient? please tell me what to do now
                                                                  Thanks

---

### Post by 23meg on 2005-12-27
Here's the exact url:

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb)

---

### Post by Maccabee on 2005-12-28
Shall there i need any change in code you given 
```
sudo dpkg -i /path/to/deb/file
```
I meant whether i should replace "file" by "gstreamer0.8-mad.deb"
and "path" by something else?
Also what should i do after issuing that command -just open totem and play mp3 files?
Plz forgive im completely new to linux.

---

### Post by Qrk on 2005-12-28
Yes, you will have to change that command to show the location of your actual deb file. 

Once you run that command,  you are set to go.

---

### Post by Maccabee on 2005-12-28
ok ie if the deb file is in /home/root/

my command should be 
sudo dpkg -i  /home/root/gstremer.....deb     rit?

But yet one more problem.
That command produced some "Dependency error"
It tells that libid3tag0 is not installed.
Will installig these will be sufficient?
[http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0-dev_0.15.1b-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0-dev_0.15.1b-1_i386.deb) 
[http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-1_i386.deb)

---

### Post by Sir_Yaro on 2005-12-28
[QUOTE=Maccabee]hi,
    Anyone plz tell me what the easiest way to play mp3 in ubuntu without a net connection?[/QUOTE]
```
[yaro][/Mp3/!News]$ play berety2.mp3
playing berety2.mp3

[yaro][/Mp3/!News]$    
```

---

### Post by Maccabee on 2005-12-29
Hi It Worked !!!!!!!!!!(gstreamerplugin)
             Thanks a Lot
Feeling happy about using Ubuntu now.

Is There any similar pulgin availabe to make my totem play movie files like avi,.mpg,.dat,.wmv etc....???

---

### Post by Lord Illidan on 2005-12-29
The best thing would be to get access to the net connection for a night, if you can, and run automatix. (Do a search for it). It will download everything you can possibly need.

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=Lord Illidan]The best thing would be to get access to the net connection for a night, if you can, and run automatix. (Do a search for it). It will download everything you can possibly need.[/QUOTE]


I hate to say it...but....that comment is right.

---

### Post by Maccabee on 2005-12-29
Im going to buy a new modem to replace my winmodem any way it will take some time
                Thanx

---

