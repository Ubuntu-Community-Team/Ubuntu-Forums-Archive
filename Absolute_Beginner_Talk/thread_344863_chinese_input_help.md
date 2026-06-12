---
title: "chinese input help"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by FANGBIN on 2007-01-23
hi everyone,
i just installed the following package for chinese input:

sudo apt-get install scim
sudo apt-get install scim-chinese
sudo apt-get install scim-config-socket
sudo apt-get install scim-gtk2-immodule
sudo apt-get install scim-tables-zh
wget -c [http://easylinux.info/uploads/fireflysung-1.3.0.tar.gz](http://easylinux.info/uploads/fireflysung-1.3.0.tar.gz)
sudo tar zxvf fireflysung-1.3.0.tar.gz -C /usr/share/fonts/truetype/
sudo chown -R root:root /usr/share/fonts/truetype/fireflysung-1.3.0/ 
sudo fc-cache -f -v

but after installation, i still can not input chinese, can anyone help me out?
i am using dapper and just updated

thanks

---

### Post by mikewhatever on 2007-01-23
It looks like you need to install some more stuff [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Chinese_Input_Method_.28SCIM.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Chinese_Input_Method_.28SCIM.29)

---

### Post by FANGBIN on 2007-01-23
sorry, there is nothing in the page you gived to me.

---

### Post by mikewhatever on 2007-01-23
Sorry if I was wrong, but it does say 'chinese input'
 ```
How to install Chinese Input Method (SCIM)

Please follow the official Ubuntu guide HERE
[edit]
How to install Desktop Applets (gDesklets)

Note: Program included in Automatix2. I you have already used Automatix2, this program may have been installed

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install gdesklets gdesklets-data
```

---

### Post by makan on 2007-01-23
> **FANGBIN said:**
> sorry, there is nothing in the page you gived to me.

perhaps you can review the link below:
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

---

### Post by FANGBIN on 2007-01-23
thank you guys, i've got work
&#35874;&#35874;

---

