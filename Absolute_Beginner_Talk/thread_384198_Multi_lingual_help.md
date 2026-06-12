---
title: "Multi lingual help"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Utopia_al on 2007-03-14
We have recently replaced one of our windows based machines with the Ubuntu dist and we are more than pleased with the results. One question relating to multi language support however, We have to constantly swap between using Turkish language and English. At the moment we are using two computers one for each language. Is it possible for users to toglle between the two languages in Ubuntu. We would definately ditch all of our windows OS for ubuntu if this were possible.

---

### Post by xyz on 2007-03-14
Let's keep it simple for a start:
Have you checked System > Administration > Laguage Support and 'check' Turkish?

---

### Post by Utopia_al on 2007-03-14
Yes, have got that far.

---

### Post by Kobalt on 2007-03-14
As fas as I know it's completely possible : you can install as many 'locales' (languages) as you want and switch between them by logging out, selecting you locale and then log back in...

---

### Post by Utopia_al on 2007-03-14
Wow. Impressed with the sppedy responses from this forum. Will try logging out and back in again with new lacale. It would be nice if there was a way of hot keying between languages without logging out. 
Pushing my luck there a bit though I think. Thanks for your very quick replies.

---

### Post by girishv on 2007-03-14
Hi,

I am not exactly sure how to do it sessionwise with out logging out, but hope this helps.
If you want to change the locale for a  newly starting application, say  firefox, you can do (in the same line)

LANG=kn_IN LC_CTYPE=kn_IN LANGUAGE=kn_IN firefox

where kn_IN is my locale :-). Please replace it with the locale you are interested in. You can find all the locale installed on your system with locale -a

Secondly, you can add the applet "keyboard indicator" to the gnome-panel. Clicking the panel changes the keyboard layout.

Girish

---

