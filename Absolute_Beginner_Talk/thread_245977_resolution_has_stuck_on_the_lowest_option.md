---
title: "resolution has stuck on the lowest option"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by lostfool on 2006-08-28
The number of pixels on my computer screen has stuck on the very lowest alternative. When I tried to modify the settings, I found that there were only one option to choose from, i.e. the lowest alternative, 640 * 480 pxls. Before I changed the options from the highest to the lowest alternative, there were about six different options to choose from. Now there is only the lowest one left, for some reason. Why has this happened? How do I do to enable all of my six original options?

---

### Post by calvinthomas on 2006-08-28
Go to a terminal (Click applications, accessories, terminal)

Type sudo dpkg-reconfigure xserver-xorg and press enter

Enter your password

Answer questions by pressing enter lots of times, you'll get to a resolution part press spacebar to select the resolutions you want then press enter again until the end

Restart computer, it'll be on the highest resolution you selected and all lower ones will be available in the method you mention previously.

NOTE: THIS WILL RESET YOUR GRAPHICS DRIVERS IF YOU HAVE MANUALLY SET THEM UP YOU WILL HAVE TO DO IT AGAIN!

Calv

---

