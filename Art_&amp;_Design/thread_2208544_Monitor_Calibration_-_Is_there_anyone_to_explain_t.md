---
title: "Monitor Calibration - Is there anyone to explain things?"
date: 2014-02-28
forum: Art &amp; Design
---

### Post by achuthpnr on 2014-02-28
Monitor calibration + printer calibration are necessary for getting good quality printed graphics/photos. Many photographers have accessibility to good quality cameras but do not own a printer and print in other facilities. These are the two scenarios I understood:

1. Own calibrated monitor and printer
2. Own calibrated monitor + Some other calibrated printer, given its printer profile
3. Online graphic artists: only need to calibrate monitor since it is not printed

The three main settings available are white point, gamma and luminance. In the support forums for various colorimeters, they give different answers why one should and should not use some specific values and some times they contradict. 

In scenario 1, I believe they could use whatever values to white point etc., but should give a match with the monitor when printed. 
I  am not sure how to proceed in scenarios 2 and 3. Probably, one could  get some trial prints and match the monitor to look closer in case 2,  but clueless about case 3. What is the reference here as there are a  wide variety of displays around?

It would be great if somebody could explain the correct parameters to use during a colorimetric calibration, not particularly intended for printing.

---------

What I use? : white point - native, gamma - 2.2, luminance - ~90 cd/m^2 . Is this setting correct? 
I tried argyll cms + dispcalgui and eye-one match using an eye-one display. Both gave slightly different results for the same settings. I dont know which one is more "accurate"  now.

---

### Post by coldraven on 2014-03-01
I am sadly ignorant of the mysteries of colour matching. One thing that I discovered is that having a photo printed at my local photo lab resulted in a marked difference to what I could print on my six colour inkjet. The lab print lost subtle colour variations.
I read somewhere that if you ask your local lab for a colour profile for their machine* it should be possible to add it to Gimp to give some consistency to your prints.
*Or rather ask them for the make and model then download it from the manufacturers.

---

### Post by tgalati4 on 2014-03-01
Color profiles are used simply to match input to output.  If you are doing an advertising layout for a company and their logo is orange and you work up a layout in Inkscape or AdobeCS, you want that logo to still be orange when it gets printed on a massive billboard.  The company would be pissed if it came out brown.

If you are a photographer, your camera can capture many stops of light more than can be shown on your monitor or can be expressed in a print.  So if your camera can capture 8 stops of light (from brightest highlights to darkest shadows), you want that entire range (gamut) to be visible in your monitor and also in a print.  A simple example is a wedding photo of a bride and groom.  You want to simultaneously get the details of the white wedding dress and some details in a black tuxedo.  You don't want a glowing white dress and a completely black tux.  So you calibrate your monitor using an ICC profile that better matches what your camera can capture.  There are a lot of limitations in this process.  So you have to compromise a lot.

Whatever your workflow, you should include a color test chart (like a MacBeth Color Checker) and compare your output colors to the final result.  Any differences should be noted and corrections applied through the color profile (ICC) until your match is the best that is possible with the technology used.

---

### Post by kurja on 2014-04-01
Here's a good page about calibration: [http://www.cambridgeincolour.com/tutorials/monitor-calibration.htm](http://www.cambridgeincolour.com/tutorials/monitor-calibration.htm)

As far as I understand the monitor brightness should be adjusted so you can distinguish both dark and bright tones, other settings at whatever gives the widest gamut (usually default settings) then you use a display colorimeter to profile the monitor. Colorimeter [software]("http://dispcalgui.hoech.net/") should guide you to adjust monitor settings if they're off. For printing, get the printer's profile in gimp (or whatever you use) to [softproof]("http://docs.gimp.org/en/gimp-imaging-color-management.html"). If it's your own printer, you'll need a printer colorimeter to make the profile.

---

