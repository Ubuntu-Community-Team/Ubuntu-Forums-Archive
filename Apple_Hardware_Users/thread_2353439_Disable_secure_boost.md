---
title: "Disable secure boost?"
date: 2017-02-21
forum: Apple Hardware Users
---

### Post by ryanliyikun on 2017-02-21
I installed Ubuntu on my mac as a dual system. When I run the script  that patch and install Uvcvideo, I got the error :

modprobe: ERROR: could not insert 'uvcvideo': Unknown symbol in module, or unknown parameter (see dmesg)
Failed to insert the patched module. Operation is aborted, the original module is restored
Verify that the current kernel version is aligned to the patched module version


 dmesg : [ 3233.439976] uvcvideo: Unknown symbol media_entity_create_link (err 0)
[ 3233.440057] uvcvideo: Unknown symbol media_entity_init (err 0)
[ 3233.440100] uvcvideo: Unknown symbol media_entity_cleanup (err 0)


 I got the same error when I tried to install it on a windows/Ubuntu  dual system machine. I solved it by disable secure boost with command  below:
sudo apt install mokutil
sudo mokutil --disable-validation


 It worked. However, it does not work on my mac. When I tried to run the commands. It says:

This system does't support Secure Boot

What should I do to solve this ?
Thank you!

---

