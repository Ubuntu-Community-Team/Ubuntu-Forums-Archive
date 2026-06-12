---
title: "Importing video files from Digi Camera"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by mmm guitar on 2006-09-09
Hi,

Fairly new to linux + finding it great so far, I am running the most up-to-date one avaliable (ubuntu dapper I think its called).  

I have a Sony CyberShot Dsc-N1 digital camera, its a photo camera but can take little video clips. Thanks to a thread on this forum I have got Ubuntu recognising the camera and importing photo's via 'gThumb', by setting the camera to PTP USB mode - all good so far :)

My problem is that I have some small video's on the camera as well (recorded by the camera) however, on import only the photo's are downloaded and the videos remain on the camera.  In gThumb, the preview pane bit shows all images and videos.

Is there a way to import these videos into ubuntu?  or is there a way to see the camera like a USB stick?  I tried setting the camera to mass storage device, but nothing happened when I connected it to my pc. I also tried to see if there was any settings in the preferences or other threads with the same prob, could find nothing.

Any help would be great thanks.

---

### Post by mmm guitar on 2006-09-10
:sad:

---

### Post by ieee488 on 2006-09-10
Are you able to do this in Windows?
Is there a separate procedure or a different cable hook-up?

In all likelihood, the video files are MPEG4 or something of that genre.

---

### Post by mmm guitar on 2006-09-10
Hi,  

Yes in windows I can.  The cable is a standard USB cable.  Within the camera all the photo's and videos are stored in the same folder and yeah standard MPEG4.  

Windows recogises it as a camera, and using some 3rd party software I can import both video and audio (also with the software that came with the camera). In addition, at the same time windows recognises it as a mass storage device - so I can go to My computer and there is a link there to the camera memory as if it were a USB memory stick.  Is it possible to access the files on the camera memory in that direct manner in ubuntu?

The files are stored in the camera on a Sandisk Pro Duo card (or something to that effect). Suppose if its currently an impossible problem then a card reader might be a solution?

Thanks, just one or two little things to figure out with ubuntu then I can wave goodbye to my windows partition :)

---

### Post by mmm guitar on 2006-09-10
Is there a gernal ptp program?

---

### Post by Lakefall on 2006-09-10
If you are not afraid of the command line, try using [gphoto2](http://packages.ubuntu.com/dapper/utils/gphoto2). The command "gphoto2 -P" should try to retrieve everything from the camera into the directory you are in. [gthumb](http://packages.ubuntu.com/dapper/gnome/gthumb) uses the same library, so in principle it should be able to get the same files though.

> **mmm guitar said:**
> is there a way to see the camera like a USB stick?
It seems [gphotofs](http://packages.ubuntu.com/dapper/utils/gphotofs) might do that, but I've never tried it.

---

### Post by mmm guitar on 2006-09-10
Hi,

Thats great thanks, gphoto2 works great and I just now noticed after you said that the gThumb viewer filters the images out to display, so the mpg's were actually imported into the folber but just ignored by the viewing app. :oops:

Great, all good. Thanks :D

---

### Post by tina-athens on 2006-09-27
Hi! It's my first week with ubuntu - linux and I am a little lost. I would like to ask something. I have connected my digital camera with my laptop. I have downloaded the gphoto2 and i am trying to import a video from the camera into my computer but my camera is not detected. What can I do? I just write in terminal: gphoto2 -P. Do I have to do something else??

---

