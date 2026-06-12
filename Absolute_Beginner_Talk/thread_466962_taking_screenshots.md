---
title: "taking screenshots"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by rjfioravanti on 2007-06-07
I want to take a screenshot of an image on my screen, so I can paste it into another application. However I don't want the hassle of getting the entire screen saved, then having to crop it with another application, then drop it into what I want finally.

Is there a way to highlight a specific area on your screen, and then take a picture of it? I know you can do this on a Mac so I am hoping we have something similar on ubuntu

---

### Post by Wolfiebad on 2007-06-07
Use KSnapshot. Download it via Synaptic.

---

### Post by H3g3m0n on 2007-06-07
Also GIMP will allow you to screenshot a window (not specific a region though).

Unfortunately cutting and pasting images and non-text across different programs doesn't work to well. I.e you can't cut and paste from Gimp into OpenOffice etc... You must save and then open it in that application.

---

### Post by rolando2424 on 2007-06-07
If you want to screenshot only a window, use ALT + Print_Screen_KEY

(This is in Gnome, I don't know if it works in KDE, XFCE, etc.

---

### Post by mhenriday on 2007-06-15
**Alt + Print Screen** takes a screenshot of the whole desktop and while **Applications&#8594;Accessories&#8594;Screenshot** does allow one to choose a single window, it does not allow one to highlight the relevant part of a window and take a shot only of that part. I don't know if this latter can be dome in **KDE**s **Ksnapshot**, or if there exists a counterpart to that application in **Gnome**....

For some reason, I can't seem to get the help function in **Gimp** to work ; how does one take a screenshot in that application, and is it possible there to highlight a portion of a window and take a screenshot of the highlighted portion, or perhaps to edit a shot of a whole window after taking it ?...

Henri

---

### Post by H3g3m0n on 2007-06-15
In gimp
File>Aquire>Screen shot

choose "a single window".

Click "Grab", Then click on the window.

Then choose the selection tool (or press 'r' key).

Drag around the area you want.

Then from the menu (The menu on window with the image, not the initial menu on gimps toolbar):

Image>Crop

Then just File>Save

---

### Post by Maulwuff on 2007-06-15
what about taking screenshots from menus? Neither Gimp nor the gnome-screenshot tool works. Is there a way to screenshot directly to the clipboard?

---

### Post by mhenriday on 2007-06-15
Thanks, **H3g3m0n** ! By playing around with **Gimp** and clicking all the alternatives, I had in fact managed  to figure out how to take a screenshot, but your tip on how to crop the image was certainly very valuable. But when I've saved the image to desktop or to my homefolder, how can I, for example, insert it into an email or a message on this thread ? When I try to copy it by right-clicking the thumbnail on my folder and then choosing «copy», instead of obtaining a screenshot when I attempt to paste it in here, I get the following string, which can't be opened :  **/home/mhenriday/Testbild20070616.xcf**. Thus my screenshot doesn't do me much good, if I wish to show someone else what I've been doing. How do I get 'round this problem ?...

Henri

---

### Post by RedSquirrel on 2007-06-15
> **mhenriday said:**
> Thanks, **H3g3m0n** ! By playing around with **Gimp** and clicking all the alternatives, I had in fact managed  to figure out how to take a screenshot, but your tip on how to crop the image was certainly very valuable. But when I've saved the image to desktop or to my homefolder, how can I, for example, insert it into an email or a message on this thread ? When I try to copy it by right-clicking the thumbnail on my folder and then choosing «copy», instead of obtaining a screenshot when I attempt to paste it in here, I get the following string, which can't be opened :  **/home/mhenriday/Testbild20070616.xcf**. Thus my screenshot doesn't do me much good, if I wish to show someone else what I've been doing. How do I get 'round this problem ?...

Henri

You need to _attach_ your screenshot to your message. 

In your email program, there will be something about "Attachments". If you have a toolbar, the Attachments icon is usually a paperclip.

The same thing applies to these forums. When you compose your message, there is a paperclip icon in the toolbar. Click on that and it will open a separate window that will allow you to attach your screenshot. 

Imagemagick is another neat tool for taking screenshots.

```
sudo apt-get install imagemagick
```once it's installed, you can run

```
import -help
```to see all of the options.

You simply do

```
import filename.jpg
```and it will turn your mouse cursor into a crosshair and you can click-and-drag whatever portion of the screen you want to save.

See also:

```
man import
```

---

### Post by H3g3m0n on 2007-06-16
Unfortunatly the Linux clipboard doesn't seem to allow for anything other than plain text in the clipboard, no formatting or images. GIMP and OpenOffice have their own clipboards to work around that, unfortunatly that means you cannot copy from one to another, at least anything other than plain text.

So you need to open the image in the other program you are using. Forums and emails will always need the image to be 'attached' reguardless of the operating system.

You also shouldn't save GIMP images to a XCF if you want to upload them, a XCF is a much bigger image and isn't supported by browsers, save as a jpeg instead.

---

### Post by mhenriday on 2007-06-16
Thanks **H3g3m0n** and **RedSquirrel** ; with your help perhaps I'll be able to master screenshots in **Feisty** after all ! This would be of great help to me, as I often have occasion to help retired people with their computer problems, and being able to send screenshots when one has to explain a complicated procedure is invaluable. The only problem is that these retirees almost universally use the legacy system, but I suspect the knowledge I gain in **Feisty** can be translated, *mutatis mutandi*, into **Windows** as well. In any event, again, much thanks !...

Henri

---

### Post by RedSquirrel on 2007-06-16
Glad to help. :)

The "import" command I gave in my earlier post is just the tip of the iceberg. You can do all sorts of things with imagemagick. 

Here are the commands I have assigned to keyboard shortcuts:

Take a shot of the whole screen in 7 seconds:
```
import -pause 7 -window root ~/misc/screenshots/screenshot-`date +%Y-%m-%d_%T`.jpg

```Allow me to click on a window to take a screenshot of it, including its frame (titlebar etc.):
```
import -frame ~/misc/screenshots/window-`date +%Y-%m-%d_%T`.jpg
```You can also change the resulting file type just by changing the filename suffix, e.g., for PNG:
```
import -frame ~/misc/screenshots/window-`date +%Y-%m-%d_%T`.png
```Have fun! :D

---

### Post by mhenriday on 2007-06-22
Thanks again for the info, **H3g3m0n** and **RedSquirrel** ! By following your instructions I did manage to add a thumbnail image to my earlier posting entitled *[Partition blues]("http://ubuntuforums.org/editpost.php?do=updatepost&p=2844146")*. I should like to have inserted the image _directly_ into the text in place of the summary I constructed by hand, as it would certainly have been more eye-catching and might hopefully have inspired someone to point me to a good partitioning tutorial which would solve my problem. But as **H3g3m0n** points out, it seems that it is not possible to do so using the **Linux** clipboard. So can it go ! Perhaps some kind soul will click on the thumbnail anyway and decide to give me a heads-up....

In any event, thanks a lot - I very much appreciate your help in teaching me to use the screenshot feature !...

Henri

---

### Post by Bartender on 2007-06-22
In Gimp for Windows, the GIMP help files are a separate download.  I wonder if the Ubuntu GIMP is the same?
Take a look at the Feisty GIMP packages.  package-gimp-help-en is listed separately from GIMP.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gimp+&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gimp+&searchon=names&subword=1&version=feisty&release=all)

---

### Post by mhenriday on 2007-06-27
Another query : I'm sure we've all seen those nifty screenshots of installations, i e, of **Feisty**, that are sometimes published in conjunction with articles online or in print ; are these taken with cameras and special apparatus, or is it possible to do them from within the same computer on which the installation is being performed ? For example, I should very much like to be able to take screenshots both of installation procedures for **Ubuntu** and **Windows**, as well as of **GRUB** during the booting process, as this would be of great help in creating double-boots tutorials for less experienced computer users who are interested in trying out **Ubuntu**. Possible without additional apparatus ?...

Henri

---

### Post by H3g3m0n on 2007-06-27
I think those are normally done by taking screenshots of virtual environments such as vmware, virtualbox, qemu, xen etc... rather than on actual physical systems.

---

