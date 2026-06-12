---
title: "Wine Question"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by wana10 on 2006-05-02
hello everyone, I'm new not only to the ubuntu scene but the linux realm as a whole, i have found ubuntu to be the best of the distro's i have tried and and currently happy with everything going on. This forum thus far has been informative and helpful when i was searching for ways to make my wireless card work, but, alas, i have found myself in a problem with which the search button has been unable to help, and so i find myself braving the posting realm.
to the question. I added winehq as a repository, downloaded and installed the latest version of wine as well as the sidenet configuring device. Everything is good so far, however, whenever i try to install a windows program (even during sidenet when it was installing ie6) there is no text in the install windows. The windows, the buttons, everything has its same function but there is no text visible. This probably has a simple response and i thank you for your time. if more information is needed ask and i'll supply if i am able.

---

### Post by htinn on 2006-05-02
When you install Wine and then ran winecfg (which I assume you have done), the fonts should have been generated at that time. There may be an issue with fontconfig, however that appears from time to time.

If this is the case, you may wish to completely uninstall Wine (make sure you delete the ~/.wine folder as well) and install an older version. Older versions are available here:

[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803)

Let me know if you need further instructions on this.

---

### Post by wana10 on 2006-05-02
i was following the instrunctions from the apress beginning ubuntu linux book and there was nothing in there about a winecfg. how do i go about running this?

*edit* i found out how to run winecfg (just type winecfg in terminal *idiot me*) however it return with the same problem as all the windows programs, that is menu and buttons and options appear, no readable words. when this happens the terminal displays

libGL warning: 3D driver claims to not support visual 0x**

with numerous identical returns except the ** is a series of numbers and letters, different for each line.

---

### Post by htinn on 2006-05-02
Looks like you'll need to go back to 0.9.11 or 0.9.10.

To install that, download from that page I linked to previously and type this in a terminal:

```
sudo dpkg -r wine
sudo dpkg -i wine_0.9.11-winehq1-1_i386.deb
winecfg
```

That may fix the problem you're experiencing.

---

### Post by wana10 on 2006-05-02
thank you very much, that solved the font problem perfectly...however, new problems arise. in winecfg when i click on the drives tab it tells me that i dont have a c drive and to click on the add drive to make one. so i do. then i give the c drive a path of /home/c and click apply and ok.
then i re-enter winecfg and it tells me again that their is no c drive. what do i do?

---

### Post by wana10 on 2006-05-02
just in case its needed, heres my terminal output 

```
@ubuntu:~/Desktop$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0

```

as i said in my last post, all fonts are working this time, however i have no drive c and cannot seem to create one

---

### Post by htinn on 2006-05-02
You may need to remove the old ~/.wine folder. To be sure, do it like this:

```
sudo rm -rf ~/.wine
winecfg
```

Hopefully, that won't destroy too much data. :p

---

### Post by wana10 on 2006-05-02
uninstalled wine, removed .wine folder, reinstalled wine...

and everything works like a charm. thanks for all your help htinn

---

