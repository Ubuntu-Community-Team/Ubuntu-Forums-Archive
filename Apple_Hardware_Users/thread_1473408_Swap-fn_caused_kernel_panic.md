---
title: "Swap-fn caused kernel panic"
date: 2010-05-05
forum: Apple Hardware Users
---

### Post by shirsoft on 2010-05-05
I have Ubuntu 9.1 installed on my macbook pro. I was trying to switch the behavior of fn-key when I came across this post.

[http://www.rickycampbell.com/swap-fn/]("http://www.rickycampbell.com/swap-fn") which asks you to do the following 3 steps
> 
First edit /etc/modprobe.d/options
sudo nano /etc/modprobe.d/options
 and make sure it has the line
options hid pb_fnmode=2
 Then save and exit. Lastly, we need to update ramfs:
sudo update-initramfs -u -v -k `uname -r`
After I rebooted I got Kernel panic saying something like unable to mount VFS at 0 and something related to missing ram image.

Please help, I spent quite some time setting up my ubuntu and dont want to do it again.

---

