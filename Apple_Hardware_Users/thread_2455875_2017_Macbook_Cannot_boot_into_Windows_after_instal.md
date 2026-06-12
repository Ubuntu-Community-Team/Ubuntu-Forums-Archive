---
title: "2017 Macbook Cannot boot into Windows after installing Ubuntu; boot-repair"
date: 2020-12-29
forum: Apple Hardware Users
---

### Post by joel-joelburton on 2020-12-29
I have a 2017 Macbook Pro (14, 1), running OSX and Windows via Bootcamp. Prior to installing Ubuntu,I could boot into Windows.

After installing Ubuntu 2020.10, I have the following experience:

- if I press nothing while booting, I get the GRUB menu [in a ridiculously tiny font because of Retina display]. Choosing Ubuntu [first + default, works fine]: my Ubuntu desktop works great :KS

- If I choose the third option, Windows, my screen goes blank and hangs

- If I hold down ESC during power on, I get a graphical display of 2 drives (I believe this is my UEFI startup menu?). Choosing Apple boots me into OSX Fine.

- If I hold down ESC and choose Windows, I get some text and boot into Ubuntu.

Before installing Ubuntu, I used gparted from the USB to shrink my NTFS partition, and installed Ubuntu on that new partition.

I tried boot-repair with the default options; this didn't change anything, but I do have this report: [https://paste.ubuntu.com/p/SZGCmsw9sX/](https://paste.ubuntu.com/p/SZGCmsw9sX/)

Any advice will be very appreciated. Thanks!

---

### Post by joel-joelburton on 2020-12-29
I can mount my NTFS drive under Ubuntu, if that's helpful.

---

### Post by oldfred on 2020-12-29
Moved to Apple sub-forum where those with a Mac may be able to help.

Do not know Mac, but have seen a lot of Mac users use rEFInd.
rEFInd on newer MAC with Secure Boot
[https://sourceforge.net/p/refind/discussion/general/thread/1a96f5bd6d/?limit=25](https://sourceforge.net/p/refind/discussion/general/thread/1a96f5bd6d/?limit=25)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

