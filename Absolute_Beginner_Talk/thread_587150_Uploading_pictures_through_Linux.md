---
title: "Uploading pictures through Linux"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Lost_Linux_User on 2007-10-22
I am new to Ubuntu.  I am more used to Windows.  Anyway, I plugged in my camera to the computer but I have no idea where the pictures are uploaded.  Can anyone help me with that and explain to me exactly where I need to go.

---

### Post by yabbies on 2007-10-22
depending on what version of ubuntu you are using
and if they uploaded properly they will be in your home folder

goto places>home

there will be a folder made with the date of the transfer
your pictures will be in that folder

---

### Post by Lost_Linux_User on 2007-10-22
Watsup man, thanks for replying so fast.  Well I just tried it again.  I plugged my camera in the USB and checked the home folder and they werent there.  In Windows, once I plug in the camera the pics will upload into the PC by itself in a folder with the date, like you described.  I have no idea how I do that in Linnux.  I'm not sure what version of Ubuntu this is but I'm pretty sure it's one of the newer versions.  Do I have to manually upload the pics myself?  I don't know where I'd go to do that.

---

### Post by scapalexis888 on 2007-10-22
For me, I prefer drag and drop. Invest in a media card reader and just stick the card in. Ubuntu automatically mounts the card and behold all your pictures are there. Then you can drag it anywhere you want. Eliminates the need for different usb cables for different cameras and you don't need to upload the photos through a camera (which I find annoying because you need a full battery or the AC adapter)

---

### Post by evilregis on 2007-10-22
It's the camera's software that is doing that uploading for you.  You may need to do this manually now... I'm not sure as I don't have a camera to hook up and see for myself.

When you connect the camera does an icon for the camera appear on your desktop?

---

### Post by Lord_Dicranius on 2007-10-22
Did an application open that you actually clicked a button to upload them to your machine?  If you're using Ubuntu 7.10, the default location that application (can't remember what it's called haha) is /home/Pictures/[date].  If you didn't actually click on anything to upload them to your machine, then more than likely they weren't transferred (unless of course you setup a script to do it automagically, but it doesn't sound like you've done that heh).

---

### Post by Lost_Linux_User on 2007-10-22
> **scapalexis888 said:**
> For me, I prefer drag and drop. Invest in a media card reader and just stick the card in. Ubuntu automatically mounts the card and behold all your pictures are there. Then you can drag it anywhere you want. Eliminates the need for different usb cables for different cameras and you don't need to upload the photos through a camera (which I find annoying because you need a full battery or the AC adapter)

I don't think I need a card reader to upload my pics though, do i?  I hope not.  In Windows I never needed that.  

After I plug my camera in the USB port, where can I find the folder for the camera.

For example, in Windows it would be in MY COMPUTER and I could browse the folders.  On this, it's totally different and I can't find it.

---

### Post by Lord_Dicranius on 2007-10-22
> **Lost_Linux_User said:**
> I don't think I need a card reader to upload my pics though, do i?  I hope not.  In Windows I never needed that.  

After I plug my camera in the USB port, where can I find the folder for the camera.

For example, in Windows it would be in MY COMPUTER and I could browse the folders.  On this, it's totally different and I can't find it.
If you click on Places at the top, if the camera mounted you should see a folder there (somewhere around the Computer listing in the middle of the menu) called something like "disk" or "camera" or even your cameras model.

---

### Post by Lost_Linux_User on 2007-10-22
> **Lord_Dicranius said:**
> Did an application open that you actually clicked a button to upload them to your machine?  If you're using Ubuntu 7.10, the default location that application (can't remember what it's called haha) is /home/Pictures/[date].  If you didn't actually click on anything to upload them to your machine, then more than likely they weren't transferred (unless of course you setup a script to do it automagically, but it doesn't sound like you've done that heh).

Nope nothing opened up for me to upload them.  On Windows (sorry I keep saying that) after I plug in my camera it will automatically recognize it and a little pop up appears at the lower right corner of the screen saying "USB CAMERA" or something of that nature.  

On Linnux, after I plug in my camera there is no note or anything that comes up so I'm guessing I have to search for the pics myself in some folder but I can't find them.

---

### Post by yabbies on 2007-10-22
once you plug the usb into your computer ubuntu should  see your camera and ask you if you want to transfer the pictures. No different than windows, except you don't need special software.
what kind of camera are you using?

---

### Post by Skrynesaver on 2007-10-22
When you plug in the camera, does a window pop up recognizing it as a camera? or as a USB storage device?.
You may have to tell it the first time which program to use for cameras.  If you have the standard install the available option is F-spot which can be found under 
Applications>Graphics>F-Spot, when you run this go to 
File > Import and select your camera in the drop down.
DigiKam is also quite a nice photo management application, (I used KDE for a long time before Ubuntu and I'm used to it).
Here yo select your camera from the main menu.

---

### Post by Lost_Linux_User on 2007-10-22
> **yabbies said:**
> once you plug the usb into your computer ubuntu should  see your camera and ask you if you want to transfer the pictures. No different than windows, except you don't need special software.
what kind of camera are you using?


It's called Kodak Easy Share.  What you are describing is what would happen in windows.  Maybe this camera doesn't work with Linnux or something.  I don't know.  I tried unplugging the USB cable and plugging it back in but no message ever came up asking me to transfer the pics.  

I don't know what the problem is.  It's very frustrating.  :mad:

---

### Post by Lost_Linux_User on 2007-10-22
> **Skrynesaver said:**
> When you plug in the camera, does a window pop up recognizing it as a camera? or as a USB storage device?.
You may have to tell it the first time which program to use for cameras.  If you have the standard install the available option is F-spot which can be found under 
Applications>Graphics>F-Spot, when you run this go to 
File > Import and select your camera in the drop down.
DigiKam is also quite a nice photo management application, (I used KDE for a long time before Ubuntu and I'm used to it).
Here yo select your camera from the main menu.

I went into Graphics but I didn't find anything called F-Spot.

Would it make any difference if I'm in a Guest account?  There are two accounts on this PC.  The main user, and Guest.

---

### Post by yabbies on 2007-10-22
try skrynesaver's advice
I have a kodak at home that works, been awhile since I had to set it up.
is your usb posrt working proeperly?
try a differnt port.

also go to System>about ubuntu and let us know what version you are using

thanks

---

### Post by Lost_Linux_User on 2007-10-22
I also did a search for "Kodak" in the SEARCH FILES option thing they have and still nothing.

---

### Post by Lord_Dicranius on 2007-10-22
> Would it make any difference if I'm in a Guest account?
That definitely could be it.  The Guest account probably has limited to access to applications and might not be able to mount USB devices.  If you have a thumb drive or any other USB device, does that show up when you plug it in?

---

### Post by nchase on 2007-10-22
go to main menu > preferences > removable drives and media

go to cameras tab

is "import digital photographs when connected" checked? if so, is the command listed as ```
gnome-volume-manager-gthumb %h
``` ?

---

### Post by Lost_Linux_User on 2007-10-22
Thanks for your help guys but I give up.  I tried all the suggestions you guys gave me and still couldn't find the pictures.

 I just don't understand this operating system.

---

### Post by Lord_Dicranius on 2007-10-22
I think I'm going crazy.  I could've sworn there were some other replies here...

**EDIT**
Yep, I was thinking of another thread lol

I wish I could be of more help, but I'm sitting in front of my WindowsXP box at work :(

---

### Post by nchase on 2007-10-22
There could be many different things causing this. I'm sorry none of the solutions proposed thus far have worked.

I'm sure this is a far cry, but have you tried using Google to search for your camera's exact model combined with terms like linux or ubuntu to see if anyone else is having the same/similar issue?

---

### Post by Lost_Linux_User on 2007-10-22
Nah just forget it.  I don't have the energy to try and figure this out anymore.  I've been doing that for the past hour and it's driving me insane so I give up.  I'm just too used to Windows to ever get used to Ubunto.

---

### Post by yabbies on 2007-10-22
don't get stressed
I was the same way when I first switched to Ubuntu
it's tough switching from windows all your life to a different OS
but once you are patient and give a willingness to learn then you find out
what a great OS ubuntu is. 

don't give up. and check 
that your user has the correct privileges:

         Navigate to "System" > "Administration" > "User and Groups"
   
      Choose the user, click on "Properties"
   
      Go to the "User Privileges" tab

You should have the "Access external storage devices automatically" option checked.

---

### Post by MSchlemski on 2007-11-04
Hey yabbies can you help me with a similar problem? I'm trying to upload photos from a Canoon Power Shot SD200 and keep getting this message:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I know nothing about Ubuntu.

thanks.

---

