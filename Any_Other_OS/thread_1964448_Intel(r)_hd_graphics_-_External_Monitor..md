---
title: "Intel(r) hd graphics - External Monitor."
date: 2012-04-24
forum: Any Other OS
---

### Post by hugom on 2012-04-24
Hi there, I just installed Linux Mint 12 and everything been going great until this really.

When I plug my toshiba l650 laptop into my external monitor the screen is fuzzy and I can't see much. My laptop resolution is 1366x768 and my monitor is 1920x1080. 

I went to the intel website and went to Linux drivers. This link - 

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3319&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&ProdId=3319&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A)

But I got a bit lost from there. Any help would be great. Do I need to download new drivers? I went to the additional drivers but that only installed one for my wireless card.

Thanks.

---

### Post by regor210 on 2012-04-24
I take it that you tried going to Preferences > Display Setting to make changes with no luck so your looking for a more updated video driver?

ubuntu-x-swat
ubuntu-x-swat is more stable
[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
$ sudo apt-get update
$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update
$ sudo apt-get upgrade

intel-gfx-testing
intel-gfx-testing is more stable than xorg-edgers
[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
$ sudo apt-get update
$ sudo add-apt-repository ppa:intel-gfx-testing/ppa
$ sudo apt-get update
$ sudo apt-get upgrade

xorg-edgers
xorg-edgers is for testing and can be unstable 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

$ sudo apt-get update
$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo apt-get update
$ sudo apt-get upgrade

If you try a ppa and find you don't need it, you can purge it.
$ sudo apt-get install ppa-purge
$ sudo ppa-purge ppa:xorg-edgers/ppa
$ sudo ppa-purge ppa:intel-gfx-testing/ppa
$ sudo ppa-purge ppa:ubuntu-x-swat/x-updates

---

### Post by hugom on 2012-04-24
Yes, that pretty much is what I am looking for. Newish to Linux so that's what I believe I need to do.

---

### Post by hugom on 2012-04-26
Anybody have any idea?

---

