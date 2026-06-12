---
title: "firefox freezes once in a while when using the search box"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by stefangachter on 2007-08-22
Firefox freezes once in a while when I am typing something into the search box in the upper right corner. Then the only thing I can do is switch to terminal mode and kill the process. I have no idea what might cause this problem. Any hint will be welcomed. Thanks, Stefan
PS. Using Ubuntu 7.04, Firefox 2.0.0.6 and Google as default search engine.

---

### Post by 1/0 on 2007-08-22
It could be many things. There's one side effect with all the extensions; it gets more complex and difficult to trace down errors. When it comes to issues in firefox I usually just rename the .mozilla folder to, lets say .mozilla-old and start over. Most of the time the issues are gone after that. You can get your bookmarks from the old folder but you should reinstall the extensions. 

Hope it helps

---

### Post by aitorcalero on 2007-08-22
Also you can give a try to [swiftfox]("http://www.getswiftfox.com")

---

### Post by stefangachter on 2007-08-23
Thanks for the hints. I was just wondering, because I did not install any add-on except for Google desktop. But maybe this cause the freezing...

---

### Post by antharr on 2007-08-23
> **aitorcalero said:**
> Also you can give a try to [swiftfox]("http://www.getswiftfox.com")

This is what I would suggest also. Firefox would freeze often on my laptop. I installed Swiftfox and I have no problems since.

---

### Post by aysiu on 2007-08-23
Try launching ```
firefox
``` from the terminal. See what error messages appear when Firefox freezes up.

---

### Post by stefangachter on 2007-08-23
Is there a better way to track any errors when firefox is freezing? Because once firefox freezes, I cannot access any other windows. So, difficult to check for some error messages. Anyway, if it will become too cumbersome with firefox, I will give swfitfox a try. Thanks so far for your help, and if I will get some useful additional information, I will post it here.

---

### Post by philinux on 2007-08-23
I've been getting this infrequently, I've run it from terminal but no errors are produced. When it freezes its sends the cpu to 100% for about 15 - 20 seconds. I monitored it with system monitor to see what happened. After 15 seconds say cpu would start to reduce fro 100% and firefox would the unfreeze.
By the way everything else is not froze I can run other apps etc, weird.

Since I installed ubuntuzilla the freezing is less frequent but still happens.

---

