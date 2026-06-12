---
title: "A Prettier rEFIt"
date: 2008-07-29
forum: Apple Hardware Users
---

### Post by simplebeep on 2008-07-29
For those of you doing a dual-boot of Ubuntu and OS X (and are already using [rEFIt]("http://refit.sourceforge.net/"), which I would strongly recommend), I have put together a set of changes you can make to the rEFIt conf and icons, to make the interface better-looking and more Mac-like.

[ATTACH]79401[/ATTACH]

Put those files in their locations, as indicated by the folder hierarchy.  DO NOT REPLACE THE EFI FOLDER ENTIRELY!  Simply pull the files out of the archive and insert them in their respective folders.  Note that you might want to rename the old icons before inserting, to avoid losing them to replacing, if you wish to go back.

Then, modify the refit.conf file.  Here's what I did:
[LIST]
[*]Under the line that says "#disable all", I put **disable tools** (no #) to get a simpler interface.  This removes the row of small icons below the boot options.
[*]I removed the "#"s from the lines beginning with "selection_big" and "selection_small".  Note that the icons have underscores _ instead of hyphens - in their names, so be sure to change the hyphens to underscores in the conf file.
[*]I also removed the "#" in front of **hidebadges internal**.  That will remove some extra clutter.
[*]Under "#hideui all", I entered **hideui banner label funcs** to remove even more clutter.
[/LIST]

You can leave some of the lower icons enabled, if you wish.  I haven't created any icons for these or for Windows (as I don't use them), but you can sample the colours from the other icons and create your own, perhaps.  If you do create icons, I'd love for you to post them here.  Just be sure to put them in a Zip file, so they don't get [J-Pegged]("http://en.wikipedia.org/wiki/Jpeg#Sample_photographs").

I'll post a screenshot of this setup soon.

---

### Post by cyberdork33 on 2008-07-29
I made an Ubuntu Icon awhile ago... I will if I can find it.

---

### Post by Clouseau__ on 2008-08-03
Thanks a lot for your post ... I had read refit's documentation on how to do this but you just saved me a lot of time, and your icons are great!

Clouseau__

---

### Post by simplebeep on 2008-08-03
Well, I don't know how to take a screenshot of the boot menu.  I know it's possible, but to save myself time, I just created this mockup of what it looks like.  Although not exact, it will give you a pretty good idea of what my modifications do.

[ATTACH]80052[/ATTACH]
[SIZE="1"]Click for a bigger version.[/SIZE]

Oh, and thank you, Clouseau__ for your feedback.

---

### Post by lael on 2009-05-05
Thank you for sharing your experiences with rEFIt.  I like your theme.

I just blogged about one that I came up with: [http://colinharrington.net/blog/index.php/2009/05/05/customizing-refit-an-efi-bootloader-intel-macs-slick/]("http://colinharrington.net/blog/index.php/2009/05/05/customizing-refit-an-efi-bootloader-intel-macs-slick/")  It contains all the resources that you need to do recreate it.

[IMG]http://www.colinharrington.net/images/refit-screen-500px.png[/IMG]

Closeup:
[IMG]http://www.colinharrington.net/images/refit-choices.png[/IMG]

I really didn't like the apple grey/silver.  Let me know if you find a way to get rid of it on the boot_linux screen after you select your OS.

I also put together an [ubuntu icon]("http://colinharrington.net/blog/index.php/2009/05/03/ubuntu-logo/") for the [boot_linux.icns]("http://www.colinharrington.net/images/boot_linux.icns") icon
[IMG]http://www.colinharrington.net/images/ubuntu-logo-transparent-shiney-128.png[/IMG]

---

### Post by inphektion on 2009-05-06
Nice guys this is great.  I definitley like black better too.

---

### Post by inphektion on 2009-05-06
I followed your post and have replaced the icons but the screen is still silver/gray not like your shot where it is black.  you mentioned hostname.bmp sets the background with the top left pixel...

I created a hostname.bmp but it doesn't seem to be used, I did set it in the .conf file.  does that bitmap have to be a certain size?  I just arbitratily picked 190x90

---

### Post by cyberdork33 on 2009-05-06
> **inphektion said:**
> I followed your post and have replaced the icons but the screen is still silver/gray not like your shot where it is black.  you mentioned hostname.bmp sets the background with the top left pixel...

I created a hostname.bmp but it doesn't seem to be used, I did set it in the .conf file.  does that bitmap have to be a certain size?  I just arbitratily picked 190x90
did you set the option in the refit.conf?

---

### Post by inphektion on 2009-05-06
yes I did.  what I didn't do was read the instructions carefully.  hostname.bmp doesn't go in the icons folder with the other stuff.  it goes up a directory.  all good now

---

### Post by simplebeep on 2009-05-07
Yes, that black interface is slick! :)  I think it fits better with the Ubuntu loading screen. Personally, I am a Mac person as much as I am a Linux person, so I like the flat grey theme which blends with the normal Macintosh startup.
Whatever floats your boat!

---

### Post by Joushou on 2009-05-07
Nice theme... The grey in the background of boot_linux.icns is a bit off though... Can't the background be transparent on that?
Now you just need to theme the rest of refit, so we can have pretty utilities aswell ;)

---

### Post by iovis9 on 2009-05-09
The grey one looks very nice. Great work man.

---

### Post by timxirish on 2009-05-10
In regards to both of the themes shared, very cool. I'm typing this from my macbook right now, and will definitely give them a shot.

---

### Post by gorn on 2009-09-05
Inspired by the gray theme I added did a tux (As I'm not running Ubuntu) and the tools.

Screenshot is attached, as is the theme files.

(To take a screenshot, hit F10, then you can find the file named screenshot.bmp in your EFI System Partition, to mount the EFI System Partition do ```
mount -t msdos /dev/disk0s1 /where/to/mount
``` or the equivalent in linux.)

---

### Post by phawnex on 2010-01-04
i know this is a rather old post but could anyone tell me almost word for word how to make the background all black. i was able to take all of the cursors off (aside of the apple and i customized just a regular picture of tux. ) only thing i want to do now is put in the black background. 

thanks.

---

### Post by simplebeep on 2010-01-04
Here's how to make the background black:

**1.** Download this image: **_[ATTACH]142492[/ATTACH]_**. Unzip it and place it in the same folder as *refit.efi*. This image's upper-left pixel is totally black, which, when placed next to *refit.efi*, tells rEFIt to make the whole background black.

**2.** Open *refit.conf*, and remove the **#** at the beginning of the line that says "banner hostname.bmp" and save the file. This tells rEFIt to look for and reference the image.

That should do it!

---

### Post by phawnex on 2010-01-04
thanks a lot! it worked. i accidentally had the banner hidden and it took me a good 15 mins to get that figured out lol

thanks alot. it works now.

cheers

1

---

### Post by pencilcheck on 2010-01-10
Hi guys, like the theme and stuff.

I have a problem with the selection bitmap. For some reason the bmp I downloaded from the link works but if I change it and save with photoshop or whatever image manipulate program, it won't work anymore even with the same name same place.

It seems like rEFIt requires a special bitmap I assume, can anyone tell me how you save and edit the selection image on a mac?

---

### Post by tommytee on 2010-04-20
my mistake...

---

### Post by mattakafred on 2010-05-06
Hey, I'm running rEFIt on my MBP and I am having issues getting the banner to work out right. It seems if the image size gets too large rEFIt seems to discard the icons and subsequently make it impossible to select a partition. Anyone know what size constraints there are?

---

### Post by boarder4021 on 2010-05-06
I apologize for being so noobish - but where exactly do I place the files? Where is the refit folder located (is it on my Macintosh HD filedrive)? 

A step-by-step guide would be greatly helpful!

---

### Post by mattakafred on 2010-05-07
default location is \efi\

Just open your Macintosh HD, and open the folder efi.

Banners and selection indicators go in the subfolder efi\refit
Icons go in efi\refit\icons and their names must match their function (the icon for selecting the OS X partition must be titled os_mac.icns).
You must configure the refit.conf file to recognize what image you want as your banner (unless you want the default "refit" logo on top, but I don't know why you would) and the banner must be .bmp

As far as I can tell the banner height cannot be much more than 1/4 the height of your monitor (on 1440x900, a 1440x300 size banner is too large, 1440x200 seems to work) 


Now my turn. Anyone know how to do a screen shot? Someone earlier said it's as easy as pressing F10, but that doesn't seem to be working.

Note: I'm running a MBP efi is on my OS X partition

Edit: Attached is a mockup of what I made (using some of the icons from lael, and misc other things), but I wanna be able to take an actual screen grab

---

### Post by lael on 2010-05-07
@mattakafred Looks good! What Apple logo is that? Where can I find that one?

---

### Post by 311005901 on 2010-05-10
Make this! This would be amazing!!

---

### Post by ranger53 on 2010-05-11
> **lael said:**
> @mattakafred Looks good! What Apple logo is that? Where can I find that one?

Save attached apple pic to your desktop. Use an app such as the free version of Img2icns and convert it to an icon by dragging it to the app. Rename it os_mac.icns and replace the one in your refit icons folder.Next time you restart the green apple will show.

---

### Post by newbie80 on 2010-05-11
Firstly thanks for the instructions posted, I was able to customize the refit boot many to what I like following the instructions posted. I am triple booting using refit, I have couple of issues (sorry for posting them here if they are not relevant) 1) It takes a long time on my MBP 6,2 to get to the refit boot menu (about 30 seconds) is there any way I can quicken this process and 2) When I select windows in the refit menu it boots to ubuntu grub - from there I have to select windows 7 to boot into windows, is there any way I can directly boot into windows 7. Thanks for your answers and once again sorry if I posted in the wrong thread.

---

### Post by tmaspoopdek on 2010-05-23
I really like the grey one with the ubuntu logo and the rEFIt interface on the other grey one. The only issue is windows. I run windows only for games, but I don't want it ruining an otherwise awesome rEFIt setup. Can someone make a grey icon for windows?

---

### Post by tmaspoopdek on 2010-05-23
Nevermind, I just found the windows icon. Great themes, all of them!

---

### Post by raprap30 on 2010-05-29
> **tmaspoopdek said:**
> Nevermind, I just found the windows icon. Great themes, all of them!

Where did you get it?

---

### Post by raprap30 on 2010-05-29
Okay, just done a monochrome version of the Windows logo. To be specific, a monochrome boot camp icon. Mind if I do a repack with the Windows icon+ the optimized refit.conf? And by the way, I also need your help with aligning the stuff. Thanks. 

And here's my final product, boot camp logo is fully monochrome :D : 

[IMG]http://desmond.yfrog.com/Himg441/scaled.php?tn=0&server=441&filename=46e.png&xsize=640&ysize=640[/IMG]

---

### Post by bkadoctaj on 2010-05-30
To all those of you having trouble getting the banner set up (particularly the all black background), make sure that your hideui section doesn't include "banner".

So this is a no-no:
hideui banner

The .conf file is somewhat misleading as it says you'll be hiding the rEFIt banner but it actually hides whatever banner one chooses, default or otherwise.

Hope this helps.  :)  Took me months to figure that out haha.

---

### Post by raprap30 on 2010-05-31
To the OP: Mind if I fork your theme? I have already created more icons for Windows + more distros:

[IMG]http://desmond.yfrog.com/Himg135/scaled.php?tn=0&server=135&filename=cud.jpg&xsize=640&ysize=640[/IMG]

---

### Post by nickotinebck on 2010-06-07
Can anyone post the grey monochrome icons for download?
I'm a total noob at image editing.
Thanks

---

### Post by ryankiefer on 2010-06-24
I've been working on a custom banner for refit, but I can't get the default Mac boot background color quite right. Color picker for Mac is just not giving me an exact color, and I end up with a boot screen that's slightly darker than the screens before/after it. Does anyone know the exact RGB color of that backdrop? Thanks.

---

### Post by Zookalicious on 2010-07-03
I thought this was nice :) Using the Somatic Icons for fun (and to confuse people who try to turn my computer on). I'm glad to see that I'm not the only person in the community interested in making the rEFIt menu nicer :P

btw just for the record I took a screenshot by pressing F10 at the menu (hold down the function key if you need to). I pressed the button about a million times, actually I pressed all of the function buttons just to be sure. Maybe not a good idea but nothing bad happened. 

Then just as previously described in this thread:
```

sudo mount -t msdos /dev/disk0s1 /filepath/for/mounting

```

I still need a banner though. My fiancee said that she would whip one up for me that says "Choose Your Weapon" so I'll update when I get that.

---

### Post by fatppl on 2010-08-20
I have a slight problem:

Everything is working, however, two of my boot icons are the same:

1)MacOSX from internal HD 

2)MacOSX from external HD 

How can i distinguish the icons for these two boot options... 

and yes i realize because they are both macosx this is why they both share the same icon - but is there any way I can distinguish the two?

---

### Post by kennethsime on 2010-08-21
So right now I have the nifty monochrome icons in place and all the other crap hidden, and I'm loving it. However I'm trying to add a custom banner so that I can have a text message above the icons. This is possible, correct?

I created a 16-bit bmp at 1280x200 (1/4 of my 1280x800 screen), placed it in the rEFIt folder along with rEFIt.conf. It's named banner hostname.bmp . Is this correct? Or am I supposed to rename it to my hostname? If this is the case, where do I find my hostname? (I believe it is just Kenneth's MacBook Pro).

The banner will not show up. Is it obvious what I'm doing wrong? Step-by-step, how do I get this to work?

Any help would be much appreciated.

Also, I've been trying to fix a problem with rEFIt being slow to come up, taking sometimes 20 seconds to show up after startup. If you would take a look at the thread, I would greatly appreciate it: [http://ubuntuforums.org/showthread.php?t=1556993](http://ubuntuforums.org/showthread.php?t=1556993)

---

### Post by szymciolop on 2010-08-31
This is modded version of lael's rEFIt.

---

### Post by drexvil on 2010-09-07
> **raprap30 said:**
> Okay, just done a monochrome version of the Windows logo. To be specific, a monochrome boot camp icon. Mind if I do a repack with the Windows icon+ the optimized refit.conf? And by the way, I also need your help with aligning the stuff. Thanks. 

And here's my final product, boot camp logo is fully monochrome :D : 

[IMG]http://desmond.yfrog.com/Himg441/scaled.php?tn=0&server=441&filename=46e.png&xsize=640&ysize=640[/IMG]


Can you post the icons and banner files? Thanks.

---

### Post by dngfng on 2010-09-07
> **Zookalicious said:**
> I still need a banner though. My fiancee said that she would whip one up for me that says "Choose Your Weapon" so I'll update when I get that.

Has that banner been created by any chance?

---

### Post by stefanwa on 2010-10-28
> **raprap30 said:**
> Okay, just done a monochrome version of the Windows logo. To be specific, a monochrome boot camp icon. Mind if I do a repack with the Windows icon+ the optimized refit.conf? And by the way, I also need your help with aligning the stuff. Thanks. 

And here's my final product, boot camp logo is fully monochrome :D : 

[IMG]http://desmond.yfrog.com/Himg441/scaled.php?tn=0&server=441&filename=46e.png&xsize=640&ysize=640[/IMG]

Hi!

Could you upload your theme somewhere? It's exactly what I searched for...great work! Thanks

---

### Post by qubert on 2010-11-03
Can some one please share those icons please please

---

### Post by mspritch on 2010-11-04
For those struggling to get hostname.bmp files recognised, try this:-

Boot into Windows
Open the hostname.bmp in Paint (in a Bootcamped setup you should be able to read this from your Macintosh HD partition)
Save As, save a copy on your Windows desktop
Boot back into MacOS or whatever
Copy the new hostname.bmp back to your \efi\refit folder

This worked for me, using a 256x40, 24-bit bitmap.  Even though there's not much difference between a Paintbrush BMP and an MSPaint BMP, it seems to be enough.

---

### Post by mspritch on 2010-11-04
> **Zookalicious said:**
> I still need a banner though. My fiancee said that she would whip one up for me that says "Choose Your Weapon" so I'll update when I get that.

rEFIt feature request: MP3 theme tune support to go with the above banner :)

---

### Post by MrNago on 2010-12-25
> **mspritch said:**
> For those struggling to get hostname.bmp files recognised, try this:-

Boot into Windows
Open the hostname.bmp in Paint (in a Bootcamped setup you should be able to read this from your Macintosh HD partition)
Save As, save a copy on your Windows desktop
Boot back into MacOS or whatever
Copy the new hostname.bmp back to your \efi\refit folder

This worked for me, using a 256x40, 24-bit bitmap.  Even though there's not much difference between a Paintbrush BMP and an MSPaint BMP, it seems to be enough.

Same here, you have to use Microsoft Paint! For some reason...
No way i coould get it to work with PaintBrush/Photoshop.
I went even simplier. Small **monochrome** (1 bit) bmp.

---

### Post by lamalex on 2010-12-25
This is beautiful!! I have been searching for that monochrome apple logo for 30 minutes, and now I find a beautiful selection and circle of friends image. Merry christmas to me.

---

### Post by wersdaluv on 2011-01-03
> **raprap30 said:**
> To the OP: Mind if I fork your theme? I have already created more icons for Windows + more distros:

[IMG]http://desmond.yfrog.com/Himg135/scaled.php?tn=0&server=135&filename=cud.jpg&xsize=640&ysize=640[/IMG]
You can find raprap30's icons here [http://cl.ly/1y2B3P3806212H2u2R06](http://cl.ly/1y2B3P3806212H2u2R06)

---

### Post by mikev63 on 2011-01-12
Hi all, 
This has been an incredibly helpful thread. Thank you to everyone here for sharing your ideas. I have one question, does anyone know how to add text to the background/hostname.bmp? ...i have been able to edit everything else and i am using a solid black background. I understand that the background color is set with the top left pixel of the .bmp file but there must be a way to add text.  Anyone got any ideas?

Thanks in advance!

---

### Post by benjihall on 2011-02-01
...

---

### Post by rezzo on 2011-04-11
Nice work!

---

### Post by Raditude on 2011-06-26
Sorry to bump, but I was wondering if I could make a request. I used to use a Hackintosh with the Chameleon bootloader. I now have a MacBook Pro, and plan to use Refit to Triple Boot Ubuntu, OSX and Windoze.

Chameleon had a [theme based on the "I'm a Mac, I'm a PC" commercials]("http://forum.voodooprojects.org/index.php/topic,451.0.html"). I have downloaded that and uploaded the images here. I was wondering if someone would be able to make a similar theme for refit. I have been unable to find a good tutorial on how to do it.

[IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Blackosx_Mactico_Im_a_Mac.jpg[/IMG]

[IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_hfsplus.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_ntfs.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_ext3.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_selection.png[/IMG]


Another option would include Steve Jobs and Bill Gates:

[IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Steve.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Bill.png[/IMG]

---

### Post by joey-elijah on 2011-06-27
> **Raditude said:**
> Sorry to bump, but I was wondering if I could make a request. I used to use a Hackintosh with the Chameleon bootloader. I now have a MacBook Pro, and plan to use Refit to Triple Boot Ubuntu, OSX and Windoze.

Chameleon had a [theme based on the "I'm a Mac, I'm a PC" commercials]("http://forum.voodooprojects.org/index.php/topic,451.0.html"). I have downloaded that and uploaded the images here. I was wondering if someone would be able to make a similar theme for refit. I have been unable to find a good tutorial on how to do it.

[IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Blackosx_Mactico_Im_a_Mac.jpg[/IMG]

[IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_hfsplus.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_ntfs.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_ext3.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/device_selection.png[/IMG]


Another option would include Steve Jobs and Bill Gates:

[IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Steve.png[/IMG] [IMG]http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Bill.png[/IMG]

Can't say i'd want to be greeted by either of those when booting my computer, but someone has to do this for the lulz factor at least.

---

### Post by nxoxe on 2011-10-13
I was looking for a refit theme and that's bring me here...
and help me a lot... now I have somthing to share..

[IMG]http://farm7.static.flickr.com/6157/6240904379_ce4fb0351d.jpg[/IMG]

In my blog [noemoreno.tk]("http://www.noesblog.tk/2011/10/refit-mac.html") is the zip file with the refir folder and the icons.. and the thanks to everybody...

hope you like it like me.

---

### Post by robertomano24 on 2011-10-21
I also have a request.With the passing of Jobs, I was wondering if anyone could make this icon fit for rEFIt.


[IMG]http://gnews.com/wp-content/uploads/2011/10/RIP-Steve-Jobs.jpg[/IMG]

Would be great. Many thanks :)

---

### Post by nxoxe on 2011-10-30
> **robertomano24 said:**
> I also have a request.With the passing of Jobs, I was wondering if anyone could make this icon fit for rEFIt.


[IMG]http://gnews.com/wp-content/uploads/2011/10/RIP-Steve-Jobs.jpg[/IMG]

Would be great. Many thanks :)


Well here is you can put it on refit folder and replace the os x icn with the same name of course.

see you around..

---

### Post by mefi on 2011-12-30
[IMG]http://whatimg.com/i/09177103006121003077.png[/IMG][IMG]http://whatimg.com/i/99129887132988606396.png[/IMG]

My icons, using a black background and big selection ring posted previously by someone else. Pretty slick..

[ATTACH]209939[/ATTACH]
[ATTACH]209940[/ATTACH]

---

### Post by dwold91 on 2012-01-11
THANK YOU! That was my problem I think! Haha

---

### Post by dwold91 on 2012-01-12
Hey, this is a fairly old post, but I just got a new MBP a week or so ago and did some customizations to my reFIT based on Xbox and PS3. Tell me what you think. Also, attached are the banner and both the icons I used in .jpg format. Just convert them to icons and put them in the correct file. :)

---

### Post by Linforcer on 2012-01-14
I'm not sure about why anyone would use this... 
Does the Xbox represent windows, because it's microsoft's or is it Mac OS X because of the X, and what OS would the PS3 be?

To everyone out there using the theme most of this thread is about and kubuntu, like me, I've made some kubuntu logos ([os_linux]("http://www.megaupload.com/?d=1CX33ZUM")) ([boot_linux]("http://www.megaupload.com/?d=ZEZ4LEJ6")).

looks pretty much like this
[IMG]https://lh6.googleusercontent.com/-zNu9ML0f3w4/TuhX5kKfQUI/AAAAAAAAQsY/b2j_d_gKNIE/w301/images.png[/IMG]

---

### Post by teknikk7 on 2012-03-01
Any way to get this crosspatch background?

---

### Post by helonaut on 2012-03-06
> **raprap30 said:**
> To the OP: Mind if I fork your theme? I have already created more icons for Windows + more distros:

[http://desmond.yfrog.com/Himg135/scaled.php?tn=0&server=135&filename=cud.jpg&xsize=640&ysize=640](http://desmond.yfrog.com/Himg135/scaled.php?tn=0&server=135&filename=cud.jpg&xsize=640&ysize=640)
Very slick & cool you added the Archer's badge !
:KS A+

> **Raditude said:**
> Chameleon had a [theme based on the "I'm a Mac, I'm a PC" commercials]("http://forum.voodooprojects.org/index.php/topic,451.0.html").  I have downloaded that and uploaded the images here. I was wondering if  someone would be able to make a similar theme for refit. I have been  unable to find a good tutorial on how to do it.

[http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Blackosx_Mactico_Im_a_Mac.jpg](http://i61.photobucket.com/albums/h46/RaditudeForever/Im%20a%20Mac/Blackosx_Mactico_Im_a_Mac.jpg)

LOL @ your idea :)

---

### Post by the8thstar on 2012-03-08
> **mefi said:**
> [IMG]http://whatimg.com/i/09177103006121003077.png[/IMG][IMG]http://whatimg.com/i/99129887132988606396.png[/IMG]

My icons, using a black background and big selection ring posted previously by someone else. Pretty slick..

[ATTACH]209939[/ATTACH]
[ATTACH]209940[/ATTACH]

Beautiful work! I'm using your icons and the result looks very professional indeed.

Would you be able to make one more with the Ubuntu default wallpaper please? Thanks a lot in advance!

---

### Post by Kaitain on 2012-03-25
> **fatppl said:**
> I have a slight problem:

Everything is working, however, two of my boot icons are the same:

1)MacOSX from internal HD 

2)MacOSX from external HD 

How can i distinguish the icons for these two boot options... 

and yes i realize because they are both macosx this is why they both share the same icon - but is there any way I can distinguish the two?

I was hoping to solve a similar issue. I have a dual boot of Lion and Tiger (don't ask...) and wondered if there were any way to get rEFIt to display different icons for each one, even if it came down to some dumb numerical order-based identification. Anyone know?

---

### Post by WESBC on 2012-06-14
Here is my take on it. It goes well with my black Macbook as well.

[IMG]http://i874.photobucket.com/albums/ab306/wesleycatig/scaledTripleBoot.jpg[/IMG]

---

### Post by nxoxe on 2012-09-29
> **nxoxe said:**
> I was looking for a refit theme and that's bring me here...
and help me a lot... now I have somthing to share..

[IMG]http://farm7.static.flickr.com/6157/6240904379_ce4fb0351d.jpg[/IMG]

In my blog [noemoreno.tk]("http://www.noesblog.tk/2011/10/refit-mac.html") is the zip file with the refir folder and the icons.. and the thanks to everybody...

hope you like it like me.

here you go the link...

[http://www.mediafire.com/?x755ub68r5ma7q5](http://www.mediafire.com/?x755ub68r5ma7q5)

---

### Post by AshtonTS on 2012-10-21
This is amazing, loving the new icons. rEFIt was so ugly before but it looks nice now.

One thing, I can't get the selection-big.bmp to show up. When I reboot, its the same ugly selection thing stock rEFIt uses. I modded the efi.conf and everything, but it just won't show the custom one :(

---

### Post by michaelbrave on 2013-02-18
So I made a few icons for rEFIt just windows mac and ubuntu so far (till people request the others)
[IMG]http://fc09.deviantart.net/fs71/f/2013/049/8/d/refit_icon_design___mac__windows__ubuntu_by_themichaelbrave-d5vcr3n.jpg[/IMG]
figured I would come back and post it here since the ubuntu forums were so helpful getting it set up etc

you can download the icons [here]("http://themichaelbrave.deviantart.com/art/rEFIt-Icon-Design-Mac-Windows-Ubuntu-354993971")

---

### Post by boletusatanas on 2013-09-25
Hey folks,

I have run into this so helpful thread and I have fully customized my rEFIt bootloader. Thank you at first!

I have one only problem:
I have multiple menu entries, and I need to delete 3 of those. How can I do that?
I cannot find the list of operating systems able to be booted and then deleting the not useful ones

[IMG]http://s18.postimg.org/y1wfwrdpl/2013_09_25_13_03_03.jpg[/IMG]

---

