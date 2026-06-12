---
title: "wish to assign 2 identical USB devices onto different busses"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by jpf32 on 2008-02-01
running kernel 2.6.24-1-486

i have 2 identical webcams .. I would like each one to be assigned to a different USB bus(cam 1 --> bus 1 and cam 2 --> bus 2) for bandwidth reasons .. however, each time I plug them both in they both always end up on the same bus (2) .. any help would be appreciated .. perhaps a udev rule?

TIA, jpf

---

### Post by max renn on 2008-02-13
Yeah, I had a hard time understanding the USB stuff.  The way it looks, if you have via rev. 5 and usb 2.0 enhanced(not sure abt intel, sis boards), then each actual port is on a different hub.  So I couldn't understand why I have six usb port but only five usb hub in device manager, so I try to hook my drives up to separate pairs of ports, just in case, but I have not noticed any difference in speed.  But I do notice a difference if I hook an external hub to one port and put two drives on it.

That is as much as I bothered to learn.  Hope it helps :)  I realize it does not address a possible software issue in linux.  Are you sure your ports are different hubs, and are you sure the bandwidth is compromised, even though they show up on one hub?

---

### Post by jpf32 on 2008-02-13
I actually just learned more about this last night ... I am running AMD Geode LX/GX hardware .. below is a copy/paste of an email which I wrote to my hardware supplier last night .. unfortunately, the units which I bought in 2005 (which are no longer available) work they way I need them to .. the newer models do not work as needed. Perhaps there was a USB2.0 spec which was changed .. I have dug up a few references to similar problems on different platforms so it is not limited to the AMD Geode hardware.
======
I have been doing more research .. I came across the AMD docs for the "CS5535 Companion Device" .. there is certainly a difference between 2 different versions ..

This is the GX version dated Feb 2005:
    [http://www.amd.com/files/connectivitysolutions/geode/geode_gx/31506_cs5535_databook.pdf](http://www.amd.com/files/connectivitysolutions/geode/geode_gx/31506_cs5535_databook.pdf)
    Read specifically pages: 13, 15, 18 .. it speak of 2 separate host controllers USB1 (1-1 & 1-2) & USB2 (2-1 & 2-2) ... "provides 4 ports controlled by 2 independent controllers" AND "There are 2 ports associated with each controller"

This is the LX version dated March 2006:
    [http://www.amd.com/files/connectivitysolutions/geode/geode_lx/33238f_cs5536_ds.pdf](http://www.amd.com/files/connectivitysolutions/geode/geode_lx/33238f_cs5536_ds.pdf)
    Read specifically pages: 13, 15, 18 .. it speaks of 4 ports which are "automatically assigned to OHCI or EHCI depending on device type" .. IT DOES NOT SPEAK OF 2 CONTROLLERS (1-1 & 1-2, 2-1 & 2-2)

Apparently this is a change at the AMD HARDWARE level. It is very unfortunate that this is now the case. I wonder if there is a work-around or hack that can provide a solution. What do you think???

---

### Post by max renn on 2008-02-13
> **jpf32 said:**
> I actually just learned more about this last night ... I am running AMD Geode LX/GX hardware .. below is a copy/paste of an email which I wrote to my hardware supplier last night .. unfortunately, the units which I bought in 2005 (which are no longer available) work they way I need them to .. the newer models do not work as needed. Perhaps there was a USB2.0 spec which was changed .. I have dug up a few references to similar problems on different platforms so it is not limited to the AMD Geode hardware.
======
I have been doing more research .. I came across the AMD docs for the "CS5535 Companion Device" .. there is certainly a difference between 2 different versions ..

This is the GX version dated Feb 2005:
    [http://www.amd.com/files/connectivitysolutions/geode/geode_gx/31506_cs5535_databook.pdf](http://www.amd.com/files/connectivitysolutions/geode/geode_gx/31506_cs5535_databook.pdf)
    Read specifically pages: 13, 15, 18 .. it speak of 2 separate host controllers USB1 (1-1 & 1-2) & USB2 (2-1 & 2-2) ... "provides 4 ports controlled by 2 independent controllers" AND "There are 2 ports associated with each controller"

This is the LX version dated March 2006:
    [http://www.amd.com/files/connectivitysolutions/geode/geode_lx/33238f_cs5536_ds.pdf](http://www.amd.com/files/connectivitysolutions/geode/geode_lx/33238f_cs5536_ds.pdf)
    Read specifically pages: 13, 15, 18 .. it speaks of 4 ports which are "automatically assigned to OHCI or EHCI depending on device type" .. IT DOES NOT SPEAK OF 2 CONTROLLERS (1-1 & 1-2, 2-1 & 2-2)

Apparently this is a change at the AMD HARDWARE level. It is very unfortunate that this is now the case. I wonder if there is a work-around or hack that can provide a solution. What do you think???

So, I am not sure which actual hardware you have.  (And I assume your cams are USB2.0?) Do you have the GX or LX?  It looks like the GX is only going to to have USB2.0 on one controller/two ports, which makes the configuration you wish not possible.  The way I understand the LX, you can have one USB 2.0 device on ports 1-3 and another on configurable port 4 (of course that would be determined by your BIOS or MB on whether or not you can actually configure that fourth port).  So that may provide the config you are looking for.

Is this a laptop? (STRIKE THAT) Otherwise, you might be well served to purchase a cheap $10 USB2.0 add-on card?

---

### Post by jpf32 on 2008-02-13
my working units are DT166 (GX) units from [www.dtresearch.com](www.dtresearch.com) .. my non-working units are DT168 (LX) units. I am running Debian Lenny 2.6.23 kernel and GSPCA webcam drivers. 

I trying to use 1.1 webcams....although I just asked my cam supplier to send me some 2.0 cams ... 

the problem is thus:
 **on the DT166 unit** .. because it has 2 busses .. seems to load balance the cams .. upon inserting the 2 cams .. one goes to port 1-1 and one goes to 2-1 .. this keeps GSPCA from complaining about bandwidth allocation (too many devices on 1 bus)
 **on the DT168 unit** .. upon inserting the 2 cams .. they both end up on a single bus (because it now assigns busses based on device TYPE, rather than load balancing based on QUANTITY of devices) .. this causes GSPCA (well maybe usbcore or ohci) to throw an error (2.6.23), or kernel panic (2.6.18) due to lack of available bandwidth.

as an FYI...
the older version of "thin client" from [http://www.rackmountmart.com/html/tc1001.htm](http://www.rackmountmart.com/html/tc1001.htm) behaves as the DT166 but has different issues regarding the CF Card Adapter and IDE lockup (as well as price)

the newer version of "thinbox" from [http://shopping.hacom.net/catalog/product_info.php?manufacturers_id=11&products_id=91](http://shopping.hacom.net/catalog/product_info.php?manufacturers_id=11&products_id=91) behaves as the DT168 unit .. however, I cannot say enough good things about working with Hacom ..**[SIZE="3"] they are fantastic![/SIZE]**

so my overall goal is to insert 2 cams and have them end up on different busses so that GSPCA doesn't crap out .. as I said, I have ordered some 2.0 cams but I'm not sure this will help...maybe I must mix a 2.0 (ehci) cam and a 1.1 (ohci) cam .. this might be the answer

Thanks for thinking about this problem, I can take all the brain power I can get on this...

---

### Post by max renn on 2008-02-13
OK, I understand now.  Those are very cool little units.  I was actually considering the NSLU2 as my next project, once I get my linux server operating satisfactorily.  Now I shall have to delve into your solution to see if it is better sorted for my wishes.  Nice :)

That sucks they changed the architecture like that, but I wonder if they changed it to make two USB 2.0 devices work on separate controllers?  I hope the USB 2.0 Cams will work for you, or at least one of each.

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1118334819312&packedargs=site%3DUS&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1931258184B16](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1118334819312&packedargs=site%3DUS&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=1931258184B16)

[http://www.nslu2-linux.org/wiki/FAQ/HomePage](http://www.nslu2-linux.org/wiki/FAQ/HomePage)

---

### Post by jpf32 on 2008-02-13
thanks for pointing out the SLUG .. my requirements call for 4 USB ports and an audio out .. additionally, I try to run everything from CF card media .. unfortunately, significant hardware changes since I bought my original DT166 units makes everything more complicated since no one really supports CF card media in this form-factor anymore .. in addition to this newly found USB problem .. 

I did find a CF-->IDE adapter supplier in Canada (importers from Tawain) .. [www.ibt.ca](www.ibt.ca) .. they have a few other goodies too .. but mainly i'm interested in their CF Adapter .. i couldn't be happier with my trusty DT166s, but now i'm negotiating all sorts of obstacles...so much for progress!

thanks again

---

