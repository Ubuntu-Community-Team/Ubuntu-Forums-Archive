---
title: "Installing Ubuntu -&gt; error no 4.4 gb drive space"
date: 2011-09-11
forum: Apple Hardware Users
---

### Post by Sayck on 2011-09-11
Hello,

I'm having some trouble installing ubuntu on my macbook. (Running on Mac OSX 10.6 with memory of 4 GB).

I tried to install ubuntu via virtual box, but when i try to download ubuntu it says that i don't have 4.4 gb space drive available... DO I have to download an older version ? 

Can I do something about it ? 

Thank you,

Sayck

---

### Post by pytheas22 on 2011-09-11
It probably says that because the virtual hard disk you created in VirtualBox is smaller than 4.4 gigabytes.  Regardless of how much free space you have available on your actual Macbook's hard drive, Ubuntu running inside VirtualBox will only see a drive of whatever size you established when you set up the virtual machine.

You should be able to increase the size of the virtual hard disk in VirtualBox, or just create a new one.

If for some reason you can't make a virtual disk larger than 4.4 gigabytes, it should be possible to install Ubuntu with as little as about 2 gigabytes of space, but for that you need to install using the use the alternate CD rather than the live CD.  The live CD installer will refuse to work unless it finds at least 4.4 gigabytes of space.

There's no major difference in disk usage between different versions of Ubuntu; they all take up about the same.

---

### Post by Sayck on 2011-09-11
Thank you for your answer,
it finally worked :)

---

