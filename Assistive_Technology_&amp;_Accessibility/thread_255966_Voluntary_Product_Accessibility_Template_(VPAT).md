---
title: "Voluntary Product Accessibility Template (VPAT)"
date: 2006-09-12
forum: Assistive Technology &amp; Accessibility
---

### Post by cruiz on 2006-09-12
Dear Ubuntu users, 

I am wondering if there is an official Voluntary Product Accessibility Template (VPAT) for Ubuntu as you have in other operative systems. As far as I know VPAT is used by US gov for buying software. Does anyone have an idea about this?

Thanks in advance. 

Carlos.

---

### Post by jasongrieves on 2006-09-13
great question!  Henrik, what do you think of proposing this?  Our infrastructure is getting pretty solid.  This would be a great step forward for us, especially for possible government purchases.  Government Regulations such as 508 demand IT be purchased that is most accessible (assuming the IT is what is needed)

Microsoft and Sun (I believe) have VPATs available.

---

### Post by cruiz on 2006-09-15
hello Jason and Henrik, 

is there any guide to develop software for linux (or ubuntu linux) and people with special needs? For example, can developers use speech synthesis natively, with no effort for application developers?.The same for alternative text explanations for images and so on. Does linux (or ubuntu linux) contribute in some way (I mean API)? All those things are expressed in ISO 16071:2002.

I hope you understand what I mean. Thank you very much.

Best regards,
Carlos

---

### Post by Henrik on 2006-09-26
Hi Carlos,

The Gnome accessibility project developer pages are a good place to start: [http://developer.gnome.org/projects/gap/guide/gad/](http://developer.gnome.org/projects/gap/guide/gad/)

If you follow good Gnome development practices and use standard GTK and Gnome widgets the application should work well with screenreaders and such out of the box. On the KDE this will not be available until KDE4, but you can make an application feed it's text information to the KDE speech system KTTS directly, as Konqueror does.

---

