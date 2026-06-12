---
title: "replace utf-8 with iso-8859-1, Is there a correct procedure?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by eslin on 2008-03-11
Hi, Ive been doing this manually om my older installs by replacing and changing stuff allover da place.
But now in my new install I would like to do this the correct way.

My goal is to use en_US.ISO-8859-1 in the X enviroment
But I cant manage to fix this now.

both GDM_LANG and LANG are still 
en_US.UTF-8

Best regards 
eslin

---

### Post by eslin on 2008-03-13
vi /var/lib/locales/supported.d/local
en_US.ISO-8859-1 ISO-8859-1                  
                                    
vi /etc/default/locale
LANG="en_US.ISO-8859-1"
                      
vi /etc/environment  
LANG="en_US.ISO-8859-1"
                 
locale-gen --purge

---

