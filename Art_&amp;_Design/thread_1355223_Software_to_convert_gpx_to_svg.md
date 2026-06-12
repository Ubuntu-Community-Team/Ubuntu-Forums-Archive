---
title: "Software to convert gpx to svg?"
date: 2009-12-14
forum: Art &amp; Design
---

### Post by doncristobal on 2009-12-14
Does anyone know a piece of software that converts gpx files (gps exchange format) to svg graphics files? Gpsbabel does not know svg.

I think it would be a fairly simple tool because both formats are straightforward xml derivatives. 

Background: I need to import gpx tracks to scribus. Scribus can import svg, but not gpx.

Thanks a lot for any hint! 

Example extracts: 
gpx: 
<trkpt lat="46.9371555" lon="7.3924233">

</trkpt>

<trkpt lat="46.9371915" lon="7.3923445">

</trkpt>

<trkpt lat="46.9372184" lon="7.3922657">

</trkpt>

svg: 
<path fill='#000000' d="M1995.59 617.046c0,37.8969 30.7919,68.8247 68.6334,69.0614 -26.5923,26.9246 -26.4966,70.567 0.302128,97.3607 (...) -0.312199,97.3607 -37.8365,0.241702 -68.6233,31.1695 -68.6233,69.0614z"/>

In the worst case, I might try to write this by myself... but there, I'm not sure I'd succeed with my basic knowledge of perl, and very basic knowledge of gpx and svg.

---

