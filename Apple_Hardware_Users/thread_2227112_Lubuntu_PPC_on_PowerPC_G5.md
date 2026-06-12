---
title: "Lubuntu PPC on PowerPC G5"
date: 2014-05-30
forum: Apple Hardware Users
---

### Post by Matthew_Portner on 2014-05-30
First off im no rookie here to any os! run everything from bsd to macos linux and windows because wife insists and Haiku(beos). Heres my issue

I boot Lubuntu PPC 14.04 LTS just fine from usb install it let it automatically take over hd i check it creates hfs partition swap and ext4. When installation completes successfully i have continue testing/restart when i restart live kernel panics on shutdown. ok no biggie power off powerpc by holding power for 10 seconds let it boot. i can tell its trying to find os. then my boot line appears i hit enter for default i get the mac file icon showing no os to boot?? Any idea what went wrong here?

---

### Post by Matthew_Portner on 2014-05-30
Please go ahead and move to apple users forum i didnt see it till after i posted.

---

### Post by bapoumba on 2014-05-30
Done.
*Thread moved to **Apple Users**.*

---

### Post by Denis_Roy on 2014-05-30
My experience is limited, but ran in the same problem, I removed all of the partitions and re-installed and everything worked, booting up that is. Next step, is the problem for me. I would like to know if you can access the GUI, because I can't.

---

### Post by Matthew_Portner on 2014-06-01
I've removed partitions and reinstalled them 3 times no go. I haven't tried 12.04 so maybe ill try that if it boots then maybe ill try a dist-upgrade to lts

---

### Post by Matthew_Portner on 2014-06-01
ok so i got it booting by installing 12.04 then i set it to 14.04 repos did a dist-upgrade rebooted to a scrambled/tiled screen is that the problem you were having  Denis_Roy? So the next issue now to fix. i cant get it to boot from command to set say vesa dsisplay though either?? is there a way on ppc edition?

---

### Post by Denis_Roy on 2014-06-03
Its a video problem, If you have the same hardware we may be talking about a driver problem. I have a [Power Macintosh G5 2.0 DP (PCI-X)]("http://www.everymac.com/systems/apple/powermac_g5/specs/powermac_g5_2.0_dp.html") 7.2, the video card is a nvidia. My guess its load the wrong driver or a buggy driver. Some one got to tell me how to change the driver. And why I think its that? Because someone else had a similar problem and added a ati card and it worked.

---

### Post by Denis_Roy on 2014-06-03
Been read up on xrandr, might be a question on detecting the viedo card property or the monitor. But the commands I'm trying are not working. I'm giving up tonight. I'll try something else later.

---

### Post by Matthew_Portner on 2014-06-03
Yeah i know its a driver issue. it is nvidia. its using nouveau driver. which is right but maybe needs updated to fix a bug or an older version of it idk for sure yet.

---

