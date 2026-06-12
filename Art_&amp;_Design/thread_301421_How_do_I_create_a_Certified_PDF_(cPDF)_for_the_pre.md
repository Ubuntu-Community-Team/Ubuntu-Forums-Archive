---
title: "How do I create a Certified PDF (cPDF) for the press?"
date: 2006-11-17
forum: Art &amp; Design
---

### Post by TuxCrafter on 2006-11-17
Hello, I am struggling a will now to create a valid file that I can send to the press. 

I have made some artwork with the gimp (tiff.rgb) and need to convert this in (CMYK) Certified PDF (cPDF), Cebuco-standard or a standard below:

   1. Certified PDF
   2. JPG 300dpi (kwaliteit 12)
   3. TIFF 300 dpi (1 laag)
   4. EPS (tekst omzetten naar contouren/outlines)

I have tried several things but they did not work. I really have to find a way to convert RGB images to a press print ready file. Please help.

I already tried these techniques:

```
#/mnt/hda3/business/grafisch/Templates/xxx/postscript.sh

sudo apt-get install psutils
sudo apt-get install gs

cd /mnt/hda3/business/grafisch/Templates/xxx/

#gs -sDEVICE=pswrite -sOutputFile=frontpages.ps -dNOPAUSE -dBATCH front_1.ps front_2.ps front_3.ps
#gs -sDEVICE=pswrite -sOutputFile=backpages.ps -dNOPAUSE -dBATCH back_1.ps back_2.ps back_3.ps
#psnup -n 3 -p a4 frontpages.ps frontpages_combined.ps
#psnup -n 3 -p a4 backpages.ps backpages_combined.ps
#gs -sDEVICE=pswrite -sOutputFile=printfile_combined.ps -dNOPAUSE -dBATCH frontpages_combined.ps backpages_combined.ps
#lp -s -d 'HP_Color_LaserJet_8500DN' printfile_combined.ps

gs -sDEVICE=pswrite -sOutputFile="xxx.ps" -dNOPAUSE -dBATCH "xxx - Front - RGB.ps" "xxx - Back - RGB.ps"
./ps2pdfcmyk.sh "xxx.ps"

gs -sDEVICE=bitcmyk -sOutputFile=front_1.bitcmyk -r300x300 -dGrayValues=256 "xxx - Front - RGB.ps"
bitcmyk2tiff front_1.bitcmyk "xxx - Front - 300 - CMYK.tiff"

gs -sDEVICE=bitcmyk -sOutputFile=back_1.bitcmyk -r300x300 -dGrayValues=256 "xxx - Back - RGB.ps"
bitcmyk2tiff back_1.bitcmyk "xxx - Back - 300 - CMYK.tiff"

gs -sDEVICE=bitcmyk -sOutputFile=front_1.bitcmyk -r600x600 -dGrayValues=256 "xxx - Front - RGB.ps"
bitcmyk2tiff front_1.bitcmyk "xxx - Front - 600 - CMYK.tiff"

gs -sDEVICE=bitcmyk -sOutputFile=back_1.bitcmyk -r600x600 -dGrayValues=256 "xxx - Back - RGB.ps"
bitcmyk2tiff back_1.bitcmyk "xxx - Back - 600 - CMYK.tiff"

#lp -d 'HP_Color_LaserJet_8500DN' "xxx.ps"
#lp -d 'HP_Color_LaserJet_8500DN' "xxx_cmyk.pdf"
```

I think i found the solution when i was searching for some LaTeX isues.

```
sudo apt-get install imagemagick

convert "xxx - Back - RGB.tiff" -colorspace CMYK "xxx - CMYK.tff"
```

If this works there will be a lot of happy people here!

---

### Post by HanZo on 2006-11-17
I think krita supports CMYK. and you should be able to generate some decent pdfs with scribus, though I've never tried.

---

### Post by TuxCrafter on 2006-12-25
I used scribus and svg to fix it. (but support for professionals printing sucks under linux at this moment)

---

### Post by mcduck on 2006-12-28
Gimp doesn't handle CMYK, but I believe Cinepaint does..

---

### Post by TuxCrafter on 2006-12-28
I learned that all text must be vector based and in Linux that means svg. Images can be converted from RGB to CMYK with various tools. But they cannot contain any form of text.

So never make business card or folders etcetera with a bitmap program. Use a vector based programs for that and only bitmap for images.

I learned my lesson. And now understand how to make documents for printers.

---

