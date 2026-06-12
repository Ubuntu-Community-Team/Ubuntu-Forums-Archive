---
title: "Memory problem concerning firefox"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-06-30
I have been worried the last couple of days due to a rare behavior concerning firefox and its memory usage. 
For example, i have now 4 tabs open:

[www.clarin.com](www.clarin.com) (local newspaper with a lot of flash)
[www.datafull.com](www.datafull.com)
[www.youtube.com](www.youtube.com)
The tab where i am creating this post

Right now my memory usage regarding firefox is 82,9 out of 512 MB total. I have told my friends who have ubuntu to open the same tabs with firefox and the memory consumed by their browser was a little more than a half.

Considerations about my system:

I recently enabled vm.swapiness=0 in sysctl.conf
I have the Metal Lion - Vista theme in firefox
I dont have direct acceleration enabled on my graphics card

I dont know if these 3 considerations affect the firefox memory usage, or if its just my computer who likes the flavour of my ram lol. If anyone could open the same tabs and post how much memory their firefox is eating it would be great

Best regards

PS: Dont fear opening those web pages, they are not a threat for anyone and are completely safe

---

### Post by Obor on 2007-06-30
My firefox is sitting on about 90MB of my 512MB memory. I don't see it as a problem. That's what the RAM is for IMO.

---

### Post by insane_alien on 2007-06-30
60 tabs, 112MB(i felt like stress testing it so i loaded every one of my bookmarks

although, if you visit a page with thousands of images on the one page it can easily be more with only 1 tab.

firefox is a bit memory hungry but generally it won't cause problems

---

### Post by ferpadro on 2007-06-30
you guys opened the tabs i suggested? just to check...

---

### Post by Papi-KB7VGW on 2007-06-30
Hi  I opened your 3 tabs plus 2 of mine and was only using 67M  The interesting thing is with just my tabs it was 58M.

---

### Post by alienexplorers on 2007-06-30
When running java or flash or a combination of the two with lots of tabs open then Firefox can become a memory & CPU hog.

---

### Post by ferpadro on 2007-06-30
i see....maybe im just too paranoic, or maybe i should try to avoid having [www.clarin.com](www.clarin.com) open for a long time, it has a lot of flash embedded there.
Regarding the swap space and the way Ubuntu handles pagination, do you think it would be wise to keep vm.swapiness at 0, or should i try a higher value?

---

### Post by smo0th on 2007-06-30
When opening a web, the browser downloads the objects to a temp folder and it's a different story if you open a text web than a gallery of images, then if you have flash animations or embedded videos like in youtube and others your browser will use more memory, also if you install cute themes the graphics will take more memory and cpu so don't be paranoic, by the way Firefox sometimes has memory leaks and if you run it for long periods of time or stress-run it it could left some unuseful memory without dumping it.

so, 3 things:

keep your firefox updated
be aware of the addons you install to firefox
if you feel it takes too much memory, restart firefox

and perhaps you wanna try netscape or opera just to compare performance

:popcorn:

---

### Post by ferpadro on 2007-07-01
I tried Opera but it seems to have a problem with the embedded flash. Everytime i want to see a video on youtube i need to left-click on the video to actually show the first image. I tried seamonkey but it felt so Netscape lol, and so old, i rejected it inmediately. I tried almost every browser (epiphany, kazehakaze, opera, seamonkey, swiftfox, swiftweasel, konqueror, galeon, dillo) and all of them had some feature i didnt like. I think ill stick with firefox, and keep Seamonkey as a backup

Thanks :D

---

### Post by smo0th on 2007-07-03
wow, nice work as a browser tester! ;) 

and wise choice, i prefer to use firefox, it's just the one that's best for my needs and there are several very useful addons =)

---

### Post by kerry_s on 2007-07-03
61 here on a 450mhz 256ram laptop.

---

### Post by ferpadro on 2007-07-03
I knew a couple of pages could not make firefox memory usage more than 60 MB. I find this rather odd. Whenever i load a page with flash like the one i posted, and then i close it (of course having more than one tab open) memory does not seem to flush. Could it be related to the disk space destinated for cache? Right now i have only 15 mb of cache and it does not seem quite a change.
Comment please

Best Regards

---

