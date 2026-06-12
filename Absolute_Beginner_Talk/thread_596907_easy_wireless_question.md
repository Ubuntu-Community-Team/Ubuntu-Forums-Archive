---
title: "easy wireless question"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-10-30
I have to run 

sudo ifconfig wlan0 up

everytime i start ubuntu so i can use my wireless.  How do i make this so I don't have to type 

sudo ifconfig wlan0 up

everytime.

Thanks

---

### Post by wieman01 on 2007-10-30
_Create startup script:_
> sudo gedit /etc/init.d/wireless-network.sh
_Add this line & save file:_
> sudo ifconfig wlan0 up
_Change permission (executable):_
> sudo chmod +x wireless-network.sh
_Create symbolic link:_
> sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/**[COLOR="Red"]S40[/COLOR]**wireless-network

---

