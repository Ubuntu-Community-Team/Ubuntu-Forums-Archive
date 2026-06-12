---
title: "[SOLVED] Problems Printing Photos with an HP Photosmart C6180"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by MidChaos on 2007-03-19
I have recently acquired a new HP Photosmart C6180 printer for my home network. I am able to configure it in Ubuntu and Edubuntu Feisty Fawn versions that were/are up-to-date. Everything seems to work fine, however I cannot print photos quite the way I would like.

I tried a few programs to print on 4x6 inch photo paper. For example, using OpenOffice.org program I am able to print the picture, however it prints with a border and I would like to do borderless. I have also tried the Image Viewer program that opens the pictures by default, it does the borderless but does not print on the bottom (approximately) 1/5th of the paper. So it seems to me to be a program issue. I also was going to try to use GIMP, but I cannot print on it because it does not see my printer and I cannot set it up as it is not in the list of printers under HP (in the GIMP software).

I am able to print exactly as I would like if I take the extra (annoying) steps of putting it on a picture card and plugging it directly into the printer. It is functional, but my wife would prefer I find a better solution.

I have tried to research this problem but have not seen anything that seemed to be helpful in this matter. What I am hoping is that someone may know what I may be doing wrong or how I can get things to run the way I would like. If someone can help, please do.

Also a note, it would be my preference to have a clean thread (low post count), so if you are going to post that you have the same problem please do me a favor and do not, it doesn't exactly help me reach a conclusion to the problem I am having.

I appreciate any help that you all may be able to give me. Much thanks in advance!

---

### Post by 11hjpphty76lkjj on 2007-03-23
For borderless (fullebleed) printing, please look here:

[http://hplip.sourceforge.net/howtos/printing.html](http://hplip.sourceforge.net/howtos/printing.html)

---

### Post by MidChaos on 2007-03-28
Thank you for that link. That did indeed help me to print from GIMP and showed me how to change my settings to do bleedless printing. However, and this may be a lack of experience from me, it doesn't completely bring me to the resolution I was hoping for. When I try to print on our 4x6 inch paper it still leaves a white space at the end of the paper. I am not sure completely if this is a problem from the computer now or if the printer compensates better for paper flaws. I am not convinced that my paper is a perfect 4x6 but closer to a 4x6.5. I guess I will have to try to do a custom paper size in the applications and see if I can't get it to print on the whole thing.

Thanks for the help so far, I also welcome other suggestions or advice as to how better to print as I want to.

---

### Post by 11hjpphty76lkjj on 2007-03-28
Would it be possible for me to get a copy of the image you are trying to print and I'll see if I can print it on 4x6 here?

A

---

### Post by finite9 on 2007-04-01
I just posted a similar thread to this, as I have the same issue.

Gnomes Image Viewer aka Eye of Gnome, can select 4x6 Canon paper, but still has a border, and there does not seem to be a program option to override this which is a shortcoming of the program which I hope gets fixed.

Gimp, as you already found out, is time consuming to setup and not really ideal for 'the wife'.

F-Spot comes the closest to being able to print borderless, and I can almost live with it, but it does not crop the image so there is still a little white border.

All this stems from the fact that images taken with a consumer digital camera are not 4x6.  In Windows, when you print such an image, Windows automatically crops quite a large portion of the longest edge of the image so that the rest of the image fits perfectly on borderless 4x6.  It is this feature that is lacking in standard Gnome tools (have not looked into KDE tools).

---

### Post by MidChaos on 2007-08-08
Alright, I know I haven't come back to this in awhile, but I had some time today and as of about 20 minutes ago resolved my own problem with the help of a few ideas from other posts.

To resolve the borderless printing of photos I installed the most up-to-date HPLIP available from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

I downloaded the Self Extracting Archive with Installer and went through the steps (bringing me up to version 2.7.7 of HPLIP). What I liked was that it did the work for me and asked me just a few questions. Then I ran the hp-setup that it had installed and set up my printer through that. The reason I did this was to try to get the scan feature through the XSane application, as a bonus I tested a picture through the default Ubuntu app and it printed perfectly once I figured out my settings (page setup to proper size is all I did and then set photo paper in print).

I am so excited about this, I can't wait till my wife gets home from work so she can share in my joy!

Thanks guys for providing the insight, I hope what I did can help someone else.

---

### Post by PsycoGeek on 2007-10-09
Please post the application you used to print, and the exact settings you used.  I have yet to get a 4x6 print out of my printer (using Picasa).  I do have the latest HPLIP installed, and have had it there for quite a while.  I also have the same printer.

---

### Post by MidChaos on 2007-10-09
I opened the picture with Image Viewer (default option for me). I went to File >> Page Setup and changed the printer to my All In One, then selected the paper size of Photo with tear off tab (that's what my wife bought, this paper has an easy to remove part which is where the white part is left) and hit Apply*. Then I went to File >> Print... and went to Page Setup and selected the source as paper tray. Then under Advanced tab and selected the Printout Mode as Photo. I left everything else as default.

* Don't forget to set the page layout properly, either portrait or landscape.

The printing takes a bit before it starts for me, I'm not sure if that's an issue or if it's the size of the file (I would guess it's an issue). If you go to monitor it that seems to speed it up somewhat so that it starts printing.

---

### Post by PsycoGeek on 2007-10-09
Thank you.

---

