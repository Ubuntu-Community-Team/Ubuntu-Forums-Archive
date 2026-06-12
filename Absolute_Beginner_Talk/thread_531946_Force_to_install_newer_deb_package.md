---
title: "Force to install newer deb package"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by aitorcalero on 2007-08-22
I would like to install a newer deb package through GDebi. But when I try to install it, it tells me that other packages will be removed and I don't want that. Just only want to upgrade current installed version.
How can I do this?
PS: I am pretty sure that those dependent packages will work fine with newer version.

---

### Post by rahimveron on 2007-08-22
I dont think there would be any problem. It will remove the old version and install the new version. Why do you worry? Go ahead. Dependencies will automatically be downloaded. So dont worry

---

### Post by AlexenderReez on 2007-08-22
force install is really dangerous......hm....make sure you don't other way before do it..just

>  sudo dpkg --force-overwrite -i  <packagename>

force with overwrite anything than prevent package to be install....

---

### Post by aitorcalero on 2007-08-22
> **rahimveron said:**
> I dont think there would be any problem. It will remove the old version and install the new version. Why do you worry? Go ahead. Dependencies will automatically be downloaded. So dont worry

But GDebi advice me that other packages will be removed, and it seems that the new one does not handle this dependencies. I mean it seems that the old one, has dependencies attached but not the new one, because it is an customized version.

---

### Post by aitorcalero on 2007-08-22
> **AlexenderReez said:**
> force install is really dangerous......hm....make sure you don't other way before do it..just

force with overwrite anything than prevent package to be install....

Is there any way to test this command without really executing it, to simulate what will happen

---

### Post by Jimmyfj on 2007-08-22
Why not just install the full packet? An upgrade is also made for the dependencies. Not just the main program.

---

### Post by aitorcalero on 2007-08-22
I don't understand. I have downloaded a new modified version of a deb package which is already installed in my system. But when I try to install it Gdebi informs that other packages will be unistalled.
Thank you all, anyway, I will give a try to --force :O

---

### Post by schorsch on 2007-08-22
You can start the dpkg command with the additional parameter "--dry-run|" so you can test what it will do.

---

