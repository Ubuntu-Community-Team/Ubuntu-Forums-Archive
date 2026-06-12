---
title: "Several Questions"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-08-24
I apologize in advance for not making much research, but I would like to ask some problems I'm likely to face during my early use of Ubuntu.

1) Phone Modem.  I have checked out the LinModem website, and by dear sake, I wish all those store boxes labeled the chips each Modem are using.  For those "left behind" in the stone age, what Phone Modem would you suggest I buy?  Or are they "all the same"?

2) Virtual Machine?  While I'm guessing VMWare would be the answer to this, I just had to make sure: I plan to dual-boot Vista with Ubuntu, but because restarting the computer to open the other OS is such a hassle, I wondered if there was some program that can simulate actions in different partitions.  i.e. I can run Windows programs (such as mediaplayer.  Too lazy to convert all those MP3 to OGG) in Ubuntu, and vice versa.

3) Installing from tar ball.  I'm terribly addicted to Ruby, Rails and IRB, but it turns out mine didn't come with it's own.  I know that there's a tar ball some where to download this library, but once I have that, what am I to do with it?  A simple step-by-step Unix command display will help.

4) Perl man pages not present.  While the main Perl interpreter, library, and main man page is there, I don't seem to have the perlintro, perlfaq, and other perl tutorial library and man pages.  Where can I download them?

Hey, thanks for all the help!

---

### Post by japtar10101 on 2007-08-24
Heh, I just found out how to download Ruby :-P

```
% sudo apt-get install ruby irb rdoc
```

Regardless, I'd like to know how to install off of a tarball, in the case I ever have to face it.  Thanks.

---

### Post by milosz.galazka on 2007-08-24
1) [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) ?
2) I am using amarok, kaffeine for media like movies, music. MP3 works in ubuntu.
If you are searching for virtualization software then check out vmware, qemu, xen.
3) You found answer :)
5) maybe ```
sudo apt-get perl-doc
```

---

