---
title: "Is there a startup conf file i can edit..."
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by IAmALinuxFool on 2007-07-15
Hi,

I'm having some issues booting in to Ubuntu normally, i can just access the recovery mode. I installed then deleted libpam and when i try to boot in to Ubuntu i get a blue screen saying something like 'Can't find config file for pam', then it takes me to a command line where it prompts me to login but i can't (when i try it just says error immediate abort), so i was wondering if there's a startup config file or something similar i can edit so Ubuntu doesnt even look for a pam config file?

Thanks,

Dan.

---

### Post by Keen101 on 2007-07-15
we'll , I'm relatively new myself, so my input may not be helpful.


But, the only "startup" file I know of is /boot/grub/menu.lst


But that is only for GRUB. Not actually sure if that helps.


hope you get it fixed.  I guess if you had to you could just do a fresh install.


good luck :)
-keen101

---

### Post by IAmALinuxFool on 2007-07-15
Hi,

Thanks for the reply but i'm loking for a file (if one exists) that lists the processes that ubuntu starts on boot so i can remove pam from it. Yeah i can do a fresh install... but it's something i'm trying to avoid :)

Dan

---

### Post by Keen101 on 2007-07-19
Is >System >Preferences >Sessions what you are looking for?


-keen101

---

