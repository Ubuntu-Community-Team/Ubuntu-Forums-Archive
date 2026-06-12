---
title: "wifi on a dell d600"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-05-18
just got a new[ish] dell d600 laptop. And, as ever, having problems with wifi.

I have followed [this](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html) guide, and even though someone on a d600 has succeeded, i am having no joy.

it appears that my laptop does not have centrino wifi, even though i was told it did... in device manager, i see broadcom corp. as the vendor of the wifi controller.

is it actually possible to get wpa support on here with that? ndiswrapper or something?

cheers, andy.

---

### Post by SuperAndy on 2007-05-18
ok, i have had a bash at ndiswrapper, using [this](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/) guide.

the guide seemed to work, untill the line starting sed...

i have the 3 files from the driver in the folder, and i cant see why this is going wrong.

any help, you would be a legend!

---

### Post by SuperAndy on 2007-05-20
ok, i do seem to just be the only one posting in my topic.

but anyway. I have installed broadcom drivers native in linux. I gave up on ndiswrapper in the end. I also installed wpasupplicant. And i do have wifi access. The only problem is, its a bit dodgy. I randomly get disconnected, and, rather weirdly, i can select all the WPA things if i go to "other wifi connection" in the little drop down menu from the network icon, but nowhere else.

I want a static ip, which involves doing the manual settings. but when i type my ssid, i only get WEP options in the security box. Is there just some conf file i need to update to redirect to the wpasupplicant files or something?

Or would a reinstall of network manager work? I am scared of trying anything though, because i am scared of messing up what fragile wifi i have. I suppose there is always a cable though...

Cheers

---

