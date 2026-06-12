---
title: "Ripping DvDs"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-13
If i wanted to burn a Dvd on to my computer, how would I go about this?
I hear that the program k9 copy can be used to do this, but i'm not exactly sure how to use this. I realize this isn't a forum for k9copy help, but i'm thinking it's not recognizing my hardware, or something.  When i click the "copy" button, after inserting a dvd, it says:
"dvd is not open" or something along those lines.
Does anyone have a tutorial on how to do this procedure, or any tips at all?
Thanks.

---

### Post by hyper_ch on 2007-12-13
do you have libdvdcss2 installed?

---

### Post by jordank on 2007-12-13
yes

---

### Post by jordank on 2007-12-13
anyone?

---

### Post by rockinlinux on 2007-12-13
when you put a DVD in the drive then open K9copy. in the left menu part there is a pciture of a folder, if you put you mouse on it it says "open". click this, the dvd will load onto the middle part of the screen alowing you to pick chapters you want to copy. when you are done picking the chapters eiter click the "mpeg" button you rip it in mpeg format ot the "dvd" button to make a .iso. Be sure to go to prefrances so you know where they are saving the files. 

K9copy is a great program, good luck and have fun!!

---

### Post by rockinlinux on 2007-12-13
also, i have never done this but i have rad that you can mount the .iso in ubuntu to watch the movie from the /iso file.

---

### Post by fenian on 2007-12-13
There is a nice little guide for k9copy[ here.]("http://www.dvd-guides.com/content/view/213/59/")

---

### Post by jordank on 2007-12-13
awesome. thank you.

---

### Post by rechick on 2007-12-13
You may also find using AcidRIP is a quick, simple and easy way to rip a DVD to an AVI file on the computer.

---

### Post by straps on 2007-12-13
[http://del.icio.us/straps/rip](http://del.icio.us/straps/rip)

---

### Post by jordank on 2007-12-13
I read the tutorial and it was very helpful.  I do have one question though, maybe someone expeirience with k9 copy would be able to help out.  Once i tell it to make an iso image, it seems the last step of this process is the "dvd burning" part.  
When it gets to this stage, is it essentially burning over the dvd that i have inserted, or is it saying it's ripping the dvd from the original to the new iso image?
This stage confused me.

---

### Post by mc4man on 2007-12-13
it's converting the temp video_ts folder stored in /tmp to an iso - probably in your home folder

---

### Post by jordank on 2007-12-13
Yeah, i got it all figured out now.  However, when i rip to an .iso file, the size of my images are 4.3 gigs.  Will these fit on a dvd? If not, how can I shrink this down?
I thought a dvd was 4 gigs, what's the story?

---

### Post by fenian on 2007-12-13
Yes it will fit a standard dvd is 4.7 gigs.

---

### Post by jordank on 2007-12-13
perfect.  Will it play on all machines, or is it encoded a special way?

---

### Post by fenian on 2007-12-13
It should play on all machines.

---

### Post by jordank on 2007-12-13
awesome thank you

---

### Post by ctyc on 2007-12-13
Try Handbrake for command line backups of dvds

[http://handbrake.m0k.org/](http://handbrake.m0k.org/)

handbrake command line usage example:

HandBrakeCLI -f avi -e ffmpeg -E lame -S 1400 -i /dev/cdrom -t 1 -o movie.avi

---

