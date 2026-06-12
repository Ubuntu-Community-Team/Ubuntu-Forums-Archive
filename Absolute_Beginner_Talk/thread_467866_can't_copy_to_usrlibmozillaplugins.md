---
title: "can't copy to /usr/lib/mozilla/plugins"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by kriiberg on 2007-06-08
i wanted to do all the necessary steps to run flash 9 on a 64 but when i tried pasting files into /usr/lib/mozilla/plugins it said that i have no premision to write in that folder the owner of the folder is specefied as root... can someone help me...

---

### Post by Big_Croc7 on 2007-06-08
Could you point to the instructions or tutorial you're using?  If you haven't got permissions you should be able to write to the folder by using the same command prefixed by 'sudo'.
E.g.
```
sudo cp mypluginfile.moz /usr/lib/mozilla/plugins/mypluginfile.moz
```

---

### Post by kriiberg on 2007-06-08
im using these instructions [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727) 

thx ill try that

I tried that did not work it spits out :
~$ sudo cp flashplayer.xpt /usr/lib/mozilla/plugins/flashplayer.xpt
Password:
cp: cannot stat `flashplayer.xpt': No such file or directory

---

### Post by Big_Croc7 on 2007-06-08
The 'cannot stat' error mean's it can't find the file to copy - you need to be in the directory where the file is, or give the full path.  If for example, you unpacked it into the folder install_flash_player_9_linux you'd use
```
cd
sudo cp install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins/flashplayer.xpt
```
note that if you start the path with / then it's relative to the root directory, but if that's missing it's relative to the current folder (which can be found with 'pwd').

---

