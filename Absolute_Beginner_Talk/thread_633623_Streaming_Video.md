---
title: "Streaming Video"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-06
I've followed the advice listed here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) yet I still can't play embedded videos such as the ones found at places like [http://www.break.com/](http://www.break.com/)

Does anyone have any advice?  What other information would you need?

---

### Post by eolson on 2007-12-06
I just followed the link  and  it works form me.

Running Gutsy.  Have done nothing strange.  Just the codec stuff and don't even remember doing that, but must have.

---

### Post by Mramius on 2007-12-07
Yeah, I've done everything there and I still get nothing.  Firefox claims that it's using the totem plugin for video etc but all I get is a grey box.

---

### Post by jryprt on 2007-12-07
Use this guide [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624) . Its what I used when you get to the part where it says ( Add the following lines to add the Medibuntu repository to the file: )  use the lines below instead.  Then do the Import the gpg key as stated.   Or try this [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)





## Medibuntu - Ubuntu 7.10 &#8220;gutsy gibbon&#8221;
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free

---

