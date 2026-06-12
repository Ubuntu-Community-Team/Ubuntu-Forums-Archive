---
title: "power management app"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by romeyde on 2008-01-30
SYSTEM > PREFERENCES > POWER MANAGEMENT

Been having trouble off and on with resume after a suspend on my amd 64 system.   Decided to try again but for some reason the power management app won't even run now.   When I try to start it, it says 'Starting Power Mangement' in the task bar, the cursor changes to a busy one for a few secs, then it just goes away.   Checked running processes but don't see it.  Tried finding a log that might tell me why it was bombing but not having a luck.

Ideas?

---

### Post by jleaker01z on 2008-01-30
Open a terminal and enter the following:

gnome-power-manager --verbose --no-daemon

Then you will be able to see (and copy/paste) any error messages.

---

