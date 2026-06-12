---
title: "double gimp?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-15
[http://www.flickr.com/photos/paperclipsandscrambledeggs/499620615/](http://www.flickr.com/photos/paperclipsandscrambledeggs/499620615/)

i have a problem.  i seem to have two versions of gimp on my computer.  when i right click on a file and select "open with gimp," it opens up gimp as shown on the left in the screenshot.  if i open up gimp any other way, it shows up as shown on the right.  the problem is that i like the one on the left better.  is there any way i can get rid of the one on the right?  it appears to be an older version.

---

### Post by nightskywind83 on 2007-05-15
Hmm... this one's interesting...

Did you install the newer GIMP from somewhere other than the Ubuntu repositories?

Run Synaptic and search for GIMP and look for the installed version and compare it to the ones you have installed...

Just some thoughts...

---

### Post by locke.dragon on 2007-05-15
nothing out of the ordinary there.

---

### Post by Ziox on 2007-05-15
sudo aptitude search gimp
what's the output?

---

### Post by locke.dragon on 2007-05-16
```

link@aperturescience:~$ sudo aptitude search gimp
p   babygimp                        - An icon editor in Perl-Tk                 
p   cupsys-driver-gimpprint         - printer drivers for CUPS                  
p   flegita-gimp                    - Gnome Gimp scan plugin.                   
p   foomatic-db-gimp-print          - OpenPrinting printer support - database fo
i   gimp                            - The GNU Image Manipulation Program        
p   gimp-cbmplugs                   - plugins for The GIMP to import/export Comm
i   gimp-data                       - Data files for The GIMP                   
p   gimp-data-extras                - An extra set of brushes, palettes, and gra
p   gimp-dbg                        - Debugging symbols for The GIMP            
p   gimp-dcraw                      - GIMP plug-in for loading RAW digital photo
p   gimp-dimage-color               - GIMP plugin to convert Minolta DiMAGE pict
p   gimp-gap                        - The GIMP Animation Package                
v   gimp-help                       -                                           
p   gimp-help-common                - Data files for the GIMP documentation     
p   gimp-help-cs                    - Documentation for the GIMP (Czech)        
p   gimp-help-de                    - Documentation for the GIMP (German)       
p   gimp-help-en                    - Documentation for the GIMP (English)      
p   gimp-help-fr                    - Documentation for the GIMP (French)       
p   gimp-help-it                    - Documentation for the GIMP (Italian)      
p   gimp-help-nl                    - Documentation for the GIMP (Dutch)        
p   gimp-help-sv                    - Documentation for the GIMP (Swedish)      
p   gimp-help-zh-cn                 - Documentation for the GIMP (Chinese Simpli
p   gimp-helpbrowser                - Built-in Help Browser plugin for The GIMP 
v   gimp-perl                       -                                           
i   gimp-print                      - print plugin for the GIMP                 
i   gimp-python                     - Python support and plugins for The GIMP   
p   gimp-resynthesizer              - Gimp plugin for texture synthesis         
p   gimp-svg                        - SVG (Scalable Vector Graphics) plugin for 
p   gimp-texturize                  - generates large textures from a small samp
p   gimp-ufraw                      - gimp importer for raw camera images       
p   gimp2.0-quiteinsane             - A Qt based SANE plugin for GIMP 2.0       
p   grokking-the-gimp               - GIMP tutorial book by Carey Bunks (HTML)  
p   gtkam-gimp                      - gtkam gimp plugin                         
p   ijsgimpprint                    - printer drivers for CUPS                  
p   libgimp-perl                    - Perl support and plugins for The GIMP     
i   libgimp2.0                      - Libraries necessary to Run the GIMP       
p   libgimp2.0-dev                  - Headers and other files for compiling plug
p   libgimp2.0-doc                  - Developers' Documentation for the GIMP lib
p   mrwtoppm-gimp                   - GIMP-plugin to support Minolta DiMAGE 5/7/
p   planetpenguin-racer-gimp-dev    - plugins for GIMP for easy development of p
link@aperturescience:~$ 

```

---

