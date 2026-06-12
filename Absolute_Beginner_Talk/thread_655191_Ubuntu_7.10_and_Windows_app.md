---
title: "Ubuntu 7.10 and Windows app"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by dewacorp.alliances on 2008-01-01
Hi all

I had a education program for kids running on Windows and i want to deploy this to Ubuntu.

At the moment on Windows, I have to use PowerIso and create a virtual drive and install the application from there. The virtual CD is loaded everytime the windows startup.

Now ... if I want to achive semilar thing in Ubuntu? How do I do this?  I did a bit a research on this and it suggests to use Wine application. Should I install the POWERISO under Wine first and install the Kids Education Program? Is there any better way?

Thanks

---

### Post by Dissel on 2008-01-01
If you need PC virtualization solution go for Virtual Box....It is simply great,

See Details here [http://www.virtualbox.org/](http://www.virtualbox.org/)

You can find it from Synaptic Package Manager,If your all repo are enabled.

If you need to run Windows Softies (.exe) then you have to install WIne.

---

### Post by kellemes on 2008-01-01
I think your best bet is to install Windows (assuming you have an install-disk) on a virtual machine like VirtualBox and then install the Kids Education Program on there.
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

I use this for a couple of WIndows apps I want to use from tux.

---

### Post by hyper_ch on 2008-01-01
And you don't need any third party application to load an ISO image.

Use this:

```

sudo mkdir /media/ISO
sudo mount -o loop -t iso9660 /path/to/file.iso /media/ISO

```

Now it's mounted and available in /media/ISO

---

