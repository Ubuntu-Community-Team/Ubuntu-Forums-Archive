---
title: "dualbooting winxp+kubuntu 7.04 gets stuck"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by doron387 on 2007-10-07
i have installed dual booting of kubuntu 7.04 on 70Gb hd with winxp already exists, 

after the bar shows it moves a while, then disappears and nothing happens (blank screen, not totally black but undefinable obscure color, no blinking "_"), 
i tried all kinds of keyboard combinations but nothing stops it.

the cd was checked few times b4 installation for its origin and for its md5sum,the cd is OK. Ialso ran live sessions and it was ok.
 
 more details :

 when i ran live cd sessions a few times before the installation, i discoverd that if i just pressed start/install kubuntu (the first menu option) the bar showed, then blank, then another bar, then blank screen and from here it didn't comtinue...(same screen like now, after the installation)
                                                        but

 if i pressed F4, changed the resolution settings to 1024x768x32 it showed the bar, then blank, then bar, sounded beep when the second bar reached almost its end, then blank, then x appeared, then blue kubuntu screen etc....and everything worked well.
 
 so i came to understand that it all lies somewhere in setting the os to use 1024x768x32 resolution, but unfortunely, this F4 menu does not appear in the dual booting menu (at least i didn't find it)
 
 my machine is : laptop hp pavilion dv 6102 ea
 +mobile amd sempron 3400
 i386 family, 1.8 MHz
 nvidia geforce 6150 go, driver : nv4_mini.sys
 resolution 1280x800x32
 512 ram
 hd sata 70 Gb
 
 the istallation steps were : 
 1. totally recovering of the computer (after bad installation) - the comuter worked fine afterwards w/wnxp.
 1.5 defraged the windows hd.
 2. resized the win NTFS partition (made it small in 10 Gb) by GParted.
 3. ran the live cd session, everything was as usual (i did press F4->chose 1024x768x32->everything worked well)
 4. installed kubuntu using the option : "guided - use largest free consistent space in the disk"
 5. installation passed perfect untill the shut aown sequence which never in the previous sessions reached the end perfectly - i mean that after ejecting the cd, closing the cd tray and pressing enter it always freezed, and this time again so i had to forced shutdown.

---

### Post by jovannicabanag on 2007-10-08
> **doron387 said:**
> i have installed dual booting of kubuntu 7.04 on 70Gb hd with winxp already exists, 

after the bar shows it moves a while, then disappears and nothing happens (blank screen, not totally black but undefinable obscure color, no blinking "_"), 
i tried all kinds of keyboard combinations but nothing stops it.

the cd was checked few times b4 installation for its origin and for its md5sum,the cd is OK. Ialso ran live sessions and it was ok.
 
 more details :

 when i ran live cd sessions a few times before the installation, i discoverd that if i just pressed start/install kubuntu (the first menu option) the bar showed, then blank, then another bar, then blank screen and from here it didn't comtinue...(same screen like now, after the installation)
                                                        but

 if i pressed F4, changed the resolution settings to 1024x768x32 it showed the bar, then blank, then bar, sounded beep when the second bar reached almost its end, then blank, then x appeared, then blue kubuntu screen etc....and everything worked well.
 
 so i came to understand that it all lies somewhere in setting the os to use 1024x768x32 resolution, but unfortunely, this F4 menu does not appear in the dual booting menu (at least i didn't find it)
 
 my machine is : laptop hp pavilion dv 6102 ea
 +mobile amd sempron 3400
 i386 family, 1.8 MHz
 nvidia geforce 6150 go, driver : nv4_mini.sys
 resolution 1280x800x32
 512 ram
 hd sata 70 Gb
 
 the istallation steps were : 
 1. totally recovering of the computer (after bad installation) - the comuter worked fine afterwards w/wnxp.
 1.5 defraged the windows hd.
 2. resized the win NTFS partition (made it small in 10 Gb) by GParted.
 3. ran the live cd session, everything was as usual (i did press F4->chose 1024x768x32->everything worked well)
 4. installed kubuntu using the option : "guided - use largest free consistent space in the disk"
 5. installation passed perfect untill the shut aown sequence which never in the previous sessions reached the end perfectly - i mean that after ejecting the cd, closing the cd tray and pressing enter it always freezed, and this time again so i had to forced shutdown.

forget about windows.

go for UBUNTU!

---

### Post by hotweiss on 2007-10-08
> **doron387 said:**
> i have installed dual booting of kubuntu 7.04 on 70Gb hd with winxp already exists, 

after the bar shows it moves a while, then disappears and nothing happens (blank screen, not totally black but undefinable obscure color, no blinking "_"), 
i tried all kinds of keyboard combinations but nothing stops it.

the cd was checked few times b4 installation for its origin and for its md5sum,the cd is OK. Ialso ran live sessions and it was ok.
 
 more details :

 when i ran live cd sessions a few times before the installation, i discoverd that if i just pressed start/install kubuntu (the first menu option) the bar showed, then blank, then another bar, then blank screen and from here it didn't comtinue...(same screen like now, after the installation)
                                                        but

 if i pressed F4, changed the resolution settings to 1024x768x32 it showed the bar, then blank, then bar, sounded beep when the second bar reached almost its end, then blank, then x appeared, then blue kubuntu screen etc....and everything worked well.
 
 so i came to understand that it all lies somewhere in setting the os to use 1024x768x32 resolution, but unfortunely, this F4 menu does not appear in the dual booting menu (at least i didn't find it)
 
 my machine is : laptop hp pavilion dv 6102 ea
 +mobile amd sempron 3400
 i386 family, 1.8 MHz
 nvidia geforce 6150 go, driver : nv4_mini.sys
 resolution 1280x800x32
 512 ram
 hd sata 70 Gb
 
 the istallation steps were : 
 1. totally recovering of the computer (after bad installation) - the comuter worked fine afterwards w/wnxp.
 1.5 defraged the windows hd.
 2. resized the win NTFS partition (made it small in 10 Gb) by GParted.
 3. ran the live cd session, everything was as usual (i did press F4->chose 1024x768x32->everything worked well)
 4. installed kubuntu using the option : "guided - use largest free consistent space in the disk"
 5. installation passed perfect untill the shut aown sequence which never in the previous sessions reached the end perfectly - i mean that after ejecting the cd, closing the cd tray and pressing enter it always freezed, and this time again so i had to forced shutdown.

Try reinstalling it, but this time manually set up the partitions.

---

