---
title: "Need to re-install OS X"
date: 2007-06-11
forum: Apple PPC Users
---

### Post by soutpiel on 2007-06-11
I'm a complete newcomer to Ubuntu. I've just installed version 6.10 on my PowerPC - by wiping the HD and doing a clean install. I've realised this is a mistake and in fact I need to re-install OS X and partition the HD so that I can have OS X booting from one partition and Ubuntu from the other. 

I've found instructions on how to do this, but I have no idea how to boot from the OS X installer CD now that I have Ubuntu running. Help! I've tried the Mac technique of holding down the 'C' key while booting, but no result there, which wasn't a surprise. How do I do this with Ubuntu...?

Very grateful for any help...

---

### Post by thedarky on 2007-06-11
Hi,
From the ppc FAQs I found
[https://wiki.ubuntu.com/PowerPCFAQ#head-7e0d9b980507337bf9c80768cabb8396a552335c](https://wiki.ubuntu.com/PowerPCFAQ#head-7e0d9b980507337bf9c80768cabb8396a552335c)

which shows you the code to edit the yaboot configuration file to allow booting from CD.

hope this helps

---

### Post by soutpiel on 2007-06-11
Thanks for the quick reply!

I followed the steps in the FAQ file, which gave me the option to boot from CD as it should. However, I still have a problem. When I press the 'C' key when prompted, the text 'Booting from CD...' appears briefly, the screen goes black, then nothing more happens. When I do this using the Max OS X CD, the drive spits the CD out. I've also tried with the original Ubuntu installation CD that I used for my current installation, and although the disc doesn't get spit out, the black screen remains and nothing else happens. 

Does anyone have any ideas ...?

Thanks again.

---

### Post by thevenerablez on 2007-06-11
Do you have yaboot installed? When I installed Ubuntu on my Mac, yaboot was installed. Before the OS loaded, it said "press l for linux, x for mac os x, c for cd rom". If you have this option, press c and it will boot from the CD drive. You do not hold down the c key on startup, just press it when prompted.

_zach

---

### Post by soutpiel on 2007-06-11
thevenerablez,

Yes, I do get those options, but when pushing the 'c' key i get no further reaction - ie. the computer fails to boot from the CD, or anywhere else. It just freezes on a black screen indefinitely until I force a reboot.

---

### Post by pxwpxw on 2007-06-11
**soutpiel**

You should be able to boot from the macosx by holding the Option key with the macosx dvd in place and it will give you an icon to select.

---

### Post by soutpiel on 2007-06-11
Thanks to everyone for posting advice. I've eventually resolved the problem by simply trying many, many times with various Mac OS X install discs. Eventually one kicked in, for no apparent reason.

---

