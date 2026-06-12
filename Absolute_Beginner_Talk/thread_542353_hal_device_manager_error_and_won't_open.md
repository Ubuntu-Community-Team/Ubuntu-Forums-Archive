---
title: "hal device manager error and won't open"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Blue_T0oth on 2007-09-03
:~$ hal-device-manager
<gtk.Menu object (GtkMenu) at 0x8439734>
Traceback (most recent call last):
  File "/usr/share/hal/device-manager/DeviceManager.py", line 132, in on_device_tree_selection_changed
    self.update_device_notebook(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 20, in <module>
    DeviceManager()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 97, in __init__
    self.update_device_list()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 247, in update_device_list
    self.update_device_notebook(self.virtual_root.children[0])
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'


ne idea what i need to do to make the device manager work again?

---

### Post by Blue_T0oth on 2007-09-03
need some help here... trying ta use bitpim but i need to be able to change permissions on usb devices... ne1 know how i can get hdm working again?

---

### Post by iolapiu on 2007-09-19
up!!!

```
simo@ubuntu:~$ hal-device-manager
<gtk.Menu object (GtkMenu) at 0xc680f0>
Traceback (most recent call last):
  File "/usr/share/hal/device-manager/DeviceManager.py", line 132, in on_device_tree_selection_changed
    self.update_device_notebook(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 20, in <module>
    DeviceManager()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 97, in __init__
    self.update_device_list()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 247, in update_device_list
    self.update_device_notebook(self.virtual_root.children[0])
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'
simo@ubuntu:~$ 

```

---

### Post by dudi on 2008-01-29
Hi,
I have exactly same problem here (Ubuntu 7.10)
Any help will be great...
Thanks.

---

