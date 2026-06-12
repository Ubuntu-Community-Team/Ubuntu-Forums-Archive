---
title: "CD/DVD ROM does not see files"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by rodgerpb on 2007-09-14
Hello...I have been searching through the forums without much success  with this.

My system has two optical drives:  a CD/DVD-ROM, and a CD-RW.  They are ATAPI devices located on the same IDE cable with the CD/DVD-ROM set as master and the CD-RW set as slave.

When I put any kind of disc (commercial dvd; dvd with burned files and same for cd's), the drive recognises what type of disc has been put in - but sees it as empty.  What I get is an empty CD/DVD creator folder.

I have tried a number of solutions in the forums which appear to involve using Shell commands to change owner, and change permissions on the drive, as well as editing the fstab file to contain a User ID and a gid - but these make no difference.

Everything seems to work fine in the CD-RW (except of course it does not read DVD's).

This is an ex Windows PC and everything did work fine under windows

Any help would be appreciated as this is really frustrating!!

Thanks, Rodger

---

### Post by bone2006 on 2007-09-14
Are these DVD movies?  When I've had an encrypted movie the same thing happens.  See if you can play a DVD movie first, if not fire up the terminal

copy and paste each of these commands one at a time

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install libdvdread3 libxine1-ffmpeg libdvdcss2

If your using totem, give put this in next
sudo apt-get install totem-xine

Just a suggestion

---

### Post by mc4man on 2007-09-14
I just posted about the same thing (didn't see your post) For curiosity sake try inserting and then ejecting a cd(music), then try a dvd , on my boxes this fixes things till I reboot
i've also noticed some other strange things lately with commercial disks - 1 has 12 vts and is 7.2gb, but when you browse the video_ts It only shows 7 vts and 6.8gb size (tried on 3 setups same thing)

edit:didn't realize you can't mount cd's properly

---

### Post by rodgerpb on 2007-09-15
:(Hi - thanks.  I have just tried those suggestions, which have not worked.

Firstly: I tried with a DVD which is not encrypted 

Next: I tried the audio CD and then the DVD in sequence.

Whatever disc I put in that drive (which includes a CD which a few jpeg images on it)-  it just sees it as an empty disc and double clicking on the icon just brings up the CD/DVD Creator folder which is empty.

I**[SIZE="4"] think that your comment about the drive not mounting the media correctly sounds in right all park[/SIZE]**

However - what I do not know how to do is:

[LIST]
[*]Check whether the media has been mounted correectly or not
[*]Issue the  terminal commands  so that the media can be mounted manually if it is not happening automatically
[*]make adjustment that will allow the media to be mounted automatically in that drive
[/LIST]

If there are any tests possible - I can post the output in a reply.

Many thanks

Rodger

---

### Post by rodgerpb on 2007-09-15
:confused: I think that the problem may be one of mounting the device or filesystem.

Here is what I tried:  (using a simple data CD with just a few jpegs on it)

sudo eject /dev/hdc
This opened the drawer of the CDROM device - that must be an 'address' or 'location' of the CD-ROM device.

So I tried the following
sudo mount /dev/hdc  /media/cdrom0

When I looked in the folder /media/cdrom0, I could see the files that are on the  CD

However when double clicking on the the CD icon -all I get is empty CD/DVD creator folder

So it does look as though this optical drive is mot mounting correctly in the same way as the other optical drive (which is a CD_RW).

My questions:

1.  Why is it not mounting automatically/correctly?
2. How do I get it to work properly?

Help -experts - please!!!!!!!!!:)


My  questions

---

### Post by rodgerpb on 2007-09-15
Does this help to understand what is going on.

I have put a CD data disc in the drive which has some Powerpoint files on it (it reads perfectly from the CD-RW drive).

I have typed in the following command

rodger@aragorn:~$ sudo mount /dev/hdc
Response was
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

rodger@aragorn:~$ dmesg | tail
[32086.778277] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[32259.768732] ISO 9660 Extensions: Microsoft Joliet Level 1
[32259.809083] ISOFS: changing to secondary root
[32348.680620] cdrom: This disc doesn't have any tracks I recognize!
[32680.989019] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[32680.989038] hdc: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
[32680.989047] ide: failed opcode was: unknown
[32681.188434] hdc: error code: 0x70  sense_key: 0x03  asc: 0x02  ascq: 0x00
[32681.188454] end_request: I/O error, dev hdc, sector 64
[32681.188919] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
rodger@aragorn:~$ 

Does this help to explain the problem?

---

### Post by mc4man on 2007-09-15
my problem has become more of a curiosity ie. why after booting up are commercial dvds seen as blank disks and then how can inserting and ejecting any cd(with data on it) allow comm. dvds to be recognized (till a reboot). In your case I'd first try to determine if drive is still good
How old is it
what brand
do you have another dvd drive to try in it's place
what controller are your drives on  ie. primary ide, secondary ide 
what are the jumpers set to

---

