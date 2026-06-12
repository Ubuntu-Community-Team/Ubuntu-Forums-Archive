---
title: "No Left-Click Copy Image in Firefox (Feisty)"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by scriptoris on 2007-09-11
Why is there no Copy Image option when you left-click on an image in Firefox on Ubuntu Feisty? The options are: Copy Image LOCATION, Send Image, Save Image, et cetera, but there is no simple COPY IMAGE.

The only recourse is to save images individually, but that's tedious. If I have my web album open and just want to copy and paste an image into GIMP, why can't I just do that?! I don't want to drag the files onto my desktop either, as that's tantamount to saving them. Why is such a simple, basic, vital feature missing in Firefox on Ubuntu? :(

EDIT
I toggled with the about:config and that didn't help. I also installed a particular Firefox extension to copy images, but when I click copy button, it still won't perform this action..

BIZARRE?

---

### Post by bone2006 on 2007-09-11
Do you have this issue in windows?

---

### Post by scriptoris on 2007-09-11
No. On my Windows XP desktop and laptop computers, Firefox ALWAYS lets me Copy an image into Photoshop.

On Ubuntu, Firefox doesn't even have a COPY IMAGE option, so I can't load anything into GIMP without saving it first.

---

### Post by asmoore82 on 2007-09-11
> **scriptoris said:**
> Why is there no Copy Image option when you left-click on an image in Firefox on Ubuntu Feisty? The options are: Copy Image LOCATION, Send Image, Save Image, et cetera, but there is no simple COPY IMAGE.

The only recourse is to save images individually, but that's tedious. If I have my web album open and just want to copy and paste an image into GIMP, why can't I just do that?! I don't want to drag the files onto my desktop either, as that's tantamount to saving them. Why is such a simple, basic, vital feature missing in Firefox on Ubuntu? :(

EDIT
I toggled with the about:config and that didn't help. I also installed a particular Firefox extension to copy images, but when I click copy button, it still won't perform this action..

BIZARRE?

Linux, or more spefically X11 because this issue exists on all UNIX systems running X11, does not
provide a standard "clipboard" for applications.

You may have noticed that if you "copy" text in any application and
then close the app, the text can no loger be "pasted" anywhere.

The real old-school way that X11 allows copy/paste of text is to simply highlight text somewhere,
then middle click (or wheel click) anywhere else and the text with be pasted.

for your image issue, click on "Copy image location" in firefox,
then in the GIMP, click "File -> Open Location" and paste in there.
The GIMP will automatically download the image and open it for editing for you.

---

### Post by scriptoris on 2007-09-11
> **asmoore82 said:**
> for your image issue, click on "Copy image location" in firefox,
then in the GIMP, click "File -> Open Location" and paste in there.
The GIMP will automatically download the image and open it for editing for you.

**Thanks!** That's perfect.. or as perfect as it's going to get, at least. When I load these images this way, will they store in a folder permanently until I remove them? Just want to make sure if they do so I can remove them afterwards.

---

### Post by asmoore82 on 2007-09-12
> **scriptoris said:**
> **Thanks!** That's perfect.. or as perfect as it's going to get, at least.** When I load these images this way, will they store in a folder permanently until I remove them?** Just want to make sure if they do so I can remove them afterwards.

it doesn't seem to... 8) excellect... you are not allowed to simply "save"
them because they aren't stored locally, you have to "save as"

---

### Post by LowSky on 2007-09-12
i think im confused, why cant you right click, choose copy and the go to where ever and right click and paste? Seems to work fine for me.

---

### Post by hyper_ch on 2007-09-12
why not directly saving them out of FF and set the FF download folder to e.g. /home/user/Desktop/FF-Downloads or something similar...

---

### Post by Ian505 on 2008-01-01
Isn't there a extension or something that provides this feature? I really need it as I simply haven't learned to use GIMP and want to paste multiple images into a program called KolorPaint... but copying and pasting copies and pastes the URL of the image not the image itself. I am forced to download and even then I have to open the image in KolorPaint (new window) select the whole image in KolorPaint and THEN copy and paste it into my other image. I really have come to depend on copying and pasting and it hinders me not to have it, or more precisely not have have it as a tool for CONVENIENCE.

-Ian

EDIT- I am using Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11.

---

