---
title: "Ubuntu 9.10 major firefox rendering issues (MBP 3,1)"
date: 2009-11-05
forum: Apple Hardware Users
---

### Post by sunbird on 2009-11-05
I upgraded to 9.10 and I thought everything went swimmingly... but yesterday I started having major rendering problems with Firefox that make the browser essentially unusable. Clicking on a tab, the tab is not displayed until you scroll up or down. Menus do not appear when clicked on. When opening new tabs or windows, nothing appears until you attempt to scroll. Most frustrating of all, right click menus do not appear at all, so it is impossible to right-click to download.

I've tried disabling visual effects, no dice.

I don't have these problems with other applications, only Firefox.

I poked around and didn't find any bug reports on this issue for 9.10. I'm wondering if there is any other troubleshooting I should do on my end before filing a bug report.

---

### Post by Dougie187 on 2009-11-05
What kind of video card do you have?

I will assume from your sig that you have an nvidia, but I guess it could be ATI too. Do you have drivers installed for it (assuming nvidia)?

---

### Post by sunbird on 2009-11-05
Sorry, I should have said. I have nvidia geforce8600mgt with the nvidia-glx-185 driver installed. I have had no problems with this setup and have been running single-boot ubuntu since 8.04.

---

### Post by sunbird on 2009-11-05
This is a problem with the upgrade from 9.04-->9.10. The installer kept version 3.0 *and* installed version 3.5 as well. To fix:

```

sudo apt-get remove firefox* && sudo apt-get install firefox-3.5

```

Or you can go into the synaptic package manager and just remove the specific firefox-3.0 packages.

I'll report this as a bug.

---

