---
title: "please help!"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by linuxtoindia on 2008-03-18
after installing edubuntu , using it for some days
, when an application crashed< i was also using hybernation at that time >
i restarted pc .
it gave an error'' no image found., cud not resume /sda ,,,....somethg

i reinstalled again the whole os., then tried ubuntu,, same problem,, wiped and installed kubuntu.. same again ,,
now am on edubuntu!

i tried some where

sudo dpkg-reconfigure xserver-xorg
then gdm


it worked
,, but showed ;''running on low graphics.''
and maximum resolution 800x600

agian whenever i boot in edubuntu
it shows the same error''
no resume image ,, then startx error ,, some blue screen
some logs...

and after trying
sudo dpkg-reconfigure xserver-xorg

it works ,, but i have to do it again and again,, creating a new headache!!
i have via chipset
unichrome K8M800 s3,unichrome


please help


thanks in advance..

---

### Post by ajmorris on 2008-03-18
hi there,
the no resume image is fine, that just means there is nothing to restore from hibernate, it will say that every time you dont hibernate.

About the X reconfigure problem... could you please post your xorg.conf files, if possible, before, and after you issue the XServer reconfigure command.

AJ

---

