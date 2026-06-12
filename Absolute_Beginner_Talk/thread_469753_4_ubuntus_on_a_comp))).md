---
title: "4 ubuntus on a comp:)))"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by yeshe_tsogyelma on 2007-06-10
Hi,

I installed ubuntu 6.06 and I thought it was not installed, but I have it like 4 times...now...I used one of the ubuntus and mounted everything there...etc....on the same comp I have Windows as my mother uses it.
When I restart the comp I have to choose between 4 ubuntus and windows:)
I know the one I used most is the ubuntu above:)
But still...how can I exactly uninstall the other stuff???

---

### Post by Nakkis on 2007-06-10
They're not different Ubuntus, they're just 4 different kernels. (a kernel is the "heart" of an OS"). Just use the newest one (in the top) if it doesn't give you any problems. The other kernels are simply left there if there are any problems with a newer kernel versions on your PC.

Ubuntu keeps automatically the 4 newest kernels and deletes the older ones so you don't have to worry about it at all.

---

### Post by Bachstelze on 2007-06-10
4 Ubuntus ? What do you see in your GRUB menu, exactly ?

---

### Post by yeshe_tsogyelma on 2007-06-10
Thank you:D

---

### Post by yeshe_tsogyelma on 2007-06-10
I previously had ubuntu and windows installed. I reinstalled windows and when I restarted I couldnt see any ubuntu...so I didnt know what happened, and reinstalled a brand new ubuntu...
Now when I have to chose between the operational system i have , as Nakkis said , more kernels.

---

### Post by KIAaze on 2007-06-10
> I previously had ubuntu and windows installed. I reinstalled windows and when I restarted I couldnt see any ubuntu...
That's because Windows overwrites the MBR (Master Boot Record).
There are ways to prevent having to reinstall Ubuntu again like backing up the MBR and then restoring it.
Another way is to do several manipulations using the [system rescue CD]("http://www.sysresccd.org/Main_Page") for example.

Windows is xeno-OS-phobic. ^^
It doesn't like living with other OSes by default.

If you try other GNU/Linux distros, you will see that they are much friendlier and even add their entries to your Grub menu. :) (except that the menu.lst file is then on the partition of the new distro)

---

### Post by ryanVickers on 2007-06-10
> and reinstalled a brand new ubuntu...
Now when I have to chose between the operational system i have
sounds like you have 2 ubuntu's, with 2 kernals each.  For future reference, I don't believe the first ubuntu was gone, just had grub removed because of windows.  I think there's a way to add it to C:\boot.ini, but not sure exactly how!

---

### Post by yeshe_tsogyelma on 2007-06-10
Yes, as i said before in my first post, I used one of the ubuntus and mounted everything there, I meant the old ubuntu:)
I customized it and all...I just didn't know what happened with my ubuntu after I reinstalled the windows thing:)
That's why i reinstalled ubuntu, and now if I want I can see the brand new ubuntu too, nothing mounted there:)
That's why I was interested if I can remove it somehow, because I thought it eats some space, but if it's not necessary, I won't:)

---

