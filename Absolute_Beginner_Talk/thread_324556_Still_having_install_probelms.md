---
title: "Still having install probelms"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Griffongob on 2006-12-23
Hi again all so I'm still having problems getting ubuntu to install. I get to where i login for the first time and then before i can enter my id the screen goes blank and then says that x server isnt working" Failed to start the x server(your graphical interface)
It is likely it is not set up correctly. Would you like to view the x server output to diagnose the problem?" I tried using the sudo dpkg-reconfigure xserver-xorg but when I get to where i choose what color I want for my display 1-24bit I choose 24 bit and it kicks be out of the reconfig saying that it could possibly overwrite some customized settings what should I do?[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

---

### Post by riven0 on 2006-12-23
> **Griffongob said:**
> Hi again all so I'm still having problems getting ubuntu to install. I get to where i login for the first time and then before i can enter my id the screen goes blank and then says that x server isnt working" Failed to start the x server(your graphical interface)
It is likely it is not set up correctly. Would you like to view the x server output to diagnose the problem?" I tried using the sudo dpkg-reconfigure xserver-xorg but when I get to where i choose what color I want for my display 1-24bit I choose 24 bit and it kicks be out of the reconfig saying that it could possibly overwrite some customized settings what should I do?[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

That's normal. It should overwrite your current xorg.conf file in order for the changes to be made. But it *will* back up your old file, just in case there is a problem. So go ahead and do it and to reboot
> 
sudo shutdown -r now



---

### Post by Griffongob on 2006-12-23
ok I'll give it a go

---

### Post by Griffongob on 2006-12-23
still didnt work I still get the same error](*,)

---

