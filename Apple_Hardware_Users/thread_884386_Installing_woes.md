---
title: "Installing woes"
date: 2008-08-08
forum: Apple Hardware Users
---

### Post by denzellow@mac.com on 2008-08-08
I have searched the forums all with the same problem as mine, but there are no solutions. So I'll just ask it here. Please forgive me as I am new. I partition my disk using bootcamp and boot up from the ubuntu install disk to install it. Everything goes on smoothly, the only part which I hate is the partitioning. I'm very lost as to how to do it. Can someone please tell me how. I really want to run Ubuntu, but I just find it difficult to. TIA!!!

---

### Post by cyberdork33 on 2008-08-09
> **denzellow@mac.com said:**
> I have searched the forums all with the same problem as mine, but there are no solutions. So I'll just ask it here. Please forgive me as I am new. I partition my disk using bootcamp and boot up from the ubuntu install disk to install it. Everything goes on smoothly, the only part which I hate is the partitioning. I'm very lost as to how to do it. Can someone please tell me how. I really want to run Ubuntu, but I just find it difficult to. TIA!!!
If you used the bootcamp assistant to create a partition for windows (resizing your OS X partition) then, 

[LIST=1]
[*]just boot the Ubuntu LiveCD and
[*]start the partition editor (gparted) under the system menu...
[*]then delete the Windows partition (should be the 3rd) and
[*]click apply.
[*]Then start the Installer and when prompted choose to install to the largest free space!
[*]that's it!
[/LIST]

---

### Post by sandysandy on 2008-08-09
there is one more utility called gparted for partitioning 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

the tutorial is 

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

always remember to backup data ( & defragment windows) before partitioning. 

regards

---

