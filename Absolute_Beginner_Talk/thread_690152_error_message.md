---
title: "error message"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by bjstabio on 2008-02-07
I had 7.10 installed with all updates and computer started to freeze up.  Nothing would bring it out of this condition except hard reboot.  Reinstalled OS and at completion of installation, as system was rebooting, I got the following message:

“Network Manager: nm_dbus_signal_devise_status_change: assertion cb_data->data->dbus_connection failed”

Can anyone tell me what this means?  Could this be the cause of the freeze?  Thank you for any help you can provide.

---

### Post by jeffus_il on 2008-02-07
Network Manager uses the dbus daemon to talk to other programs running on your system, something it expects is not there. If you don't have a laptop that is roaming, you can just click on the network manager icon and manually set your networking parameters.

---

