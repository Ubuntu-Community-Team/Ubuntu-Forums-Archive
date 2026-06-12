---
title: "OS X user new to Linux."
date: 2013-11-06
forum: Apple Hardware Users
---

### Post by antoniolamb on 2013-11-06
Hey you guys. I am the owner of an early 2011 macbook pro and I would really love to be able to run ubuntu from a usb thumb drive. 

I am tired of not being able to use alternatives to OS X. I want to test Ubuntu out and decide whether I want to dual boot. The problem is that I am not sure how to make a bootable thumb drive for an early 2011 macbook pro (8.2). I understand it could be quite complicated to get that working. Any help is appreciated.

---

### Post by jdwaugh on 2013-11-06
I have never done it, don't use OS X much, but here are directions on how to build a live thumb drive.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

Or if you prefer a more gui approach, this program seems like it will work:

[http://penguintosh.com/](http://penguintosh.com/)

Just use a thumb drive you don't mind reformating because I think you will lose everything on it.

Hope that helps, and happy experimenting

---

### Post by antoniolamb on 2013-11-06
I just tried the gui and I could not load the kernel :/. Any ideas what it could be? I feel like it might be the AMD graphics card. I found this but I am having trouble understanding it. [https://help.ubuntu.com/community/MacBookPro8-2/Raring](https://help.ubuntu.com/community/MacBookPro8-2/Raring)

---

### Post by buzzingrobot on 2013-11-06
Mac-specific install images are available at releases.ubuntu.com. 

The 8,2 will default to the AMD card, which will likely run much hotter than in OS X. The fans will max out. To use the onboard Intel video instead, the AMD must be disabled.  I never managed to do that reliably on my 8,2. Linux cannot switch between them as demand requires, as OS X can.

Good luck.

---

### Post by antoniolamb on 2013-11-06
Thank you for the replies. Okay. Well, so far I managed to get my macbook pro to recognize the USB drive, and I used this installer, which is actually quite good. [http://sourceforge.net/projects/mlul/](http://sourceforge.net/projects/mlul/)
I tried to use other installers like UNetboot but they didn't work. This is basically what it looks like for me, except the screen goes black and crashes after the part that says "fasten your seatbelts.. et al" 
[http://www.youtube.com/watch?v=Y5unDeUo8w0](http://www.youtube.com/watch?v=Y5unDeUo8w0) (skip to 2:00. pardon the crappy music... I didn't make the video)

I think I understand what is wrong.. It is probably the AMD card... how do I disable it so I just boot with just the intel video instead?

---

### Post by bapoumba on 2013-11-07
Moved to Apple Users.

---

### Post by buzzingrobot on 2013-11-07
I found burning a USB image via these instructions always worked: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx).

Macs have no BIOS, hence no BIOS setup where you can switch GPU's. If memory serves, the machine needs to boot in EFI mode before Linux will see the Intel. Left on its own, the Ubuntu Mac image boots in BIOS-compatibility mode (what Apple does with Bootcamp to convince Windows to install). The AMD needs to be disabled during the boot process before the kernel launches. I found, and have lost track of, instructions to accomplish this by editing Grub's configuration. On a full install, it worked once with one Ubuntu release.

There's a fair amount of guidance around the web about putting Ubuntu on Macbooks, with some that's specific to 8,2 units. I'd guess most of that applies to booting  from a USB stick.  However, the 8,2 seems to be particularly difficult to work with.

---

### Post by antoniolamb on 2013-11-07
Thank you buzzingrobot. I tried the guide, and unfortunately, everything goes well until I get to dd'ing to the USB drive. As soon as the process finishes, I get an error saying "this disk is unreadable". I'm not really sure what I might be doing wrong.
EDIT: wait I just checked the md5 hash on my ISO I downloaded and it did not match, so my ISO must have been corrupted... ****! maybe it was working before... I will get back to you guys on that asap.

---

### Post by antoniolamb on 2013-11-07
Alright so I tried again, this time I checked the md5 hash and it matches. I used this file: trusty-desktop-amd64+mac.iso (md5=6a6c95faf613baa98e89895b0fc26490)

Computer specs:
MacBookPro8,2
Processor Name:	Intel Core i7
graphics/displays: [B]AMD Radeon HD 6750M (PCIe)+Intel HD Graphics 3000 (built-in)
[/B]


I followed the instructions here word for word. [http://www.ubuntu.com/download/deskt...ick-on-mac-osx]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx") 
unfortunately, I still couldn't get it working. The thumb drive won't show up at all. I also have refind installed. This is what I did and what happened (commands are in green bold)

TERMINAL
**[COLOR=#008000]dhcp-209-206:~ antoniolamb$ diskutil list[/COLOR]**
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *750.2 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            749.3 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1 **[COLOR=#ff0000][<---- That is my USB drive][/COLOR]**
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *4.1 GB     disk1
   1:                        EFI                         209.7 MB   disk1s1
   2:                  Apple_HFS Untitled 1              3.8 GB     disk1s2
**[COLOR=#008000]dhcp-209-206:~ antoniolamb$ hdiutil convert -format UDRW -o /Users/antoniolamb/Desktop/trusty-desktop-amd64+mac.img /Users/antoniolamb/Desktop/trusty-desktop-amd64+mac.iso    [/COLOR]**
Reading Master Boot Record (MBR : 0)&#8230;
Reading Ubuntu 14.04 LTS amd64           (Apple_ISO : 1)&#8230;
Reading  (Windows_NTFS_Hidden : 2)&#8230;
...............................................................................
Elapsed Time: 50.456s
Speed: 17.7Mbytes/sec
Savings: 0.0%
created: /Users/antoniolamb/Desktop/trusty-desktop-amd64+mac.img.dmg

[COLOR=#008000]**dhcp-209-206:~ antoniolamb$ diskutil unmountdisk /dev/disk1**[/COLOR]
Unmount of all volumes on disk1 was successful
**[COLOR=#008000]dhcp-209-206:~ antoniolamb$ sudo dd if=/Users/antoniolamb/Desktop/trusty-desktop-amd64+mac.img.dmg of=/dev/rdisk1 bs=1m[/COLOR]**
Password:
892+0 records in
892+0 records out
935329792 bytes transferred in 197.279702 secs (4741135 bytes/sec)
dhcp-209-206:~ antoniolamb$
then I get this:
[IMG]http://s18.postimg.org/40nxhspg9/error.png[/IMG]
I have spent two days trying to get this to work... It is driving me crazy!!!!

---

### Post by buzzingrobot on 2013-11-07
Be sure to remove the '.dmg' extension OS X adds. You want just the '.img'.  Just mv or cp it.  You can call it anything so long as it ends in .img.

That help page mentions this but isn't clear or specific about removing the extra extension.

---

### Post by baabsaget on 2013-11-07
Unetbootin is your friend...
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

