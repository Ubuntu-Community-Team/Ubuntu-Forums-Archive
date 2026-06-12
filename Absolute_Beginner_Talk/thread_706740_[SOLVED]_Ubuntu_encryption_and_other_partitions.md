---
title: "[SOLVED] Ubuntu encryption and other partitions?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-02-24
I have Ubuntu Gutsy installed with encryption. I was wondering if there is anyway to make more partitions? I unfortunately need windows for some programs. I installed Windows Vista in VMware Server, but unfortunately that doesn't work completely correct and wont allow me to do what I need. So is there a way to make my computer a dual (or perhaps more) boot, but still have Ubuntu or all of it encrypted?

---

### Post by ipburbank on 2008-02-24
I have a dual boot system on my dell, but there are some tricks. First of all you have to install windows, then ubuntu because Windows isn't good with keeping ubuntu boot-able. When I did this I backed all of my data up to an external drive, then with the windows installer disk told it to wipe my drive. After that was done I switched CDs to the Ubuntu installer and when the partition settings comes up you tell it how much space to use, and it will make windows smaller. After the install is done and you reboot you get a screen asking which operating system to boot into! In ubuntu I moved all of my data back to my drive and ta-da, I was done!:)

I hope that this was helpful, Istvan.

---

### Post by slughappy1 on 2008-02-25
but will that allow me to use disk encryption?

---

### Post by Beefeater on 2008-02-25
Can you describe your computer-system?

Install windows and then ubuntu following this guide
[https://help.ubuntu.com/community/EncryptedFilesystemHowto8](https://help.ubuntu.com/community/EncryptedFilesystemHowto8)

But of course you would have to format your hard drive.

---

### Post by slughappy1 on 2008-02-25
I have a Dell Inspiron 1420n (the Ubuntu version). I re-installed Ubuntu using the Alternate CD for Ubuntu Gutsy 7.10. When using the alternate installation method you have an option to encrypt the hdd, but there is no option on how large to make it (it just uses the whole hdd). I want to know if there is anyway of making my computer a dual boot but still have encryption, at least on the Ubuntu partition.

If you would like more information on my computer (which I can't see why you would) I will post it

---

### Post by slughappy1 on 2008-02-25
So I found [this]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html") website that I think will work. It appears to be able to make more partitions (hopefully one that is not encrypted for Vista)

---

