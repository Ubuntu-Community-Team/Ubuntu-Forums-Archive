---
title: "Restore MBR on Windows HD"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-05-03
Well....I really don't seem to be able to handle this linux thing. So maybe I'll just give up. The problem is the primary master has it's MBR altered by grub to allow to choose the boot. So, If I decide to quit Xubuntu, how do I restore the boot to normal? How do I restore the MBR?

---

### Post by alienexplorers on 2007-05-03
The program you need to run is fixmbr from your windows disk.

---

### Post by Ganda_Melga on 2007-05-03
> **alienexplorers said:**
> The program you need to run is fixmbr from your windows disk.


Thanks a lot for your help! It's going to be hard going back to Windows...

---

### Post by louieb on 2007-05-03
After you try VISTA You'll be back. [How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

### Post by medya on 2007-05-03
you can use Norton PQ boot .
after you installed vista, come back to ubuntu ! wink

---

### Post by neodarksaver on 2007-05-03
just instal another linux, Grub or lilo will be back.

---

### Post by Ganda_Melga on 2007-05-04
The funny thing is like Ubuntu! But I am a bit discouraged, seems to difficult to me. In another of my threads another member suggested Linux is not right for me. I'm a little bit lost. 


Anyway, thanks for your help! :popcorn:

---

### Post by Ganda_Melga on 2007-05-04
> **neodarksaver said:**
> just instal another linux, Grub or lilo will be back.

Nah! I love this Ubuntu stuff. I think I'll give up on linux, so I won't install another distro of linux.

---

### Post by Ted Nancy on 2007-06-07
I had a similar problem. An OEM vista disc from HP, no restore partition to work with, and no desire to just restore factory default.

Here is what worked for me:

Download MbrFix.exe from [www.sysint.no](www.sysint.no) (click the downloads link, and read over the readme link beside the download link to the file.)

Then do from Vista:

>Start >Accessories and right-click "command prompt" and then choose "run as administrator"

Then type (without quotes):

"MbrFix /drive 0 fixmbr /vista"

And reboot. Grub should be gone and Vista should boot normally. If not, you'll have to review the documentation. It could be that drive should not = 0.

Once Vista boots normally, go to control panel and use the disk management utility to delete the non-windows partitions. Reboot again. Then use the same utility to expand the Vista partiiton to full size of hard disk.

Best,

---

