---
title: "Windows installer boots straight into windows"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by cmk_78212 on 2007-01-20
I downloaded the file from torrent, and everything was working fine.  When I restarted as prompted, I did not get the option to boot into window or ubuntu, it just booted straight to windows.  

The FAQ section on the wiki recommends:

Q. The bootloader doesn't show up at all, and it boots straight into windows

A. Make sure C:\boot.ini has a "timeout" value higher than 0, and that this is the last line: C:\grldr="Ubuntu" 

So I load up c:\boot.ini and notice that my time out value is 3, but that my last line reads:

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons.

I try adding C:\grldr="Ubuntu" to the end, but it won't let me save it.  It says:
cannot create bootfile.ini file, make sure path and file name are correct.  When I try doing a "save as", it says this file name exists as a read only file.  

I'm not sure what to do next

---

### Post by mikewhatever on 2007-01-20
Have you installed GRUB into MBR?

---

### Post by rai4shu2 on 2007-01-20
[http://www.ubuntuforums.org/showpost.php?p=2038895&postcount=256](http://www.ubuntuforums.org/showpost.php?p=2038895&postcount=256)

Please realize that this is a prototype and for testing only.

---

### Post by Hmarroqu on 2007-01-20
I have ubuntu and windoze on the same machine and the way i did it was to install windows first and leave sufficient space for ubuntu then i installed ubuntu.  When i boot, the grub comes out and allows me to choose, i do not choose then it boots straigt to ubuntu.  if this pertains exactly to the problem.

---

### Post by cmk_78212 on 2007-01-20
GRUB can be found on my C drive.  I assume that means it is installed.

The post from the other forum worked!

Now I get the "error 17: file not found" message.

The FAQ's say to defrag the hard drive.  I will see if this works.

---

### Post by cmk_78212 on 2007-01-20
Well, it got a little further along after the de-frag, but still came to the same error message.  Let me know if anyone has any ideas.

---

