---
title: "ati mobility u1 aka 320m"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by haroonie on 2007-08-04
Hello!  Greets from the Ubuntu Newbie.

I've searched the forum and couldn't come up with a definite answer..

I have an hp pavilion ze4400 and was wondering if compiz-fusion will run with my ati 320m video card.  I've read mobility driver support was not that great and fgl / open gl for this particular card isn't that great.

Can anyone shed some light on their experiences w/ a 320m and compiz / beryl / c- fusion?

Thanks.

---

### Post by overdrank on 2007-08-04
> **haroonie said:**
> Hello!  Greets from the Ubuntu Newbie.

I've searched the forum and couldn't come up with a definite answer..

I have an hp pavilion ze4400 and was wondering if compiz-fusion will run with my ati 320m video card.  I've read mobility driver support was not that great and fgl / open gl for this particular card isn't that great.

Can anyone shed some light on their experiences w/ a 320m and compiz / beryl / c- fusion?

Thanks.

Hi I did a quick search for that graphics card and the links are kind of old
[http://search.yahoo.com/search?p=ati+320m+on+ubuntu&fr=yfp-t-501&toggle=1&cop=mss&ei=UTF-8](http://search.yahoo.com/search?p=ati+320m+on+ubuntu&fr=yfp-t-501&toggle=1&cop=mss&ei=UTF-8)
Are you sure that is your graphics card, you can make sure with the lspci command in the terminal, located under applications, accessories, terminal. :)

---

### Post by haroonie on 2007-08-05
> **overdrank said:**
> Hi I did a quick search for that graphics card and the links are kind of old

Yes, its is quite old, about a 5 year old laptop.  The problem with the IGP 320M mobility video card that's in older laptops is that it is based on the old Radeon chipset, making it not work properly with XGL and AIGLX.

After trying compiz fusion with both XGL and AIGLX on my chipset, i found the compiz fusion crashed all the time.  I read around and finally just used the "radeon" drivers that came with feisty w/ compiz fusion and found that it worked fine!  ATI's horrible w/ linux driver support, lets see if they release the source soon.

To all, ATI IGP 320M mobility u1 runs compiz fusion fine on feisty.  Now i have gorgeous eye candy w/ my laptop running feisty and i love it. :)

---

### Post by overdrank on 2007-08-05
> **haroonie said:**
> Yes, its is quite old, about a 5 year old laptop.  The problem with the IGP 320M mobility video card that's in older laptops is that it is based on the old Radeon chipset, making it not work properly with XGL and AIGLX.

After trying compiz fusion with both XGL and AIGLX on my chipset, i found the compiz fusion crashed all the time.  I read around and finally just used the "radeon" drivers that came with feisty w/ compiz fusion and found that it worked fine!  ATI's horrible w/ linux driver support, lets see if they release the source soon.

To all, ATI IGP 320M mobility u1 runs compiz fusion fine on feisty.  Now i have gorgeous eye candy w/ my laptop running feisty and i love it. :)

Great and glad to hear, Good luck and enjoy! :guitar:

---

