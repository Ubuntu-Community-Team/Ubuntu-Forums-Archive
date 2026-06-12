---
title: "disable kdewallet"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by adhuvi on 2006-08-11
I'm using kopete under ubuntu dapper and chose to use kdewallet to store my password, but I don't want to use it anymore. How do I disable it?

thanks.

---

### Post by msak007 on 2006-08-11
You can disable kwalletmanager by doing the following:

1. Bring up kwalletmanager by double-clicking the wallet icon in your system tray.
2. Click on **Settings** --> **Configure Wallet**
3. Uncheck the box at the very top labeled "Enable the KDE wallet subsystem"
4. Click **Apply** / **OK**, right-click on the system tray icon, and choose **Quit**.

If you ever want to use the KDE wallet in the future, you can start it by typing **kwalletmanager** in the terminal (as there's no KMenu shortcut for it) and checking the box you unchecked to disable it. Also, you can prevent applications from using it by choosing "Always Deny" when prompted the first time the app tries to access the wallet. For example I disallowed kopete from accessing my wallet, but I still use it for knetworkmanager so it can store the password and connect automatically.

---

### Post by adhuvi on 2006-08-11
There isn't such an icon in my system tray, and when i type kwalletmanager, i get:

bash: kwalletmanager: orden no encontrada

Which is something like: order not found. 

I'm under gnome, any ideas?
thanks a lot

---

### Post by msak007 on 2006-08-12
That means it's not installed then. Are you sure you were prompted to store the password in kwallet? Gnome uses gnome-keyring by default...maybe someone can point you in the right direction for that as I'm not a Gnome user. Sorry I can't help more than that.

---

### Post by adhuvi on 2006-08-12
Sure it's kwallet:

"The a application 'kopete' has requested to open the wallet 'kdewallet'. PLease enter de password for this wallet below"

I loged in again to confirm that. But in synaptic kwalletmanager apears as nos installed. I'm going to try installing it first...

---

### Post by adhuvi on 2006-08-12
Solved. Intalled kwalletmanager with synaptic, reloged twice (first time kopete didn't responded well) and followed your instructions with the system tray icon. Worked nicely. 
Thanks a lot.

---

