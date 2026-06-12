---
title: "Joost via VMWARE ..."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-11-25
I tried to get Joost to work via VMWARE using this:

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

but all I get is a black screen.

Anyone know how to get Joost to work using VMWARE?

Thanks

Carl

---

### Post by nidelius on 2007-12-06
You have to enable DX9 and install DX 9 in vmware. I run VMware workstation 6.0.2 build-59824.
It's currently an unstable thing and I have noticed that you can not minimize vmware when running this feature. What you need to do first is to make sure your graphic card is installed correctly in k/ubuntu. After that you need to enable 3D in VMware. Make sure your XP machine is TURNED OFF and not in any suspended mode. Then add the following to your /home/user/vmware/machine/machine.vmx file

```

svga.maxWidth = "1600"
svga.maxHeight = "1200"
svga.vramSize = "67108864"
mks.enable3d = TRUE

```

After this start up your XP machine and run directX9 installer (download here) [http://filehippo.com/download_directx/](http://filehippo.com/download_directx/)

After this install joost. And you should be good to go. The DirectX9 feature is as I mentioned in a testing stage and does not work 100% with DX9 so I have noticed some bugs with transparant stuff. Like for example I can't se witch channel I'm choosing. But anyway you can play joost in vmware thats great! :D

Here is a screenshot how it looks. Sad enough the channels does not appear. But its working :D
[[IMG]http://s1d2.turboimagehost.com/t/34098_joost.png[/IMG]](http://www.turboimagehost.com/p/34098/joost.png.html)

---

### Post by cwmoser on 2007-12-06
I tried to get Joost to work on my vmware setup but it won't work.

Carl

---

### Post by nidelius on 2007-12-06
Are you using vmware workstation?. Or server? I don't think the server version is working with 3D setup.Have a look here [http://ubuntuforums.org/showthread.php?t=84344](http://ubuntuforums.org/showthread.php?t=84344)


EDIT: You can also try dxdiag in windows after you have installed everything so check if direct X is enabled

---

