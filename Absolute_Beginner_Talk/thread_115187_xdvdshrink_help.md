---
title: "xdvdshrink help"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by vector on 2006-01-10
HI
I just got badly lost and need a GPS update :)
I was bashing thru the dvd copy stuff like an icebreaker ship when i realised i had dozens of web pages open and links everywhere and just brain splattered.
Here is what i have done.
1st id rather try xdvdshrink  than wine and dvdshrink(for the moment anyway)
totem wouldnt play the dvd to start with so 
I installed automatix and sure enough totem can now at least see and play the start of the dvd. when it gets to the menu screen totem gives an error "looks encrypted have you got libdvdcss installed"
I apt-get isntalled libdvdcss2 allthough I thought automatix did this?
ok now it works plays ok but has that interlace problem people mentioned(when things move) however ill worry about that later.

BUT i run xdvdshrink and it doesnt seem to see anything. Strangely it picks up the  the name of the project ok from the disk title but dosent see any titles, audio channels etc.
ok what am i doing wrong now

---

### Post by vector on 2006-01-11
ok i have progressed some what.
there was a bunch of tools  that werent installed. again I thought automatix did this. I manually apt-get installed them.

transcode
dvdauthor
*mjpegtools
subtitleripper
gocr
?dvd+rw_tools
*mkisofs
* were already installed 
? apt-get install dvd+rw_tools didnt work :(
however there is a dvd+rw-tools which was already installed
however xdvdshrink now recognises and i managed to shrink to mpegs a dvd. so were real close

I tried to burn dvd and noticed that the original had 8 titles. I set up the multiple tab and let it rip
one with make menu and one without.
both dvd "cup coasters" only have the 1 title on them. the menu one did also activate a menu screen with 8 titles but not matter what i did it went nowhere

---

