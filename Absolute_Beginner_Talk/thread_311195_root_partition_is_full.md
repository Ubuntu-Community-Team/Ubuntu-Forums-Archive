---
title: "root partition is full"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-12-02
here is  something I dont want to screw up.
My computer (dappler drake) started working in a wierd manner, then I notice that my root partition is full. my df -h result is given below.
I am not expert in linux and I am not sure what is the safest way to clean root. any help is highly appreciated. Thanks

mozkaynak@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             897M  896M     0 100% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  136K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hda5             3.7G   72M  3.5G   3% /home
/dev/hda1              55G   16G   39G  29% /media/hda1
/dev/hda7             449M  8.2M  417M   2% /tmp
/dev/hda8              14G  2.8G  9.9G  22% /usr
/dev/hda9             924M  720M  205M  78% /windows
/dev/hdc              697M  697M     0 100% /media/cdrom0
/dev/hdd              2.6G  2.6G     0 100% /media/cdrom1

---

### Post by zgornel on 2006-12-02
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
The root partition is way to small for a typical ubuntu install

---

