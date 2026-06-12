---
title: "I cant boot Win7 from dual boot."
date: 2015-06-19
forum: Any Other OS
---

### Post by sam138 on 2015-06-19
I cant find any options to boot Windows from my boot menu. I Partitioned 200gb for my linux and installed from a usb. I am now only able to boot linux and have no option to boot my partition with windows installed.

---

### Post by Bucky Ball on 2015-06-19
Welcome. Boot into Ubuntu, open a terminal and type:

```
sudo update-grub
```

Let it roll until it's back at the cursor. Reboot. Any luck?

Are you sure you haven't wiped Windows? Boot from live Ubuntu install media, choose 'Try Ubuntu', launch Gparted and look for the Win partition (NTFS filesystem). Post a screenshot here if you like.

---

### Post by Ashley_Scopes on 2015-07-02
If you want to restore the Windows bootloader, boot a windows recovery or installation disk for the version of windows you are using, select repair, open a command prompt and run bootmgr /fixmbr and then reboot. You could then try installing easybcd in Windows...there is an option to install GRUB in that program iirc.

Read up on how to do this properly first, I am writing this from memory only. I would suggest you try the first posters method unless you need to specifically boot into Windows to fix it :)

---

