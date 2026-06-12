---
title: "Oxygen iconset for KDE3"
date: 2008-01-20
forum: Art &amp; Design
---

### Post by Bendemann on 2008-01-20
Here's a quiet actual iconset of Oxygen. I love these symbols and made a few changes to run with KDE3.

[http://rapidshare.com/files/85208191/oxygen.7z](http://rapidshare.com/files/85208191/oxygen.7z)

Copy to /usr/share/icons and select Oxygen in KControl.

---

### Post by Bendemann on 2008-01-20
Edit:

Pleasy type as su

```

#!/bin/bash
cd /usr/share/icons/oxygen
find ./ -name "mail_folder_sent*" -exec rename 's/mail_folder_sent/folder_sent_mail/g' "{}" \;
find ./ -name "document_open_folder.png" -execdir cp {} folder_open.png \;

```

---

### Post by Bendemann on 2008-01-22
Patch:

Run as su.

```
#!/bin/bash 
 echo Patching Oxygen. 
 cd /usr/share/icons/oxygen 
 find ./ -name mail_folder_sent.png -exec rename 's/mail_folder_sent/folder_sent_mail/g' "{}" \; 
 find ./ -name document_open_folder.png -execdir cp {} folder_open.png \; 
 find ./ -name applications_accessories.png -execdir cp {} package_editors.png \;       
 find ./ -name preferences_desktop_peripherals.png -execdir cp {} input_devices_settings.png \; 
 find ./ -name applications_development.png -execdir cp {} package_settings.png \; 
 find ./ -name system_users.png -execdir cp {} kuser.png \; 
 echo Done. 
 sleep 2
```

---

### Post by Bendemann on 2008-01-24
Patch:

```
#!/bin/bash
find ./ -name mail_folder_sent.png -exec rename 's/mail_folder_sent/folder_sent_mail/g' "{}" \;
find ./ -name system_suspend_hibernate.png -exec rename 's/system_suspend_hibernate/hibernate/g' "{}" \;
find ./ -name system_suspend.png -exec rename 's/system_suspend/suspend/g' "{}" \;
find ./ -name system_switch_user.png -exec rename -f 's/system_switch_user/switchuser/g' "{}" \;
find ./ -name system_lock_screen.png -exec rename -f 's/system_lock_screen/lock/g' "{}" \;
find ./ -name system_log_out.png -exec rename -f 's/system_log_out/exit/g' "{}" \;
find ./ -name reload.png -exec rename -f 's/reload/undo/g' "{}" \;
find ./ -name system_restart.png -exec rename 's/system_restart/reload/g' "{}" \;
find ./ -name document_open_folder.png -execdir cp {} folder_open.png \;
find ./ -name applications_accessories.png -execdir cp {} package_editors.png \;		
find ./ -name preferences_desktop_peripherals.png -execdir cp {} input_devices_settings.png \;
find ./ -name applications_development.png -execdir cp {} package_settings.png \;
find ./ -name system_users.png -execdir cp {} kuser.png \;
find ./ -name view_refresh.png -execdir cp {} reload_page.png \;
find ./ -name view_refresh.png -execdir cp {} reload_all_tabs.png \;
find ./ -name trashcan_empty.png -exec rename 's/trashcan_empty.png/trashcan_empty.png.bak/g' "{}" \;
find ./ -name trashcan_empty_alt.png -exec rename 's/trashcan_empty_alt.png/trashcan_empty.png/g' "{}" \;
find ./ -name trashcan_empty.png.bak -exec rename 's/trashcan_empty.png.bak/trashcan_empty_alt.png./g' "{}" \;

```

---

