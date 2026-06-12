---
title: "To remove or not to remove Lilo fm MBR??"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by jobrimal on 2005-12-04
Hello, I am a newbie in Linux,not too bad in windows!! I have XP on my maindrive
with LILO in the MBR.On my secondary drive I have Mandrake 10.1.Ok they both work satisfactory.HOWEVER I wish to uninstall mandrake, and install Ubuntu onto
my secondry drive.
              Will I have to remove Lilo from my Main Drive MBR before installing Ubuntu 5.10???
               If so HOW?????[http://ubuntuforums.org/images/smilies/rolleyes.gif](http://ubuntuforums.org/images/smilies/rolleyes.gif)
:rolleyes:
 Will appreciate any help.

---

### Post by linbetwin on 2005-12-04
You don't have to uninstall Mandrake. Just install Ubuntu on the Mandrake partition. During the installation of Ubuntu, you will be asked whether you want to install GRUB in the MBR. Choose "Yes" GRUB is a bootloader similar to LILO and will allow you to boot into Ubuntu of Windows.

---

