---
title: "Greeter Application Crashes"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by frank002 on 2008-01-28
Hello:
 For the last couple of days, I have been getting the "Greeter Application is Crashing" error at bootup. 
I looked up posts dealing with this problem and the solution seems to be to disable the Accessible Login option in LogIn Windows Preference.  My problem is that I have this option disabled already. I must assume that the problem lies somewhere else. If anyone has any ideas, please let me know. Thanks.

---

### Post by spiderbatdad on 2008-01-29
Are you using a custom Greeter? Is more than one theme selected in Login Window Preferences>>Local?  Have you selected "include hostname chooser?"
Custom greeters occasionally develop errors in the GdmGreeterTheme.Desktop launcher...which must have that name...as far as I know. You can find the aspects of your Greeters in /usr/share/gdm/themes/<theme name>

You would want to make sure the GdmGreeterTheme.Desktop xml does not have a line like [Desktop] at the top, but instead looks like the 3rd screenshot below.

---

### Post by frank002 on 2008-01-29
No, I am not using a custom greeter. Today the problem did not happen but I am still on the lookout. Thank you for your quick response.

---

