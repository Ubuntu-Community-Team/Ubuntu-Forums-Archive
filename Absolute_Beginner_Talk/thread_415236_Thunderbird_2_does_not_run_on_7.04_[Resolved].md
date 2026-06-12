---
title: "Thunderbird 2 does not run on 7.04 [Resolved]"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by zhengw3 on 2007-04-20
I was trying to install Thunderbird on Feisty. There is only thunderbird 1.5 in the Feisty repository, so I downloaded the 2.0 from mozilla website, and it is supposed to run directly after decompression. I got it to run for the first time, and afterwards, it doesn't run anymore. I tried to run it in terminal, and saw an error message "Segmental fault, core dump". I don't know what this problem is. 

The version of my ubuntu is 7.04, the new release that was just out yesterday. Can anyone help me? Thanks a lot!

---

### Post by Nik_Doof on 2007-04-20
I've had it running last night without any major issues... please post the output from you running it in terminal, you could be possibly missing a lib or something.

---

### Post by zhengw3 on 2007-04-20
The output running it in terminal was a message "Segmental fault, core dump", and then nothing happened. It did run for the first time. Then I probably installed some other softwares (I don't exactly remember which softwares), and then tried to run thunderbird 2 again. It wouldn't work anymore. However, 1.5 runs with no problem.

---

### Post by zhengw3 on 2007-04-20
Figured it out. It is the problem of SCIM with Chinese input agian. Replaced SCIM with SCIM-bridge and thunderbird 2 runs fine.

---

### Post by clevin on 2007-04-20
> **zhengw3 said:**
> Figured it out. It is the problem of SCIM with Chinese input agian. Replaced SCIM with SCIM-bridge and thunderbird 2 runs fine.

did u uninstall SCIM and install SCIM-bridge? or still have SCIM installed?

---

### Post by clevin on 2007-04-21
I found this workaround is easier
>  Then just edit the startup script of firefox/mozilla etc, add one line in the beginning of the file (after the first line if it begins with #!/bin/sh):

export GTK_IM_MODULE=xim

---

