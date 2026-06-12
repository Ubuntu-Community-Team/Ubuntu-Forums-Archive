---
title: "iSight and Coriander"
date: 2007-03-31
forum: Apple Intel Users
---

### Post by Azathoth_ on 2007-03-31
Hi, i have a problem when a try to use isight with amsn and other v4l compatible problems. iSight is a firewire webcam and i have tried a lot of ways to make it possible. But coriander gives me this error:
warning: could not find a Digital Camera on the bus...
I need to use webcam and only v4l2 compatible programs, like ekiga let it.
Can anyone help me with coriander??? or with other msn compatible client with v4l2?

Thanks a lot

Mario

---

### Post by oswaldkelso on 2007-04-17
Better late than never? 
I have got my isight working in ekiga today. On my g4 emac running debian etch. I'm not sure which pakages worked as I tried a hole bunch, below are that pakages I installed.

Installed the following packages:
dvbackup (0.0.4rj1-6)
dvgrab (1.8-4)
gscanbus (0.7.1-6)
gstreamer0.8-dv (0.8.12-6)
libdc1394-11 (1.0.0-4)
libdv-bin (1.0.0-1)
libpt-plugins-avc (1.10.2-2)
libpt-plugins-dc (1.10.2-2)
libquicktime0 (2:0.9.7-1)
libraw1394-5 (0.10.1-1.1)

then as root I ran coriander in a terminal and the isight showed up and worked fine thought on disconecting I had to unplug the camera and replug it to activate it again.

I quit coriander then I still as root setup an ekiga account and checked enable video. then  video plugin as 1394dc.
then input device as /dev/video1394/0. then auto and it worked. 

I only just tried it so will have to play with permissions hope it helps someone

---

### Post by Azathoth_ on 2007-04-18
Thanks a lot. But, at least with Feisty Beta, it doesn't work for me with a MB C2D. :(

---

### Post by oswaldkelso on 2007-04-18
> **Azathoth_ said:**
>  it doesn't work for me with a MB C2D. :(
Sorry I did not realise the built in isights were firewire. I thought you were using an external isight with a firewire cable. That why I thought the post should be in ppc.

---

### Post by Azathoth_ on 2007-04-18
Ahh, that is the reason why it doesn't work for me with coriander :(

Thanks again

---

