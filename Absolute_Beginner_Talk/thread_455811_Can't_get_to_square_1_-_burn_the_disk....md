---
title: "Can't get to square 1 - burn the disk..."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ccfjeff on 2007-05-27
Hi,

I'm thinking there may have been a problem with the package from the download site, [United States CERIAS, Purdue University (North America)]("http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/") but I already registered for these forums so I'll post it anyway.

I began the download of 7.04 Feisty Fawn but it was a load.  I have a cable connection with an alleged 3 meg download speed, though it can vary quite a bit up or down from there.  Even so, I think the estimated download time was fluctuating at 5 hours or so.  If I remember correctly the download size was 4,066 MB which seemed rather odd as I read somewhere that the size on the CD would be a little less than 700 MB which makes sense as my CDs are only 700MB.  I figured there was some installation software or whatever and maybe it would be compressed or something before burning to disk but that sure seemed like a lot.  But whatever...

I stuck with it and let it load in the background and when it finally finished I clicked on the default which was to open it with Roxio disk burner or whatever it is.  Although some version of Roxio is on my computer it isn't the default and I don't think I have ever tried to use it.  My guess is that it is some crippled trialware or whatever that came with the computer.

But anyway it opened up and asked to burn my new download to CD, so I popped in a blank CD, hit OK or whatever the default was and it started to go but very quickly notified me that there was some error with linking to the file or something.  I may have tried it again, but eventually couldn't figure out what to do and hit cancel.  I figured there would be some icon on my desktop or something to try again, but there wasn't any trace of it that I could find and I hadn't specified anywhere to save the file.

Bummer.

So, I went back and tried again.  I did the download again but went on to bed and let it continue.  I got up about 5 am and saw that there was an error message that there wasn't enough room in the temporary files (maybe) and was informed that I would have to clear out some space.  That was a different error than the first time but I thought maybe that was what had caused the original problem.  There had been no option for me to choose which drive for the temporary files to be stored on.  I knew I didn't have 4 GB to spare on my C drive.

Bummer.

So...  I tried again.  This time I finally changed the default and selected "save to disk" and saved it to an external USB (not USB2) drive.  Once again the estimated time hovered around 5 hours or so.   and I went back to bed figuring it should be done by 10 to 10:30 or so.  The speed slowed down quite a bit, though, and even though and it was only about 40 to 45% done by 9:30am and it was still at an estimated 5 hours!  Bummer.  I think it finally finished about 2:30 pm or so.

Roxio popped up and offered to burn it to disk so I of course accepted the offer, but it said there was something wrong with the CD or there wasn't enough room on it.  It was probably a couple of years old but had never been used as far as I could tell, and it was listed at 700MB capacity, but I popped in another.  Same thing.  So I tried another.  Same thing.  So I tried another brand.  Same thing.  Bummer.

I just checked the file via Windows Explorer and it is listed at 3.97 GB / 4,163,890.  I thought perhaps a full blown Roxio was part of the installation package, but I doubt that would add anywhere near that much size.

As I was registering I tried downloading from the Western Michigan site.  Am I a glutton for punishment or what?  But surprise surprise it finished downloading a few minutes ago!  The size is listed at 714,464 KB.

They are both listed as .iso files.  Can I just click on it and it will be able to be burned to disk?  Some years ago I had downloaded a Linux disk but my system didn't know what to do with an .iso file.  I think I searched and found some programs that would be able to read .iso files but I ended up never installing the thing.

How do I burn it to disk now?  I'm guessing 714,464 is indeed just below the 700MB threshold of my CDs?

Any help would be appreciated.  Thanks.

---

### Post by confused57 on 2007-05-27
Maybe this link will help:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I also have Roxio and just right click on the iso and select "Record to CD", which opens Roxio, set the write speed to no more than 8x...Roxio automatically burns an iso "as an image" in the version that I have.

714 Mb sounds about right for the desktop live cd...the 4 Gb file "may" have been the dvd?

There's a free cd burner that you can download that works pretty well...CDBurnerXP Pro3, don't have the link offhand, but googling should find the homepage.

---

### Post by ccfjeff on 2007-05-27
> **confused57 said:**
> Maybe this link will help:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

I also have Roxio and just right click on the iso and select Write to Disk, which opens Roxio, set the write speed to no more than 8x...Roxio automatically burns an iso "as an image" in the version that I have.

714 Mb sounds about right for the desktop live cd...the 4 Gb file "may" have been the dvd?

Thank you very much.  

A followup question though.

The mentioned the Checksum and included a link to download a program to do so.  As I recall that was one of the things that had confused me a bit the last time I had tried this.  As I recall I had downloaded some very long number and was to do something with the downloaded file to make sure it was identical.  I thought it might have been a way to make sure I hadn't downloaded a file with a virus in it or something.

Does this program do that automatically?  I don't have any checksum number to check it against.

Thanks again.

---

### Post by ramjet_1953 on 2007-05-27
Some VERY Important things to remember when burning any iso image.

1. Remember to burn it as an iso image, not just a data disk. Most buring software has that option tucked-away in the drop-down menus.

2. Burn the image at a speed no greater than 4 X , or you will have big problems with errors.

3. Use high quality media. Cheap CDR's are fine in most instances for music and data, but for iso's you must use premium media.

If you do all of the above, the burn should be fine.

Regards,
Roger :cool:

---

### Post by rusty4r on 2007-05-27
the psychocats page should also suggest a checksum program that will check the number for you

---

### Post by ccfjeff on 2007-05-27
> **ramjet_1953 said:**
> Some VERY Important things to remember when burning any iso image.

1. Remember to burn it as an iso image, not just a data disk. Most buring software has that option tucked-away in the drop-down menus.

2. Burn the image at a speed no greater than 4 X , or you will have big problems with errors.

3. Use high quality media. Cheap CDR's are fine in most instances for music and data, but for iso's you must use premium media.

If you do all of the above, the burn should be fine.

Regards,
Roger :cool:

Thanks.  It looks like Roxio Easy CD Creator is the default for .iso files.  It has an option in a drop-down box to set the speed lower to 4X or even 2X but there is no option that I can find for selecting .iso or image or music or anything.  I wonder if it automatically detects that.

---

### Post by ccfjeff on 2007-05-27
> **rusty4r said:**
> the psychocats page should also suggest a checksum program that will check the number for you

OK, but I don't have the checksum from the website.  Here's the page I downloaded it from: 

[http://mirrors.cs.wmich.edu/ubuntu-releases/]("http://mirrors.cs.wmich.edu/ubuntu-releases/")

According to the info page for Nullriver's checksum program, it sounds like I would have to find it on that page somewhere:

[INDENT][COLOR="DarkRed"]Once you have downloaded the file, use winMd5Sum to get the MD5 checksum of the file on your computer. Then make sure that the MD5 checksum from the web site is the same. If they are the same, then your file is exactly the same as the file on the website.[/COLOR][/INDENT]

Am I misunderstanding this or is there some other place to get the checksum as it is supposed to be?

---

### Post by rusty4r on 2007-05-27
no I think you are understanding it you should be able to get the checksum number from your source. also the psychocats page recommends another free program for burning the iso. after I had trouble I used it so that I could follow her directions to the letter and it worked for me

---

### Post by rusty4r on 2007-05-27
[http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/feisty/]("http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/feisty/")

here is the link  to the checksum or "MD5SUM" from your source

---

### Post by ccfjeff on 2007-05-27
> **rusty4r said:**
> [http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/feisty/]("http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/feisty/")

here is the link  to the checksum or "MD5SUM" from your source

Ok, thanks, I figured out how you got there and I doublechecked with the WMich link and it looks to be the same:
[http://mirrors.cs.wmich.edu/ubuntu-releases/feisty/]("http://mirrors.cs.wmich.edu/ubuntu-releases/feisty/")

e296e3468358789904097fc8df29609a

Thanks again for your time & help.

---

### Post by confused57 on 2007-05-27
It should look something like this:
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso

---

### Post by ccfjeff on 2007-05-27
> **confused57 said:**
> It should look something like this:
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso

Thanks.  It does. And it matches up!  

e296e3468358789904097fc8df29609a

I'm ready to burn.  (so to speak).

Thanks again!

---

