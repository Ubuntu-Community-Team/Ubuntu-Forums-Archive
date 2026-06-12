---
title: "Printing to A4 Paper"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2008-03-09
In 'Printer Configuration', under the 'Printer Options' tab, in the drop down menu 'Media size', how do I select A4 as a paper size?  Currently the only option I have is 'Letter'.

---

### Post by glennric on 2008-03-09
What menus are you talking about?  What software are you openning these menus in?  Or is it in System->Administration->Printing?

---

### Post by mikeypc2006 on 2008-03-09
> **glennric said:**
> What menus are you talking about?  What software are you openning these menus in?  Or is it in System->Administration->Printing?

I'm using Xubuntu, so under Setting --> Printing

The printer is a Canon Pixma iP1600 which set-up under Xubuntu automatically and is connected locally to my laptop through USB.

---

### Post by glennric on 2008-03-09
I am not familiar with the XUbuntu menus and settings.  Someone else will have to help you here.  Sorry.

---

### Post by mikeypc2006 on 2008-03-09
> **glennric said:**
> I am not familiar with the XUbuntu menus and settings.  Someone else will have to help you here.  Sorry.

Thanks anyways :)

*bump*

---

### Post by dcstar on 2008-03-10
> **mikeypc2006 said:**
> In 'Printer Configuration', under the 'Printer Options' tab, in the drop down menu 'Media size', how do I select A4 as a paper size?  Currently the only option I have is 'Letter'.

Printer paper configurations are usually set by the Locale you use, have you configured you system to be the correct timezone?

---

### Post by mikeypc2006 on 2008-03-13
> **dcstar said:**
> Printer paper configurations are usually set by the Locale you use, have you configured you system to be the correct timezone?

How do I check and see, bearing in mind, I'm running Xubuntu?  I selected 'London' when I set my computer up, so I'm not sure where I've gone wrong.

---

### Post by dcstar on 2008-03-14
> **mikeypc2006 said:**
> How do I check and see, bearing in mind, I'm running Xubuntu?  I selected 'London' when I set my computer up, so I'm not sure where I've gone wrong.

Right-click the time, select "Adjust Date and Time", or:

```
**sudo tzselect**
```

/etc/papersize should also contain "a4"

---

