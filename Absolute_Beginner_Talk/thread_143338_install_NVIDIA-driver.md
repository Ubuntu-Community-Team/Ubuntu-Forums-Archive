---
title: "install NVIDIA-driver"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by aerypton on 2006-03-12
[driver for GeForce 6600]("http://www.nvidia.com/object/linux_display_ia32_1.0-8178.html")

I want to install the video-driver (to be able to use 2 screens). I follow the steps shown on the NVIDIA-site (link above). On step 3, everything goes well until ubuntu says I have to run it as a root. But there is no root in Ubuntu, is there?? :rolleyes: 

Who can help me further?

---

### Post by astoltz on 2006-03-12
The command 'sudo -s' followed by your password will get you a root prompt.

---

### Post by aerypton on 2006-03-12
thank you!!

---

### Post by aerypton on 2006-03-12
Next problem is the X-server. Thisone should be shut down. 
How do you do it? :-k

---

### Post by patrick295767 on 2006-03-12
to shutdown the X-server : 
```
sudo /etc/init.d/gdm stop
```
  
to start it : 
to shutdown the X-server : 
```
sudo /etc/init.d/gdm start
```

(if you are using kdm, plz replace gdm with kdm)

Greetz
====
(to reconfigure ur xserver-xorg:
> dpkg-reconfigure xserver-xorg)
(nv for nvidia )

---

