---
title: "Firefox wont open any pictures, gives error."
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-25
It seems that any time I try and open a site with a picture in it, I get an error message telling me that Firefox doesn't know how to open this type of protocol(irc).

It has never happened before today, and I haven't messed with anything at all. Im using dapper.

---

### Post by UnknownVariable on 2006-10-25
The IRC protocol is a protocol (like [http://)](http://)) that attempts to open mIRC and connect to an IRC server. It has nothing to do with images. Since mIRC is (as far as I know) windows only, you should just be able to ignore it and carry on. :)

---

### Post by voodoonirvana on 2006-10-25
> **UnknownVariable said:**
> The IRC protocol is a protocol (like [http://)](http://)) that attempts to open mIRC and connect to an IRC server. It has nothing to do with images. Since mIRC is (as far as I know) windows only, you should just be able to ignore it and carry on. :)

Yeah I try, but when I click "Ignore", it basically does nothing and I have to go into the system monitor and shut down Firefox entirely.:confused:

---

### Post by UnknownVariable on 2006-10-25
That's odd. Does it happen on any page with images? Such as [www.google.com?](www.google.com?)

---

### Post by voodoonirvana on 2006-10-25
> **UnknownVariable said:**
> That's odd. Does it happen on any page with images? Such as [www.google.com?](www.google.com?)

Hmmm, no it didn't seem to happen in google images, nor when I view any of the images. But it has happened about 4 times today already and it's really bugging me.

---

### Post by furiousV on 2006-10-25
> **voodoonirvana said:**
> It seems that any time I try and open a site with a picture in it, I get an error message telling me that Firefox doesn't know how to open this type of protocol(irc).

It has never happened before today, and I haven't messed with anything at all. Im using dapper.

Go to Options, look in Content, and make sure something like "**Load images from originating website only**" isn't enabled. I had this problem before, and it was fixed with that.

I'm now using Firefox 2.0 and can't see that option, so look around.

Edit: Just noticed what I said might not be the answer to your particular problem, but just double check it anyway.

---

### Post by Kapre on 2006-10-25
> **voodoonirvana said:**
> It seems that any time I try and open a site with a picture in it, I get an error message telling me that Firefox doesn't know how to open this type of protocol(irc).

It has never happened before today, and I haven't messed with anything at all. Im using dapper.

Can you post the sites that gives you this error?

---

### Post by voodoonirvana on 2006-10-25
> **furiousV said:**
> Go to Options, look in Content, and make sure something like "**Load images from originating website only**" isn't enabled. I had this problem before, and it was fixed with that.

I'm now using Firefox 2.0 and can't see that option, so look around.

Edit: Just noticed what I said might not be the answer to your particular problem, but just double check it anyway.

Nope, it's unchecked. But here is the exact words that it gives me when I try and open certain pages:

Firefox doesn't know how to open this address because the protocol (news) isn't associated with any other program.

---

### Post by voodoonirvana on 2006-10-25
bump.....

---

### Post by OptimusPrime on 2006-10-25
Maybe you need to type "about:config" into the address bar, search for "ipv6" and enable it.

---

### Post by voodoonirvana on 2006-10-25
> **OptimusPrime said:**
> Maybe you need to type "about:config" into the address bar, search for "ipv6" and enable it.

Actually, I think I can remember messing with that for some reason about a month ago. Something somebody suggested on here. It was disabled though, I enabled it. What exactly is it?

---

### Post by OptimusPrime on 2006-10-25
> **voodoonirvana said:**
> Actually, I think I can remember messing with that for some reason about a month ago. Something somebody suggested on here. It was disabled though, I enabled it. What exactly is it?

Internet protocall version 6.  It just makes your firefox compatable with this protocall.  I don't really know why, but enabling it really helps a lot.

---

