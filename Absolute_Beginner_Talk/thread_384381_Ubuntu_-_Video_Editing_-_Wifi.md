---
title: "Ubuntu - Video Editing - Wifi"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by ahickey on 2007-03-14
Hi,

My notebook as died and I'm using it as a reason to move 100% to Linux.
The only things I haven't sorted out are Video Editing and recommendations on Wifi Cards.
Any and all recommendations appreciated.


Video Editing Needs:
Capture from DV Camera (Firewire)
Edit DV
Author DVD
Record DVD movie - not just put the video file on the disk


Wifi Needs:
Recommendations on specific PCI cards or USB Dongles.

Iff these two are sorted then there is nothing standing in my way besides by own ignorance...

Thanks for any and all help.
Albert.

---

### Post by reclusivemonkey on 2007-03-14
> **ahickey said:**
> 
Video Editing Needs:
Capture from DV Camera (Firewire)
Edit DV
Author DVD
Record DVD movie - not just put the video file on the disk


dvgrab will capture from your DV camera and Kino will edit your DV. I think you can import directly via Kino, although I don't have a DV camera so can't say for sure. Authoring DVDs can be done in DeVeDe or QDVDAuthor although I have not had much luck with either I am afraid. I think tovid is another option although its command line only.

> **ahickey said:**
> 
Wifi Needs:
Recommendations on specific PCI cards or USB Dongles.


I have a Broadcom card which works fine in Edgy; lspci lists it as

Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by ahickey on 2007-03-15
Thanks for that.

I use to be a command line guy in the DOS days and then moved into Windows world.
I am not adverse to a bit of config file editing and command line processes.  

I'm looking forward to the challenge.  It will be good to get technical again.

Albert.

---

### Post by reclusivemonkey on 2007-03-15
> **ahickey said:**
> Thanks for that.

I use to be a command line guy in the DOS days and then moved into Windows world.
I am not adverse to a bit of config file editing and command line processes.

I'm looking forward to the challenge.  It will be good to get technical again.

Albert.

You will *love* Linux then :-)

A lot of people seem to have problems with WiFi cards and the various GUI's; I used the CLI for mine as I used to have to set it up this way in Slackware and its pretty straightforward as long as you follow the right steps.

The Wikis for Ubuntu are particularly helpful when you are just starting out;

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I am sure there will be a Feisty one up as soon as its out officially.

---

### Post by ahickey on 2007-03-15
That's what I'm hpoing for.  It is a bit of techie fun again after being a user for so long.
My expectations is that it will all work in the end but it might be a bit painful getting there.

This is OK for me as I will enjoy the process as much as the end result and will give me the knowledge and experience to help others around me.

---

### Post by ahickey on 2007-05-31
Well, I took the plunge.  
I am running Ubuntu on my system - not dual boot, so no going back.

I am now running 64bit Feisty on an AMD64 Semperon based system. 
Motherboard - Asrock AliveNF6G-DVI
512MB RAM (64MB shared for video – NVIDIA 6100)
6 x Onboard USB ports work – needed Feisty
Onboard Audio works – only checked stereo – needed Feisty
Running at 1280x1024 24 bit colour
PS2 Mouse USB Keyboard
Digital Camera – Canon IXUS 60 connects
External USB hard drives connect and work
External NTFS drive works after installing NTFS support
External USB DVD Writer works

My external NTFS drive and External DVD writer also have Firewire, so I will be testing if they work on the Firewire connection as well.  I will probably leave them as USB as I have spare USB ports and limited Firewire ports.

I have wifi set up using a PCI LAN card from [www.linuxemporium.co.uk](www.linuxemporium.co.uk).  I did have to use a static IP address, but other then that it all worked perfectly.  I didn’t use their script, just the standard support from Feisty

Evolution for my emails - is it just me or is it very slow at downloading emails.

Firefox for web browsing – say no more.

gedit for web design - I hand code PHP/HTML, so the code highlighter here is enough for me for now.

The GIMP for image editing for web design and other bits.

Mogrify for batch resizing of images for web gallery – create thumbnails. I have a PHP script that auto creates a gallery for all thumbnails in a folder and full size images in a sub folder.  I just FTP the thumbnails and the fill size images, FTP the PHP page and it just works.

gFTP for uploading files – had to untick the option to keep permission as it stopped the pages from being accessible from the website.

I have played with KINO and it worked for capturing video from my camera through Firewire - I can't control the camera from KINO but that might be the Firewire cards fault.
I have done some limited editing with it as well (adding and removing clips, trimming clips)  It gave me some audio codec error when trying to save in DVD format that I haven’t tackled yet, but I expect it to be some package that’s missing.

I even have Beryl working - when I bother to enable it as I'm a bit of a minimalist and so don’t really like to have the overhead of wobbly windows, but it works.  

The only problem I still have is what looks like an issue rendering JPGs where unless they are at their native resolution I get stray green pixels kind of like tearing of the image.

So, after 2 months of running Ubuntu it is doing everything I need.
I’ve had fun getting some things working and been frustrated getting other things working but overall I’m very happy and have a sense of achievement.

---

