---
title: "Asus partitions"
date: 2011-12-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Canaryguy on 2011-12-04
Hello,

A friend has bought an Asus netbook and it comes with the partitions shown in the file that I have attached. Is the partition sda4 necessary? I'd like to delete it because I want to create a partition for Ubuntu.

Thanks.

---

### Post by tartalo on 2011-12-04
sda4 is an EFI partition used by boot boost, if you remove it you can create it again later, the content is written by the BIOS

---

### Post by Canaryguy on 2011-12-05
How can I create an EFI partition later if I delete it? What happens when you delete it? Does something stop working?
But in any case, would it be better if I delete the partition sda3 (that seems to be used to store user's data) and to create then two extended partitions one NTFS and the other for Ubuntu?

---

### Post by tartalo on 2011-12-05
When you boot the computer the BIOS takes a couple of seconds. With Boot Booster, if nothing changed in the BIOS since last boot, this time is skipped (You see GRUB immediately). Boot Booster uses that 16MB EFI partition to store information.

If you delete the EFI partition Boot Booster doesn't work, but it's very easy to create a new one:
[http://ubuntuforums.org/showthread.php?t=1025920](http://ubuntuforums.org/showthread.php?t=1025920)

sda3 is supposed to be where Windows will store your documents. I deleted sda3 completely and didn't notice anything strange in Windows.

EDIT: But in your case you seem to have some information there. Maybe you already used the computer with Windows?

---

### Post by Canaryguy on 2011-12-06
Thanks tartalo, I kept the EFI partion and deleted the sda3 partition that was intented to store the user's data in Windows.

Well, I had a little nightmare but in the end everything worked fine. I saved the Ubuntu ISO on a Pendrive using Unetbootin because this way is faster than installing using a CD/DVD. I connected the Pendrive and rebooted, then I pressed F2 to enter in the BIOS to put the Pendrive as the first device to be read, I saved the changes and rebooted. The system recognized the Pendrive but instead of seeing the usual menu of Unetbootin I saw a different one, something similar to GRUB with only three options: to try ubuntu without installing, to install it and another one that I don't remember. Had this something to do with EFI? hmmm... Well, In any case I created an logical partition for Ubuntu and Swap and another partition NTFS for Windows to store data. The installation of Ubuntu finished without problems I restarted and.... Nothing happened! Ubuntu didn't load, just Windows. Then I found out that after pressing F2 to set the Pendrive as the primary device to be read you have to press once the system is restating F12 and then I could see the Unetbootin menu and I made the same steps as before to create partitions and it worked.

---

### Post by tartalo on 2011-12-08
Glad to see that you did it :)

---

