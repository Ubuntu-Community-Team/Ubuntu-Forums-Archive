---
title: "Why does turning off my ATI driver 'help' Beryl/Compiz-Fusion to work?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by kobinasucks on 2007-09-16
I have Feisty running on a Dell Inspiron 6000 with an ATI M22 Radeon Mobility M300 card and in installing first Beryl and then Compiz-Fusion, I've noticed that neither work unless I go into my Restricted Drivers Manager and de-enable (is that a word?) the card.

Now, I know I should not look a gift horse in the mouth but while Beryl worked fine this way, Compiz keeps crashing my computer and returning me to my log-in screen and I suspect it is because I am supposed to be using the ATI card and I am being punished by the Open Compositing gods for being stupid enough not to do so.

I followed an amalgalmation of this 

http://ubuntuforums.org/showthread.php?t=540475"]http://ubuntuforums.org/showthread.php?t=540475

and this page

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

... in order to get Compiz working but it just wouldn't work until I turned off the card.

Is there any way of turning on the card and getting it to still work? Or anyway of simply ending the constant crashing?

---

### Post by overdrank on 2007-09-17
> **kobinasucks said:**
> I have Feisty running on a Dell Inspiron 6000 with an ATI M22 Radeon Mobility M300 card and in installing first Beryl and then Compiz-Fusion, I've noticed that neither work unless I go into my Restricted Drivers Manager and de-enable (is that a word?) the card.

Now, I know I should not look a gift horse in the mouth but while Beryl worked fine this way, Compiz keeps crashing my computer and returning me to my log-in screen and I suspect it is because I am supposed to be using the ATI card and I am being punished by the Open Compositing gods for being stupid enough not to do so.

I followed an amalgalmation of this 

http://ubuntuforums.org/showthread.php?t=540475"]http://ubuntuforums.org/showthread.php?t=540475

and this page

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

... in order to get Compiz working but it just wouldn't work until I turned off the card.

Is there any way of turning on the card and getting it to still work? Or anyway of simply ending the constant crashing?

On the first how to your linked, it is for a XGL session that you choose at the login window. And also instructs you to remove the ```
Fglrx is part of the ATi proprietary driver.
```.

---

### Post by kobinasucks on 2007-09-17
Yeah.. I tried using the XGL session and still had no joy. However, I don't know how to remove fglrx without removing the whole card or ruining my whole system. I thought it's supposed to be an integral part of the graphics package?

Is it adviseable to remove it? Haven't I done that anyway by disenabling the graphics card? 

Oh dear.

---

### Post by kobinasucks on 2007-09-17
I just tried logging in using GNOME + XGL still without the ATI driver. Compiz-Fusion is working but extremely jerky. I am tempted to fire up Envy to reinstall the driver but it's pointless unless there is a way of maintaining the ATI driver but removing fglrx.

Help! I feel like I'm close... (famous last words...)

---

