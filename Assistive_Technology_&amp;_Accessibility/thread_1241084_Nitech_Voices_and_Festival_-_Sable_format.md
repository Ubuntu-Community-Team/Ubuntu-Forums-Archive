---
title: "Nitech Voices and Festival - Sable format"
date: 2009-08-15
forum: Assistive Technology &amp; Accessibility
---

### Post by OBI_Ron on 2009-08-15
Hello Everyone,

The title almost says it all - I have Festival set up, and can use the Nitech voices.  However, it seems as if the Nitech voices don't work when used in sable.  At least they don't seem to respect the tags.

I have the following in the .sable file:

<?xml version="1.0"?>
<!DOCTYPE SABLE PUBLIC "-//SABLE//DTD SABLE speech mark up//EN" 
        "Sable.v0_2.dtd"
[]>
<SABLE>
<SPEAKER NAME="nitech_us_awb_arctic_hts">

Today<BREAK LEVEL="Medium" TYPE=","/>and every day:

</SPEAKER>
</SABLE>

When I use a different voice, the tags are respected, and the output sounds like what I would expect.  I also double checked this using the <PITCH> tag, using an extremely high value, and got the same results - it would work with non-Nitech voices.

Is there something I can do to work around this?  I really like the sound of the Nitech voices, but so far, it seems as though I have few options for controlling them.

Thanks in advance!

---

