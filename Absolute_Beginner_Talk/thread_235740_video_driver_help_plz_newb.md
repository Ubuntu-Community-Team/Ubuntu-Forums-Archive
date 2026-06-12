---
title: "video driver help plz newb"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by inmate#001 on 2006-08-13
i am trying to install the nvidia driver for my video card when i try to run it it says i have a x server running so i go to init 3 i try it again it says the same thing plz help o yeah 1 more question i can use sudo to run adminastrative comands but when i try to use su it keeps saying i have the wrong password during the install it dosent ask for a password for root i tried using my account password but that dosent work does the root password default out as something plz help

---

### Post by kebes on 2006-08-13
In answer to the second question, there is no root account in Ubuntu by default. You can create one if you need to, but unless you have a specific reason, don't do it.

You can use "sudo" to run root commands whenever you want. You can even use "sudo -s" to jump into a root console, effectively the same thing that "su" would accomplish. Just use the normal user password for your account (assuming it has admin power).


With regard to your driver problem: can you be more specific? You should be able to install the driver and then update your config files and reboot. At what point does it give an error? During boot? Please post the exact error.

---

### Post by sean_ on 2006-08-13
[http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Dapper#How_to_set.2Fchange.2Fenable_root_user_password)

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by inmate#001 on 2006-08-14
i tried the sudo apt-get install nvidia-glx nvidia-kernel-common comand like the tip tels me to and i get a error message saying that it cant find the file

---

### Post by Drakkor on 2006-08-14
It's available in Synaptic,assuming you have updated your sources list to include uninverse and multi-universe programs,just do a search for glx. :D

---

