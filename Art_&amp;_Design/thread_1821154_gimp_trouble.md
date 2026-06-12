---
title: "gimp trouble"
date: 2011-08-08
forum: Art &amp; Design
---

### Post by p.wolf on 2011-08-08
hey, im following a tutorial in which i need the resynthesize plugin. i downloaded it and placed the files into the plug ins folder, as they have a .py extension.  this didn't work so i also tried them in he scripts folder, still no luck. help please?

thanks~

---

### Post by prokoudine on 2011-08-09
> **p.wolf said:**
> hey, im following a tutorial in which i need the resynthesize plugin. i downloaded it and placed the files into the plug ins folder, as they have a .py extension.

You did it right. All files in plugins folder should be executable. Did you do it? Place .py files back to plugins folder and check if they have "Executable" checkbox on in file properties dialog.

Also, I hope you restarted GIMP if you had it running at the moment. GIMP cannot pick new plug-in while it's running.

---

### Post by p.wolf on 2011-08-09
i did, no luck :(
i will check if they are executable

---

### Post by p.wolf on 2011-08-09
still doesn't work :(

---

### Post by prokoudine on 2011-08-10
> **p.wolf said:**
> still doesn't work :(

Please run

ls -lh ~/.gimp-2.6/plug-ins/

in terminal and post the output

---

### Post by p.wolf on 2011-08-10
bryan@p:~$ ls -lh ~/.gimp-2.7/plug-ins/
total 260K
-rwxr-xr-x 1 bryan bryan 6.5K 2011-04-13 18:24 plugin-heal-selection.py
-rwxr-xr-x 1 bryan bryan 3.1K 2011-04-13 19:42 plugin-heal-transparency.py
-rwxr-xr-x 1 bryan bryan  17K 2011-04-13 19:39 plugin-map-style.py
-rwxr-xr-x 1 bryan bryan 7.6K 2011-04-13 19:31 plugin-render-texture.py
-rwxr-xr-x 1 bryan bryan 3.3K 2011-04-13 19:22 plugin-resynth-enlarge.py
-rwxr-xr-x 1 bryan bryan 3.6K 2011-04-15 20:12 plugin-resynth-fill-pattern.py
-rwxr-xr-x 1 bryan bryan 3.2K 2011-04-13 21:12 plugin-resynth-sharpen.py
-rwxr-xr-x 1 bryan bryan 5.9K 2011-04-13 19:24 plugin-uncrop.py
-rwxr-xr-x 1 bryan bryan  62K 2011-04-15 22:37 resynthesizer
-rwxr-xr-x 1 bryan bryan  53K 2011-04-15 22:37 resynthesizer-gui

---

### Post by prokoudine on 2011-08-10
Ahem... Can you see other Python plug-in at all? Filters/Web/Slice...? Filters/Python-Fu/(Anything)?

---

### Post by SoFl W on 2011-08-10
In GIMP, Edit-> Preferences-> Folders option, plug-ins option is your folder listed there?

[B]
EDIT:[/B] 
See if it is in a different section such as Script-Fu

---

### Post by SoFl W on 2011-08-10
Others are complaining of the same problem, read through the comments at
[http://registry.gimp.org/node/25219](http://registry.gimp.org/node/25219)

---

### Post by Miss Fashion on 2011-08-11
I have the similar problem with you! 
 
I just installed the resynthesizer 0.16 plugin and the heal plugin also. I made the patch to the smart-remove.scm file. The heal tool seams to work fine but the resynthesizer tool is not performing nearly as well. I tried various settings within the resynthesizer tool and have yet to see any useable transformations. One image I the tool on was a red bricked lighthouse with a window midway up the structure. When I used the resynthesizer tool to remove the window, the area was replased with a murky darker brown colered area. I used the heal tool on the same and it worked fine. Am I missing something. I thought the resynthesizer tool was the more powerful plugin? Are there any patches to resynthesizer 0.16 that would clean up the functionality of this tool.

---

