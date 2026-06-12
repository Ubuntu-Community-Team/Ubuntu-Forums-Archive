---
title: "Can not change resolution"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by mukitti on 2006-10-28
My computer has feature like this
-Build in VIA K8M800 Chipset
-Monitor LG Flatron ez T711ss

I use Ubuntu 6.10,resolution is 1280x1024, I try to change resolution to 1024x 768,but The Ubuntu switch to login page and the resulution is still 1280x1024. Can somebody please help me.:mrgreen:

---

### Post by taurus on 2006-10-28
Have you tried to reconfigure your X again with (from terminal:  Applications -> Accessories -> Terminal)

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dbott67 on 2006-10-28
If you're still having troubles, please post the output of **cat /etc/X11/xorg.conf**

-Dave

---

### Post by mukitti on 2006-10-29
Thank you for your answer,now the problem was fixed.:mrgreen:

---

### Post by willy1234x1 on 2006-10-29
I want to know why you didn't use that resolution it's alot better than 1024x768 I'm stuck with that since my screen can't handle any larger sizes but I'd love a resolution that large more workspace

---

