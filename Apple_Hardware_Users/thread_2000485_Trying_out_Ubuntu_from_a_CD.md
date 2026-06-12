---
title: "Trying out Ubuntu from a CD"
date: 2012-06-09
forum: Apple Hardware Users
---

### Post by Penfold1971 on 2012-06-09
I'm preparing to build my own PC, with Ubuntu as the OS.
I've downloaded Ubuntu 12.04, and burned the ISO file onto a CD using Disk Utility, following the instructions on [http://www.ubuntu.com/download/help/burn-a-cd-on-mac-osx](http://www.ubuntu.com/download/help/burn-a-cd-on-mac-osx)
The CD contains a variety of folders and files.

I wanted to try Ubuntu out from the CD, but have failed at the first hurdle. I'm used to rebooting holding down the C key, but my current machine simply boots into its installed OS, Mac OS 10.4.11.
My machine is a G4 17" PowerBook (1.33 GHz). I do not want to install Ubuntu on this machine.

I can't believe I'm that incapable but am willing to have it demonstrated to me. Can anyone enlighten me as to what I'm doing wrong?

(I burnt two disks, one with the 64 bit version, the other with the 32 bit version. I'm trying to use the 32 bit disk with my PB.)

---

### Post by EuroCity on 2012-06-09
Your PowerBook has a PowerPC (32-bit) processor; so, you need this ISO:

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso)

... which should boot your Mac into the Ubuntu desktop.

There is also an alternate CD for PPC:

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-alternate-powerpc.iso)

... which, for example, one can use to install Ubuntu if the desktop CD doesn't work.

---

### Post by Penfold1971 on 2012-06-10
Thank you - that worked.
(I had a black screen with several lines of text to negotiate, and found I had to type in 'live' then press the Return key before before I got to the Ubuntu Desktop.)

As a further question, I had wanted to try out Ubuntu from a CD on my Intel iMac*, but again was confronted with a black screen where I had to indicate 'CD Rom type' at a prompt. Not knowing what to do, I powered off the iMac and ejected the CD. What would I need to enter at the prompt?

* iMac Intel Core 2 Duo, 2.4 GHz, 4 GB RAM, OS 10.6.8

---

### Post by Lars Noodén on 2012-06-10
For the Intel Mac, you'll need a different disc from the PowerPC Mac.  You can get it via the web or via Torrent, see AMD64+mac:

[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

---

### Post by Penfold1971 on 2012-06-10
Lars, I have actually burnt two other discs, in addition to the one I've now used on my PowerBook.

I got them from this page:  [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

At the time, I didn't know which version to download, so I downloaded both the 32 bit and 64 bit versions - hence the two other CDs.

Is Precise Pangolin the name given to version 12.04?

---

### Post by Lars Noodén on 2012-06-10
For the Intel Mac you should be able to run the 64 bit version, but the 32-bit will also work.

Yes, Precise Pangolin is an alternate name for 12.04.  Sometimes it's just called Precise.

---

### Post by Penfold1971 on 2012-06-10
I successfully tried out the 32 bit version from the CD on my Intel iMac. It looked pretty good - most certainly for what I have in mind.

The 64 bit version - well I got a black screen with the following displayed at top left:

 [B]    1.
     2.
Select CD-ROM Boot type: _[/B]

at which point I chickened out and powered off.

---

### Post by Penfold1971 on 2012-06-10
I should have added a question at the end of my last post:

Where I got:

[B]1.
2.
Select CD-ROM Boot type: _[/B]

What should I have typed at the prompt?

---

### Post by EuroCity on 2012-06-11
You should try with this CD, for a 64-bit Intel iMac:

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso)

(the ones you download from the main Ubuntu webpage are for "ordinary" PCs and virtual machines).

---

### Post by EuroCity on 2012-06-11
... See also here, for example:

[https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro)

... where they say:


*The regular 64-bit Ubuntu CDs have trouble booting on older Intel Macs, such as MacPro1,1, due to EFI incompatibilities. You must download a special +mac CD of Ubuntu to work-around this problem. [...] If you try to use a regular 64-bit Ubuntu CD on such systems, you may get the following blocking message while trying to boot off the CD:*

```
1.
2.
Select CD-ROM Boot type:
```

---

### Post by Penfold1971 on 2012-06-11
> **Lars Noodén said:**
> For the Intel Mac you should be able to run the 64 bit version, but the 32-bit will also work.

Yes, Precise Pangolin is an alternate name for 12.04. Sometimes it's just called Precise.
Thanks Lars for that info.

---

### Post by Penfold1971 on 2012-06-11
> **EuroCity said:**
> You should try with this CD, for a 64-bit Intel iMac:

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso)

(the ones you download from the main Ubuntu webpage are for "ordinary" PCs and virtual machines).

Thanks again, EC. That worked just fine.

I made a bit of a hash of getting a demo working on my two Apple machines, but got there eventually with a lot of help.

---

