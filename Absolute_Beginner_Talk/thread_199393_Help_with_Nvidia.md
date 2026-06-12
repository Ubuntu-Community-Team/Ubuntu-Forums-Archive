---
title: "Help with Nvidia"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2006-06-18
I have searched the forums and I didn't see this error anywhere else.  Any help would be great, and sorry if this has already been posted.

I enter this
 > apt-get install nvidia-settings nvidia-glx linux-restricted-modules-386

and I get this
> Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
linux-restricted-modules-386 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Conflicts: nvidia-settings but 1.0-3ubuntu7 is to be installed
E: Broken packages


---

### Post by nalmeth on 2006-06-18
you can leave out nvidia-settings if you just want to get 3D going. It's not needed for 3D-Acceleration

---

### Post by u.b.u.n.t.u on 2006-06-18
Three steps to install Nvidia 3D on ubuntu 6.06.

1.
```
 sudo apt-get install nvidia-glx linux-restricted-modules-`uname -r`
```

2.
```
sudo nvidia-xconfig
```

3.
reboot.

Please see my wiki page in my signature for more information.

---

### Post by tseliot on 2006-06-20
nvidia-settings conflicts with nvidia-glx because nvidia-setting is already included in nvidia-glx.

nvidia-settings (as a package) can be installed only by the ones who use nvidia-glx-legacy.

BTW here is my guide which I hope will make things a bit clearer:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

