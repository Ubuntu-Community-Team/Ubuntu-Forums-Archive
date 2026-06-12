---
title: "8gb partition limitation for early macs"
date: 2008-04-14
forum: Apple PPC Users
---

### Post by stream303 on 2008-04-14
Just found a great apple reference concerning the errors one might come up with if they have upgraded the hard drive in very early macs that originally had a small drive:

[http://docs.info.apple.com/article.html?artnum=25249](http://docs.info.apple.com/article.html?artnum=25249)

Seems that the trick is to partition it to less than 8gb, 7.8 is ok, but 7.5 gb to be on the safe side.

I guess if your install is throwing errors like:
```

Default Catch
Unimplemented Trap
Segment Loader Error
```

this could be a good indication for early machines that need a 7.5 gb partition.

Not sure if a firmware upgrade fixes this issue to allow for very large partitions on newer/larger hard drives...

---

### Post by oswaldkelso on 2008-04-14
Hi stream
While were talking about  hard drive size limits there is a 128gb limit on many early  g3 and g4 macs. I suspect its similar to the 8gb limit on early imacs  I cant remember where I saw it but it was mentioned in this forum somewhere. Its just good to draw users or potential new linux users attention to it  in an effort to make their install go well.

---

### Post by stream303 on 2008-04-14
You are right - good thing to check for some machines that can only go to 128gb (at least to contain root / boot...)

I think that some of the confusion for the earlier G3's might be due to them being shown as being able to use up to 128gb drives, but fail to mention that they need to upgrade the firmware to do so, otherwise they are stuck at 8gb (7.5 to play it safe)

Thanks for the 128gb warning too.  I had forgotten about those boxes..

---

