---
title: "Share Musics and Photos between osx and ubuntu"
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by m84 on 2008-05-07
If it possible to access my itunes and iphoto library from my osx partition so that they are usable with say rhythmbox and f-spot? I dont particularly want copy all my files across, and have duplicates on each os.

I assume this would involve mounting the mac patition, but i dont know if this is safe to do, or if importing the libraries would cause issues in osx.

Thanks

---

### Post by phr0ze on 2008-05-07
Mounting the partitions should not be a problem. You can even mount it as read only.

Thanks,
John

---

### Post by frog_pilot on 2008-05-07
But you will run into problems because of file permissions if you are using the default storage locations in osx. the subfolders of the osx user folder are not permitted to open for others. if you are the only user of your mac, simply change the permissions for the subfolders in your user folder in osx.

then you will be able to mount the volume and access your files by klicking on it. the volume will mount as read only.

if you want to mount the volume read/writable, you have to turn off journaling on your osx volume.


//edit: maybe you have to install hfsplus and hfsutils first:```
sudo apt-get install hfsplus hfsutils
```

---

