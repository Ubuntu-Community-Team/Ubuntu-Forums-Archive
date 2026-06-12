---
title: "Another E17 thread"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-12-11
I wonder if anyone experimenting with E17 has had any luck making their own backgrounds.  I tried to do so using the instructions in the manual, which involve using an .edc file to generate an .edj file, which is used for the background.  It all appeared to work correctly, but the desktop refuses to add it.  I have no problem using the alternate backgrounds provided on the E17 website.  The instructions are here:

[http://get-e.org/E17_User_Guide/English/_pages/3.8.html](http://get-e.org/E17_User_Guide/English/_pages/3.8.html)

If anyone's figured this out, I'd be grateful for any insight you could share.  Thanks!

---

### Post by Bagger on 2005-12-11
I have had no problems creating backgrounds... following is a sample background .edc file and below that is the build script. After you compile the . .edj file copy it to your backgrounds folder. 

In this case this is a full sized image, there is a slight difference in a tiled image but I do not recall what it was now.

Hope the following gets you on the right track

fonts {
}
images {
	image: "/trilogyBG.png" COMP;
}
data {
}
collections {
	group {
		name: "desktop/background";
		parts {
			part {
				name: "background_image";
				type: IMAGE;
				mouse_events: 0;
				description {
					state: "default" 0.00;
					visible: 1;
					rel1 {
						relative: 0.00 0.00;
						offset: 0 0;
					}
					rel2 {
						relative: 1.00 1.00;
						offset: -1 -1;
					}
					image {
						normal: "/trilogyBG.png";
					}
				}
			}
		}
		programs {
		}
	}
}




Build script, build.sh, seperate file

#!/bin/sh
edje_cc $@ --image_dir . --font_dir . trilogy.edc -o trilogy.edj

---

### Post by deNoobius on 2005-12-11
Thank you so much!  I'll try it.  The only obvious difference I see with what I did is the forward slash before the file name--and that might make the difference, because I am in fact compiling in the same directory where the image file resides.  

I'll post the results.

---

### Post by deNoobius on 2005-12-11
Bagger, your script worked!! Sweeet! Thanks a million!  I'm going to post the results in the gallery!

---

