---
title: "bluetooth dial up networking and cingular"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-09-17
is anyone out there using cingluar for bluetooth dial up networking? (DUN)  Where do i put the username, password, etc?  I know where to put the phone number to dial (see below)




/etc/ppp/peers/gprs.chat


TIMEOUT                 15         
ECHO                    ON 
HANGUP                  ON       
''                              AT 
OK                              ATZ      
OK                              ATD(phone number here)

---

### Post by linuxwizard on 2007-09-17
See if this will help

[https://help.ubuntu.com/community/BluetoothDialup/Cingular](https://help.ubuntu.com/community/BluetoothDialup/Cingular)

[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

---

