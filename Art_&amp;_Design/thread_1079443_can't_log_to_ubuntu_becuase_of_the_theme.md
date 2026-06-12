---
title: "can't log to ubuntu becuase of the theme"
date: 2009-02-24
forum: Art &amp; Design
---

### Post by KLIA on 2009-02-24
hello guys. i was following one tutorial to transform ubuntu into mac leopard, and after i am nearly fnished, the installation requires you to reboot in order to get everything correctly working but the surprised was that i am stuck on the welcome log in with white screen and no vivid desktop, i tried rebooting many times but no joy..

any idea how to remove the theme from the terminal or some other solution to get my desktop back, i am using gnome 

Thanks in advance

---

### Post by Orlsend on 2009-02-24
Have you tried using the recovery mode? Just hit "esc" when you turn you computer on (When you see a small counter, usually its a 7 second one) and select to boot into recovery mode.

To tell you the truth I never herd of a theming tutorial that requires you to installs complicated stuff and then to reboot.

When your problem is done and you still want the mac then use [Epidermis]("http://epidermis.tuxfamily.org/"). its downloads and installs the mac theme and many others with one click.

---

### Post by smartboyathome on 2009-02-24
I think he used Mac4Lin, btw. :)

---

### Post by kspringer on 2009-02-24
Try this:  [http://http://ubuntuforums.org/showthread.php?t=923028](http://http://ubuntuforums.org/showthread.php?t=923028)
 
Worked great for me.
 
k.

---

### Post by Orlsend on 2009-02-25
> **smartboyathome said:**
> I think he used Mac4Lin, btw. :)

Well Epidermis installs the Mac4lin. but theres no rebooting and the change can be done after being installed.

---

### Post by KLIA on 2009-02-25
> **Orlsend said:**
> Have you tried using the recovery mode? Just hit "esc" when you turn you computer on (When you see a small counter, usually its a 7 second one) and select to boot into recovery mode.

To tell you the truth I never herd of a theming tutorial that requires you to installs complicated stuff and then to reboot.

When your problem is done and you still want the mac then use [Epidermis]("http://epidermis.tuxfamily.org/"). its downloads and installs the mac theme and many others with one click.

hey man, thanks for the advice about Epidermis....i am gonna give it a shot

i got my desktop back using this command 
apt-get -f install 
which i think it installed gtk2-engies but once i open the theme manager it states that the theme won't work correctly becuase i don't have gtk+ theme

any ideas

---

### Post by KLIA on 2009-02-25
> **Orlsend said:**
> Have you tried using the recovery mode? Just hit "esc" when you turn you computer on (When you see a small counter, usually its a 7 second one) and select to boot into recovery mode.

To tell you the truth I never herd of a theming tutorial that requires you to installs complicated stuff and then to reboot.

When your problem is done and you still want the mac then use [Epidermis]("http://epidermis.tuxfamily.org/"). its downloads and installs the mac theme and many others with one click.

hey man, thanks for the advice about Epidermis....i am gonna give it a shot

i got my desktop back using this command 
apt-get -f install 
which i think it installed gtk2-engies but once i open the theme manager it states that the theme won't work correctly becuase i don't have gtk+ theme

any ideas

---

### Post by Orlsend on 2009-02-26
Have done all the updates and what version of ubuntu are you using?

---

### Post by KLIA on 2009-02-28
i am using the latest version 8.10 and Yes my system is up to date

---

### Post by sirebral on 2009-02-28
Can you try restarting XORG?    **Ctrl - Alt - Backspace.**

I have had problems with GDM Themes giving me blank screens, so when i test them out I make sure I have the GDM Screen randomly selected from a list of two.

---

