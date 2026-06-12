---
title: "In over my head"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by jackdirt on 2005-12-21
Ok so I got so sick of windows after years and years of use I went and wiped my hard drive clean and installed Ubuntu. Now knowing nothing I have hit my first major road blocks. 

I read over the search and found some similar problems but I really had no idea how to fix the problems. I can only access internet wirelessly on my pc and now I need to know how to get my wireless card to work or else me have no net. Very sad me on friends computer now.  Once I get internet I need know how install video card it nvidia stupid thing and d-link. I know this is very vague but I am helpless right now. Much like clam without shell. Please with kind hearts shine light on me and bring joy. Many blessings and thanks.

Me need dual monitors soon one monitor no enough it make boring. Thanks for internet friends!

---

### Post by az on 2005-12-21
What kind of wireless card?

---

### Post by jackdirt on 2005-12-21
the install disk say AirPlus Xtreme G adapters d-link ver4.00 it internal card. 

Thank you Hope help

---

### Post by jimrz on 2005-12-21
for your vid card, first get / install from synaptic  nvidia-glx

if that leaves you missing some functionality that you require, look [[COLOR="Sienna"]**here**[/COLOR]]("http://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")
 for how-to manually prepare and install your binary drivers.

My nvidia card seems to be doing all I need with just the synaptic  nvidia-glx, but I have not tried dual monitors, yet.

Afraid I'm not much help with the wifi, but there are lots of posts on this forum relating to it that you can search.

Good luck.

---

### Post by az on 2005-12-22
[QUOTE=jackdirt]the install disk say AirPlus Xtreme G adapters d-link ver4.00 it internal card. 

Thank you Hope help[/QUOTE]

DWL-G520?

[http://support.dlink.com/faq/view.asp?prod_id=357](http://support.dlink.com/faq/view.asp?prod_id=357)

[http://www.dlink.com/products/category.asp?cid=1&sec=0#cid_13](http://www.dlink.com/products/category.asp?cid=1&sec=0#cid_13)


If this is so, then you should already have a working wireless card - the madwifi drivers are included in the linux-restricted-modules package that is installed by default.  You should see a wireless device in the networking tool (System - Administration - Networking)

---

### Post by jackdirt on 2005-12-22
yes that is it but whenever I go to networks or try to use synaptic I just get the litlte spin wheel and then nothing happens. I'm guessing I should be getting some menu to pop up no? 

thanks

---

### Post by az on 2005-12-22
Open up a terminal and type

sudo apt-get -f install

It is possible that your installation did not finish properly.  That command will finish it.

If it does nothing, post the output (the error it gives) of

sudo synaptic

---

### Post by Mustard on 2005-12-22
[QUOTE=jackdirt]yes that is it but whenever I go to networks or try to use synaptic I just get the litlte spin wheel and then nothing happens. I'm guessing I should be getting some menu to pop up no? 

thanks[/QUOTE]

Did you use expert install?

That is certainly reminiscent of problems people often have when they use the expert install and sudo privileges are not set up for the first account.

---

