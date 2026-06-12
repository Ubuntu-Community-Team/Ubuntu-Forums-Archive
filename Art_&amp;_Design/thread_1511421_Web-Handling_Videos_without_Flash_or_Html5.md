---
title: "Web-Handling Videos without Flash or Html5?"
date: 2010-06-16
forum: Art &amp; Design
---

### Post by MasterNetra on 2010-06-16
I was wondering if someone knew how to host+run a video file in like a player on a site without using Flash or HTML5 (as its not complete or widely supported yet)?

---

### Post by Alan James on 2010-06-18
I have been looking for the same thing and have not found it yet.

---

### Post by Linuxforall on 2010-06-18
Minitube handles all youtube stuff without flash, don't know if that would actually suit your purpose here.

---

### Post by Merk42 on 2010-06-19
There isn't one, that's the problem that Flash (and later HTML5) solve.

Back before Flash was used for videos, they had to be encoded into different formats; Windows Media, Quicktime, and some sort of AVI.  The problem is that there is no guarantee the viewer has the proper codec to view the video file.
Flash solves this by bundling the codec with its player.
HTML5 solves this by bundling the codec with the browser.

---

### Post by MasterNetra on 2010-06-19
> **Merk42 said:**
> There isn't one, that's the problem that Flash (and later HTML5) solve.

Back before Flash was used for videos, they had to be encoded into different formats; Windows Media, Quicktime, and some sort of AVI.  The problem is that there is no guarantee the viewer has the proper codec to view the video file.
Flash solves this by bundling the codec with its player.
HTML5 solves this by bundling the codec with the browser.

hmm I suppose I'll have to deal with flash in that matter until html5 is in place. :/

---

### Post by MasterNetra on 2010-06-19
> **Linuxforall said:**
> Minitube handles all youtube stuff without flash, don't know if that would actually suit your purpose here.

I doubt it considering I want to ENCODE video into a webpage and have it viewable to people. I guess either youtube or flash will have to do.

---

### Post by NightwishFan on 2010-06-19
If they have Firefox 3.5+ (or chrome?) just embed an ogg theora video in the page (like wikipedia). Use the <video> tag. (I think)

---

### Post by MasterNetra on 2010-06-19
> **NightwishFan said:**
> If they have Firefox 3.5+ (or chrome?) just embed an ogg theora video in the page (like wikipedia). Use the <video> tag. (I think)

Only problem is I am designing professionally and there is that pesky fact the IE is widely used.

---

### Post by NightwishFan on 2010-06-19
I see. Still dragging their legs, how quaint. Well I wish you luck. I suppose flash or similar is the only option.

---

### Post by Alan James on 2010-06-19
> HTML5 solves this by bundling the codec with the browser.

And it builds the player into the browser. No need to install an external player like Flash or Quicktime. Too bad the browsers haven't agreed on a standard video Codec yet.

---

### Post by Personal Jesus on 2010-06-19
> **Merk42 said:**
> 
Back before Flash was used for videos, they had to be encoded into different formats; Windows Media, Quicktime, and some sort of AVI.  The problem is that there is no guarantee the viewer has the proper codec to view the video file.

The sad part is that some sites continue to stream video in this manner.

---

### Post by MasterNetra on 2010-06-19
> **Alan James said:**
> And it builds the player into the browser. No need to install an external player like Flash or Quicktime. Too bad the browsers haven't agreed on a standard video Codec yet.

It would be easier just say ah forget and do both. As for the FOSS oriented browsers, just provide a addon for the Proprietary format(s) and let the browser prompt the user to install it when it comes across it. 
Choice > Forced

---

### Post by Merk42 on 2010-06-19
Well if you don't mind encoding the same file multiple times (Flash, ogg, h.264, WebM) you can use [Video For Everybody](http://camendesign.com/code/video_for_everybody)

Realistically though, Flash will serve the vast majority. The exceptions being FLOSS advocates and mobile users, though depending on your viewerbase you may not need to concern them.

---

### Post by MasterNetra on 2010-06-20
> **Merk42 said:**
> Well if you don't mind encoding the same file multiple times (Flash, ogg, h.264, WebM) you can use [Video For Everybody](http://camendesign.com/code/video_for_everybody)

Realistically though, Flash will serve the vast majority. The exceptions being FLOSS advocates and mobile users, though depending on your viewerbase you may not need to concern them.

Indeed, I guess they are just not that important yet. :p

---

