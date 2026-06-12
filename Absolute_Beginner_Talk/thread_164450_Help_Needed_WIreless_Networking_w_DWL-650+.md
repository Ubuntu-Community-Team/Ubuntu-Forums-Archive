---
title: "Help Needed: WIreless Networking w/ DWL-650+"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by losrivas on 2006-04-22
Hi. First, let me say I'm brand-new to Ubuntu and to Linux in general. Also, thanks in advance for the help.

I can't get my wireless card to work. I've done a few searches, and poked around a bit with network-admin, but I'm still at a loss. 

What do I need to do to get wireless internet working on my laptop? The wireless card I'm using is a DWL-650+.

Any and all help is greatly appreciated. Thanks again.

-losrivas

---

### Post by garner_nc on 2006-04-22
You need to use Ndiswrapper, available from repositories. I have the same card but mine is specifically revision M. Look on lower right corner of label on card.

Apparently this should work with RTL8180 drivers and Ndiswrapper. I've not had a a chance to actually try mine yet but there is lots of documentation on the net to be found. 

I'm curious to see how this works for you. Sorry I can't give you more help.

All the Best,
Doug White
Garner, NC USA

---

### Post by losrivas on 2006-04-22
Thanks for the help so far. 

I looked into it a little more, and apparently there is a group working on open-source drivers for this card: [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) 

I checked the page, and wound up at the HowTo page for Ubuntu: [http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu) 
Unfortunately, there is almost zero information on that page so I'm stuck, again. Is there anyone who could guide me through installing the ACX100 driver on Ubuntu 5.10? 

If we're successful, maybe we can contribute to the ACX100 HowTo Wiki page for Ubuntu.

Thanks again everybody.

- losrivas

---

### Post by losrivas on 2006-04-23
Does anyone have any experience with the ACX100 drivers in Ubuntu? Thanks for your help everybody.

---

### Post by spacey on 2006-04-23
Hi. I have the same card as you. I have tried the acx100 drivers but with no luck. The only way i have been able to use my card, is by using ndiswrapper with the original windows drivers.

---

### Post by nalmeth on 2006-04-23
download ndiswrapper and ndisgtk (the gui for ndiswrapper), download your driver from here:  [http://support.dlink.com/products/view.asp?productid=DWL%2D650%2B](http://support.dlink.com/products/view.asp?productid=DWL%2D650%2B)
should be an .inf file I think, but just follow what ndisgtk tells you

---

### Post by losrivas on 2006-04-26
Thanks for the help so far. How do I open the ndisgtk gui once it's been installed? I can't find it in System => Administration or any of the drop-down Applications menus.

---

