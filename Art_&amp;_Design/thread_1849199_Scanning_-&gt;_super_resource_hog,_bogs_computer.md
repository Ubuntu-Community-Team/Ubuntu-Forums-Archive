---
title: "Scanning -&gt; super resource hog, bogs computer"
date: 2011-09-24
forum: Art &amp; Design
---

### Post by scu-ba-de-buntu on 2011-09-24
Using Simplescan is helpful for scanning my notes from class, but when I save to PDF it basically locks up my computer. I set the priority to 10 and this fixes the problem enough that my mouse responds now, but it is still a problem. My computer only has about 1.8Gb of Ram and Simplescan plus convert (which apparently is called by simplescan) uses almost all available Ram. Is there a way to prevent this? I don't mind doubling processing time if it means that I don't have to wait for each set of notes to finish scanning before I can type essays. We are talking about 10 maybe 15 pages at a time. I did more but it locked my computer for quite a while. In addition, I believe there may be a memory-leak as after closing the program there is still a slight hang in response-time until rebooting.

---

### Post by MarjaE on 2011-09-26
I was scanning one of my old notebooks - which took hours - when simplescan just quit all of a sudden. I restarted simplescan but everything was gone.

---

### Post by scu-ba-de-buntu on 2011-11-10
> **MarjaE said:**
> I was scanning one of my old notebooks - which took hours - when simplescan just quit all of a sudden. I restarted simplescan but everything was gone.

MarjaE: That stinks! Did you report your crash to the simplescan peoples? Also, was there a 'core' file dumped?

I believe the speed problem is tied to Image conversion. Not sure about a memory-leak yet. Partially solved (tolerated) by changing priorities such that it is less important than other programs.

---

