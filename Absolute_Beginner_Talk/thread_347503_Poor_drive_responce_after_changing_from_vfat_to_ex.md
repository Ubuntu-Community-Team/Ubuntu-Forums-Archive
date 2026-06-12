---
title: "Poor drive responce after changing from vfat to ext3"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by jadedjay on 2007-01-27
Hi

I am not sure if this is a good place to put this question as it might fall more into the Multimedia area, but then Im a beginner so....

My problem as simple as I can explain it.

I have a computer with an usb external drive stack connected.  The drives inside the stack use to be formatted to vfat when I originally purchased them.

The main function of the computer is to run Freevo (media desktop) on Ubuntu Edgy to watch various video files and play audio files that are on the external drive stack.  
This was all working rather well and I never noticed any problems with the performance and display of videos in various media players including mplayer and xine (via Freevo), even when watching rather long films.

I then decided to format the drives to ext3 to get the benefits of that file system.  And do away with my last attachment to MS windows.
That all went well, and I moved all my original files back onto the drives.

I have now noticed however that when I watch the video files in the same media players (i.e. none of their settings have changed from previously)  after several minutes of viewing the video files, the picture ends up going out of sync with the audio.  This appears to big happening on all of the video files I am watching, especially the larger ones.

I am at a loss when another external vfat drive I have can still serve up the video files fine, with no noticable delays.  In fact the same file works perfectly.  

I am guessing that I am doing something wrong with the mounting of my ext3 and I cant understand why the performance would be any worse than a vfat drive.

Following some suggestions from other web sites I have tried mounting the drives in /etc/fstab using the following settings:

1st attempt.
/dev/sda1 /media/audio ext3 nouser,auto,atime,rw,nodev,noexec,nosuid 0 0
/dev/sdc1 /media/visual ext3 nouser,auto,atime,rw,nodev,noexec,nosuid 0 0
2nd attempt.
/dev/sda1 /media/audio ext3 defaults 0 0
/dev/sdc1 /media/visual ext3 defaults 0 0

But the performance is still the same.
I dont really want to return my drives to vfat.
:( 
Can anyone give me some pointers on how I should mount the ext3 drives correctly?

---

