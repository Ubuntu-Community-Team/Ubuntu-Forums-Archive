---
title: "problem with edgy"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by vatzcar on 2007-01-04
Hi,
previously i was using ubuntu 6.06 without any problem with xine, wine, and few other stuff installed. now i've installed 6.10. during the process i didn't have any upgrade option, so i had to re-install the whole os. now i'm facing following problems:

1. whenever i'm using the command(except first time after each boot) **'sudo nautilus'**, it's not asking me for password.
2. at the time of executing the above command an error is showing, and my mounted partitions are not coming within nautilus.
```
(nautilus:22819): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

```
3. if i'm browsing my vfat partition the following messing is showing(only for few folders)
```
** Message: don't know how to handle video/x-xvid, framerate=(fraction)25/1, width=(int)208, height=(int)176, codec_data=(buffer)00000000
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)22050, channels=(int)1, codec_data=(buffer)040080bb000008000000000000000000000000000000
totem-video-thumbnailer couln't open file 'file:///media/sdb7/mov03287.avi'
Reason: You do not have a decoder installed to handle this file. You might need to install the necessary plugins..
** Message: don't know how to handle video/x-xvid, framerate=(fraction)25/1, width=(int)208, height=(int)176, codec_data=(buffer)00000000
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)22050, channels=(int)1, codec_data=(buffer)040080bb000008000000000000000000000000000000
totem-video-thumbnailer couln't open file 'file:///media/sdb7/mov03288.avi'
Reason: You do not have a decoder installed to handle this file. You might need to install the necessary plugins..
** Message: don't know how to handle video/x-xvid, framerate=(fraction)25/1, width=(int)208, height=(int)176, codec_data=(buffer)00000000
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)22050, channels=(int)1, codec_data=(buffer)040080bb000008000000000000000000000000000000
totem-video-thumbnailer couln't open file 'file:///media/sdb7/mov03290.avi'
Reason: You do not have a decoder installed to handle this file. You might need to install the necessary plugins..

```
it's all 'bout totem and codec, but there's nothing to do with that as i'm just browsing one folder in my vfat partition.
4. when i'm going to install xine. running './configure' and error is coming that xine configuration failed due to non existence of libpng. where i'm installed with libpng (even with libpng-dev)
5. whenever i'm trying to run wine, a folder access error is coming.

i'm totally updated with all my installed stuffs. i've tried to re-install edgy over and over. my partition is like this 

root - on extended partition residing with another vfat partition.
swap - on same extended partition.
home - on a primary partition.
my disk have partition like this
{primary partition - NTFS}
{primary partition - [extended partition - vfat, ext3(root), swap]}
{primary partition - ext3(home)}

please help me to solve this problem. thank you.

---

### Post by vatzcar on 2007-01-04
ohhh.... one more thing i forgot to tell, my ATI control panel is not also working. it can't find out **'fireglcontrolpanel'**. BTW, in my prev. version ubuntu all were working just fine. Thanks

---

