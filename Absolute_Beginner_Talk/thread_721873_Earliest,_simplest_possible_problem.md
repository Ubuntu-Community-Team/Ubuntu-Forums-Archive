---
title: "Earliest, simplest possible problem"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by aprilia on 2008-03-11
Hi all, I am hugely frustrated with myself because I cannot overcome the simplest possible problem.

I have downloaded ubuntu, burnt it to disks a couple of times just to try, but NEVER has it shown as an iso cd image. I'm on XP on a decent acer laptop - there should be no issue, But after downloading and extracting the rar, all I have is a folder, NOT an iso image. I have, as I've said, burnt it a couple of times experimenting with a few different ways, but my pc will NOT boot from any of  the cds. I (think I have) tried everything on the ubuntu website help.

I have ensured that I am not just putting the whole folder onto the disc, I've tried opening the folder and then copying the contents by selecting all and burning, I have tried many things but I definitely do not have an ISO image and I definitely do not have a bootable cd. Even if I try installing a spare, fresh formatted hard drive to ensure windows doesn't jump the gun on my bios settings (which I have set to prioritise booting from the cd).

I haven't even managed to get started installing ubuntu. I am not a complete novice but not an advanced computer user. Why is it so hard at this stage and does anyone have any advice? Highly dispirited, but strongly in favour of linux.

Thanks in advance.

---

### Post by JoshuaRL on 2008-03-11
Your problem might be with Nero (or whatever CD burning app you use).  I've heard some other problems like this.

Don't extract it.  It isn't a rar, its a full ISO.  Just make sure you burn as an image at the lowest speed possible.  That should fix it for you.

And welcome to Ubuntu!

---

### Post by Chris555 on 2008-03-11
If you downloaded a valid .iso image, there is a tool you can install in XP that will give you right click context menu to burn iso without using nero. I found it to be a better easier tool to use than to try to sort though Nero. 
Here is the link   [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

just make sure you match the correct version of isorecorder to your version of XP.

hope this helps out

---

### Post by bumanie on 2008-03-11
May be you should go to the canonical site and download through there. That way you can be sure (save for any download errors) that you will get the correct .iso you are after. They may exist everywhere, I guess, but I have never personally seen an ubuntu .iso compressed into a .rar file. I would go to where you can download a straight out .iso

---

### Post by ejb331 on 2008-03-11
I agree with the other replies. After you download the file from ubuntu.com all you need to do is burn it to a CD. You do not need to extract it or anything, it is already a .iso file. Nero will get the job done or there are plenty of other programs to burn an .iso in Windows.

If you still aren't sure or want a quick how-to, check out this link.
[http://wlmtips.com/2008/03/03/how-to-burn-an-iso-file-in-windows-xp/]("http://wlmtips.com/2008/03/03/how-to-burn-an-iso-file-in-windows-xp/")

---

### Post by frimilden on 2008-03-11
This is a common mistake that is made when installing winrar, people check off the box that says have winrar handle them. As said before it is most likely an iso and not a rar file.

---

### Post by JoshuaRL on 2008-03-11
Winrar, that's the problem.  I forgot the name of the application.  Nero uses winrar for rars.

---

### Post by aprilia on 2008-03-12
Cool. Thanks for that everyone, will try it tonight. It's so frustrating to take as much care as possible with the intial setup only to be knocked off course at the first step. I haven't had this problem before with other rar files but I guess a new OS is different. I'll adjust winrar. Hang on there's no point as I won't be needing it again on this particular XP setup ;).

Nice to get some first hand experience of the forum working in accord with its reputation - I posted just before I went to bed and your 6 replies were all there as soon as I got to the office this morning :)

I'll update once I've (hopefully) made progress. Thanks again.

---

### Post by jan quark on 2008-03-12
I hope you manage to burn your CD at this time
if not check this guide:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by lucasl on 2008-03-12
FYI, the main reason (as far as I know) that simply burning the extracted folder to a CD doesn't work is because the ISO contains info that will make the CD bootable. This info is lost when extracted.

---

### Post by aprilia on 2008-03-13
I now have a cd that will boot, but it stalls at the main menu. If I select "check disc" and even leave the pc for 20 minutes, it still does not compete the task - the cd drive stops within two minutes and never starts up again.

I'm now trying to download it at work but all the mirrors are slow (shouldn't really be doing it u know ;)). 

So next thing I guess is for me to be extra careful with the burning method and then go and learn something about hashes. I'll be back.... this is not proving to be easy. But at least its my existing system causing the problem, not the linux stuff.

---

### Post by gwarguy on 2008-03-13
I too made this mistake when starting up. I solved it by using a different burn method. I went and downloaded the Ubuntu ISO off the offical page. Once the iso was downloaded I went and got Alcohol 120% (assuming your using windows to try and setup linux like I was) This is a pay for use program, but allows a trial period with enough options to accomplish what you need to do.  When alcohol starts up, make sure you click the correct option. You want to use the "Image Burning Wizard"

This is bring up a new window and ask you to select your image. Hit the browse button and then select the ubuntu-7.10-desktop.i386.iso or whatever version you downloaded for your computer type.  

The first time i used fireburner and it just copied the .iso to the cd, and did not mount the actual image. Using the above process will mount the image as a useable, bootable cd. Make sure you burn on the slowest speed, and you dont have any other programs up and running. 


On a side note, I could not get ubuntu-7.10.desktop.i386.iso to work. It continued to crash and lock up during the installation. I then tried the ubuntu-7.10-alternate.i386.iso and used the above mounting method and it installed flawlessly. 

Hope this helps some!

---

### Post by dorkdork777 on 2008-03-13
Try burning it at a lower speed. Most decent image burning software will have an option to burn the image at a speed like 4x or 8x. If your software does not have this option, consider downloading ImgBurn - it's a great free image burner.

---

### Post by arekkusu on 2008-03-13
ImgBurn is a free burning app for Windows that will do the job. (no need for Alcohol 120%...)

[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by which_chick on 2008-03-18
If your laptop is not happy with the Live CD install after you've tried it twice, it might be worth a try to attempt the "alternate install"  version.  

I used the "alternate install" CD successfully on my laptop (Dell Inspiron) after I got several black-screen-deaths trying to use a carefully burned Live CD that passed the error-check process on the first screen.  The "alternate install" CD isn't terribly difficult or technical and it got me up and running when the usual "Live CD" would not.

---

