---
title: "graphics cards explained"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2008-02-17
Hello I don't understand the thing with all those drivers - xgl ,flxgl (I have probably misspelled them). Could you please clarify this issue for me. How many graphics drivers are there and what is the difference between them. 10x

---

### Post by JoshuaRL on 2008-02-17
There's a lot, but usually you can pare it down to two for each type of card:

1). Open source.  This is usually community created and maintained.  It may have more features then the other kind, depending on how open the manufacturer is about releasing info.

2).  Closed source, or proprietary.  This is the driver that is made by the manufacturer.  Some are pretty good (Intel integrated and nVidia) and some are kind of crappy (ATI, depending on how old of a card it is and anything with a VIA chipset)  These come from the manufacturer, so they tend to have a little less stability issues if they support your card.

What type of card do you have?  I'm guessing ATI, right?

---

### Post by herbster on 2008-02-17
fglrx = driver for ATI cards.

XGL = in simple terms, a way of rendering for those with the ATI driver, since it isn't able to do it by itself.

nVidia cards don't use XGL because the use direct rendering (they don't require anything on top of what the driver provides, unlike ATI), they work the best in linux (I've had both and many of each). nVidia cards use nVidia's driver, which is as easy as apt-get install nvidia for most cards. For newer ones (8800 series primarily), one can get the drivers off nvidia.com.

I'm sure an expert here can correct me if I'm wrong or add more.

---

