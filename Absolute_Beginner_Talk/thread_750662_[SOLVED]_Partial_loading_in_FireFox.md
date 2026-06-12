---
title: "[SOLVED] Partial loading in FireFox"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by laidback on 2008-04-09
When I visit some sites (e,g, [www.ebuyer.com](www.ebuyer.com), [www.ebay.com](www.ebay.com)) my FF doesn't fully load the pages, I get to see most of it or perhaps all but the loading slider guide never finishes and the cursor continues to spin. I've installed Epiphany to see what that does and all seems well. So I reckon it's something to do with my FF installation. Any ideas? (This Forum site loads fine)

Running 7.04.

Kindest Regards

Laidback

---

### Post by Fixman on 2008-04-09
> **laidback said:**
> When I visit some sites (e,g, [www.ebuyer.com](www.ebuyer.com), [www.ebay.com](www.ebay.com)) my FF doesn't fully load the pages, I get to see most of it or perhaps all but the loading slider guide never finishes and the cursor continues to spin. I've installed Epiphany to see what that does and all seems well. So I reckon it's something to do with my FF installation. Any ideas? (This Forum site loads fine)

Running 7.04.

Kindest Regards

Laidback

No exact idea, but you can try reinstalling firefox throught synaptic.

---

### Post by sports fan Matt on 2008-04-09
What version of Firefox?  Im running FF3 Beta 5 with no issues

---

### Post by sports fan Matt on 2008-04-09
those pages work fine

---

### Post by The Titan on 2008-04-09
> **sox fan Matt said:**
> What version of Firefox?  Im running FF3 Beta 5 with no issues
same, and it is pretty stable.  You should consider just switching to 3.

---

### Post by FuturePilot on 2008-04-09
The pages load fine here with Firefox 2.0.0.13

---

### Post by laidback on 2008-04-10
Thanks for your replies one and all.
I'm running 2.0.0.13.

I have the tar of v3.0b5 downloaded, does it install and replace existing version preserving local settings etc (bookmarks)?

---

### Post by sayakb on 2008-04-10
> **laidback said:**
> Thanks for your replies one and all.
I'm running 2.0.0.13.
 
I have the tar of v3.0b5 downloaded, does it install and replace existing version preserving local settings etc (bookmarks)?
 
FF v3b5 will install separately and will not replace the 2.0.0.13 version. Plus it wont automatically import bookmarks either.

---

### Post by laidback on 2008-04-10
Thanks for that, I'll give it a go then.

---

### Post by misfitpierce on 2008-04-10
Works fine for me here Ubuntu 7.10 64 bit - Firefox 2.0.0.13

---

### Post by laidback on 2008-04-10
Unpacked tar into local dir (Firefox3) fine, then $ ~/Firefox3/firefox/firefox (which the Firefox site gives as the command to run the script) simple opens the existing Firefox. I'm doing something wrong, any ideas?

Thanks

---

### Post by laidback on 2008-04-10
Loaded 7.10, no problems there, Firefox 2.0.0.12.
Maybe I should just reload FF in 7.04 via Synaptic.

---

### Post by laidback on 2008-04-10
OK, have FF v3 working. But it's no better. Must be something to do with my installation I reckon.
Got this msg in the terminal :-

(Gecko:6201): GLib-CRITICAL **: g_hash_table_unref: assertion `hash_table != NULL' failed

Any offers?
Many Thanks

---

### Post by laidback on 2008-04-10
May have found the solution to this problem.
I removed the ~/.mozilla directory and then the next time I used FF it created a new one. This time Ebuyer and Ebay seemed to load fine.
Wonder if it's got soething to do with passwords as I have an account with both of these sites.
Maybe it's fixed.

---

