---
title: "DVD Help!"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Drillbit on 2007-05-02
I can burn CD's. I can burn movies on CD. I can play DVD's but can't burn a movie to DVD. I just get error messages on all, including Nautilus.

I have a Samsung SH-W163A (TS-H553A) and have burned DVD's on Dapper and Edgy.  

K3B error message

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ERROR: Communication problem with k3b, it probably crashed.
paul@paul-desktop:~$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD__RW_TS_H553A to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 1, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()


EDIT: Seems that my drive is now a DVD + drive only. I don't why or how but at least it's burning now.

---

### Post by starcraft.man on 2007-05-02
Let me recommend a program called Devede to do the transcoding, just open it up and you can either transcode right into a disk structure or an iso. That should solve the problem.

Its in the repos, I don't think you need to add anything. Just type in the terminal:

```
sudo aptitude install devede
```

That should do it for ya, enjoy your dvd movies.

You can just burn the iso or disk structure to a dvd with k3b after.

---

### Post by Drillbit on 2007-05-02
> **starcraft.man said:**
> Let me recommend a program called Devede to do the transcoding, just open it up and you can either transcode right into a disk structure or an iso. That should solve the problem.

Its in the repos, I don't think you need to add anything. Just type in the terminal:

```
sudo aptitude install devede
```

That should do it for ya, enjoy your dvd movies.

You can just burn the iso or disk structure to a dvd with k3b after.

Thanks you very much, but before I go on the hunt - I should have explained a little further. The movies that I try to burn are on my HD in the form of XVids or .avi's etc. I just want to burn them out. Will your suggestion work for that?

---

### Post by starcraft.man on 2007-05-02
Yup, devede is a transcoder. When you install it and open it up, pick DVD. Then just import the file, choose your  video bitrate so that its less than 4.3 GB (max size of standard DVD) and then select disk structure in the bottom of the first page. Then push next, save it to your desktop or anywhere else.

Wait until its done transcoding, then you have the TS files in the folder that was made. Just burn the audio/video folders inside the new folder with K3b into a data DVD (option right on main page). This should play on any dvd player :)

Note: you can choose ISO instead of disk structure, but sometimes I've run into problems trying to burn where as I've always been successful with disk structure and a manual burn.

---

### Post by Drillbit on 2007-05-02
> **starcraft.man said:**
> Yup, devede is a transcoder. When you install it and open it up, pick DVD. Then just import the file, choose your  video bitrate so that its less than 4.3 GB (max size of standard DVD) and then select disk structure in the bottom of the first page. Then push next, save it to your desktop or anywhere else.

Wait until its done transcoding, then you have the TS files in the folder that was made. Just burn the audio/video folders inside the new folder with K3b into a data DVD (option right on main page). This should play on any dvd player :)

Note: you can choose ISO instead of disk structure, but sometimes I've run into problems trying to burn where as I've always been successful with disk structure and a manual burn.

Again, thank you. 

So, the problem with burning the movies came from them being avi's xvid's etc? If I convert them K3B should work?

---

### Post by jacktar on 2007-05-02
Will this method overcome the mplayer bug that distorts the sound in devede burned disks ?

---

### Post by Drillbit on 2007-05-03
Thing is, I have a Divx DVD player. In Dapper and Edgy it used to only take me minutes to movies onto a disc. Sometimes I'd get three or four on there. 

Can't do that now. I was just wondering if it's a Feisty thing? And does anyone know how to fix it?

---

### Post by jacktar on 2007-05-03
I tried the above method but it produced a poor quality movie with no sound.

---

