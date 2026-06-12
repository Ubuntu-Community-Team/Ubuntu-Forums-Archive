---
title: "IE 7 problems"
date: 2007-12-30
forum: Art &amp; Design
---

### Post by lzfy on 2007-12-30
Hi there. I don't know if this is the right place to ask but I coulnd't find any other place to ask. The problem is that my site doesn't work with IE7. Other browsers works just fine. The problems occurs when i link the page with some javascript files. If I remove that line everything seems to work fine.

It's this code causing the problem.
[B]<script type="text/javascript" src="js/mootools-release-1.11.js" />
<script type="text/javascript" src="js/slide.js" />
<script type="text/javascript" src="js/slimbox.js" />[/B]

Can somenone help me with this? I tried google but I coulnd't find anything usefull.
Thanks.

[Link to the site]("http://lzfy.nl/portfolio_digitalart.html")

---

### Post by LaRoza on 2007-12-30
What do you mean by "don't work"?

---

### Post by lzfy on 2007-12-30
I just get a blank page with the known javascript security warning. Nothing else.

---

### Post by junior aspirin on 2007-12-30
just a blank page in firefox 3 too. using the latest nightly.

---

### Post by LaRoza on 2007-12-30
Works in Opera...

---

### Post by sowelie on 2007-12-30
You can't use self closing tags with the scrip tag.  You have to actually have a </script>

---

### Post by jken146 on 2007-12-30
Works in Firefox 2.0.0.11

---

### Post by smartboyathome on 2007-12-30
> **LaRoza said:**
> Works in Opera...

I can confirm it works with Opera 9.24.

---

### Post by Meep3D on 2007-12-30
> **sowelie said:**
> You can't use self closing tags with the scrip tag.  You have to actually have a </script>
What he said.

---

### Post by lzfy on 2007-12-30
> **sowelie said:**
> You can't use self closing tags with the scrip tag.  You have to actually have a </script>

That seems to help :) Thank you.

 But the animations in IE7 are not smooth as it is in Opera/Firefox :(  

But that is caused by something else I guess.

---

### Post by nikRbokR on 2007-12-30
Haha... ya thats just the way IE is.  MS has it so that developers hafta develop sites based on how IE "interprets" the rules.  It screws up everything even w/ perfect coding.  That's y u'll find that problem. IE tends to interpret rules differently, so somehting that works perfectly well in Firefox or Opera will look like crap on IE.  I don't use IE at all anymore (even w/ the tabs).  Firefox is the only browser I use :) (haven't tried Opera yet on Vista yet, just firefox).

---

### Post by sowelie on 2008-01-06
> **lzfy said:**
> That seems to help :) Thank you.

 But the animations in IE7 are not smooth as it is in Opera/Firefox :(  

But that is caused by something else I guess.

Yes, animations in IE are going to be slower because IE's javascript engine is terrible compared to Opera/Firefox.  If you use JQuery, they have found away around this issue.

---

### Post by Presto123 on 2008-01-06
Ran on SeaMonkey:

Not bad, a little slow. But, that's a lot of stuff to load. Really nice stuff on there!

---

