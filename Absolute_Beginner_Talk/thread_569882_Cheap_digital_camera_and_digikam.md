---
title: "Cheap digital camera and digikam"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by alphasurfari on 2007-10-07
I recently bought a 10$ 'micro' digital camera. I figured for 10$ what could I lose? I was amazed to see that someone had written a driver for it and it worked flawlessly with digiKam in Kubuntu. It was using one of the 'chez-ez' drivers. 

Unfortunately a bad battery trashed that camera quickly. I went back to the same discount store and bought what I thought was the same camera again (this time for only 5$!). Although it was the same chassis, it was re-branded by some different unheard of company and it appears to have a different chip inside, sadly one that is not read by gphoto. 

Has anyone had any luck or tricks to work with these cheapo cameras? I don't have much info, but here is a pic of the camera mentioned (this link probably wont last long):

[http://xscargo.flyerservices.com/cached_images/products/thumbnail/XSC_PR0009_142_XSP1_img74.jpg](http://xscargo.flyerservices.com/cached_images/products/thumbnail/XSC_PR0009_142_XSP1_img74.jpg)

I also had an older cheapo camera lying around that I thought I would try. It doesn't work either. Here is an amazon page for a camera from the same manufacturer that looks very similar (not identical).

[http://www.amazon.com/SiPix-Stylecam-Snap-Digital-Camera/dp/B00007L18X](http://www.amazon.com/SiPix-Stylecam-Snap-Digital-Camera/dp/B00007L18X)

Both these cameras charge off the USB and register that they have been connected to a computer. Here is the lsusb output when I have connected this second camera:
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0851:1542 Macronix International Co., Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


When I run gphoto-2 --auto-detect the camera's PC indicator flashes.. So there is some kind of connection going on! Anyone have any ideas for how I can access this bargain cameras?

---

