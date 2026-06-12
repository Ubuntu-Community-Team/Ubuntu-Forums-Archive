---
title: "need to verify CD (md5 a CD, not an ISO)"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by josephpford on 2006-12-22
Hello, I'm a newbie, as are most people in this forum I suppose.  I had 6.06 sent to my place in the form of a CD (that's an awesome service!!!) and that works just fine.  However, I downloaded 6.10 to my Windows XP desktop and burned it to a CD and I can't boot that.  I tried using the "Check CD" option on the boot menu, but it doesn't even get past "starting linux kernel".  I also checked the MD5 of the ISO file on my desktop using the winMd5Sum program Ubuntu recommends (another great easy to use program), and that checked out okay.  My next guess is I burned the CD wrong or it failed or whatever.  I burned two copies, and both copies didn't work.  Is there a way to check the MD5 of the actual CD?  Or is there another way I can verify the CD has no problems?

---

### Post by taurus on 2006-12-22
Did you burn it as an ISO image and make sure you burn it at a slow speed like 4x...

---

### Post by josephpford on 2006-12-22
Yes I burned it as an ISO image, but I did not burn it at a slow speed.  It took 5 minutes and some seconds to burn the entire image.  I am guessing that is about 16x, but I don't know for sure.  I'll try burning at 1x tonight and see if that works.  I'd still like to know if there is anyway for me to verify the burn against the MD5 (or is that just not possible?)

---

### Post by Bachstelze on 2006-12-22
To dump an iso from your disc :

```
dd if=/dev/cdrom of=image.iso
```

Then you can md5sum the iso :)

---

### Post by josephpford on 2006-12-22
Ok, I'll try that.  Thanks!

I know one problem I will run into probably is that my harddrive is a secure NTFS file system, so I won't be able to dump the CD onto that drive.  This should be interesting.  But I'll try playing around...

Thanks,
Joe

---

### Post by OzzyFrank on 2007-08-26
Yes, but none of this answers the actual question, so I am going to post it again myself soon (unless it gets answered here of course). I have successfully gotten FileCheckMD5 for Windows to run in Wine, and it is used for creating MD5s for whole folders and verifying the burned result after (you have to have the .md5 file on the CD or folder too of course). Trouble is, that unlike very other MD5 file out there, the Ubuntu CD has a "md5sum.txt" file instead of one with an "MD5" or "md5sum" extension... so FileCheckMD5 fails to see it at all (and if you type it in it still doesn't work).

Now, I gather there HAS to be a way to check the various Ubuntu CDs besides the check CD option in the boot menu. This would not only save the hassle of booting a Live CD just to test it, but would be invaluable for the ones we CAN'T test (like I can't test amd64 CDs coz I am i386).

So what utility for Linux/Ubuntu is made for this purpose... checking whole folders/CDs instead of individual files... and that can handle the .txt extension?

---

### Post by asmoore82 on 2007-08-26
> **OzzyFrank said:**
> Yes, but none of this answers the actual question, so I am going to post it again myself soon (unless it gets answered here of course). I have successfully gotten FileCheckMD5 for Windows to run in Wine, and it is used for creating MD5s for whole folders and verifying the burned result after (you have to have the .md5 file on the CD or folder too of course). Trouble is, that unlike very other MD5 file out there, the Ubuntu CD has a "md5sum.txt" file instead of one with an "MD5" or "md5sum" extension... so FileCheckMD5 fails to see it at all (and if you type it in it still doesn't work).

Now, I gather there HAS to be a way to check the various Ubuntu CDs besides the check CD option in the boot menu. This would not only save the hassle of booting a Live CD just to test it, but would be invaluable for the ones we CAN'T test (like I can't test amd64 CDs coz I am i386).

So what utility for Linux/Ubuntu is made for this purpose... checking whole folders/CDs instead of individual files... and that can handle the .txt extension?

**pipe** the output of the 'dd' command directly to the 'md5sum' command if
you don't want/need to actually save the iso file ...

```
~ $ dd if=/dev/cdrom | md5sum
```

this works _because_ the dd command defaults to **standard output** if you don't tell it where else to go
_and_ because 'md5sum' defaults to **standard input** if you don't give it a filename to work with ...
note that even if the commands didn't behave this way, you could ***still*** get the job done like so ...
```
~ $ dd if=/dev/cdrom of=/dev/stdout | md5sum /dev/stdin
```

:guitar:*NIX Rules!!!

---

### Post by OzzyFrank on 2007-09-05
**[COLOR="Blue"]cd /media/cdrom0 && md5sum -c md5sum.txt[/COLOR]**

Paste that in a teminal, then mark this as [SOLVED]. This will work with any CD that has a file called "md5sum.txt". You can of course change that, as well as the device path if yours isn't "cdrom0" etc. When finished, you'll be told if there were errors (if there is no mention, there were no errors). Works a charm! Cheers.

---

### Post by sciencewhiz on 2008-01-04
> **asmoore82 said:**
> **pipe** the output of the 'dd' command directly to the 'md5sum' command if
you don't want/need to actually save the iso file ...

```
~ $ dd if=/dev/cdrom | md5sum
```



I found when i ran that, it checked more data then the size of the iso file and gave the wrong checksum. I limited the size with bs and count and then everything worked as expected.

---

### Post by boltronics on 2008-02-12
sciencewhiz: you are correct. 

```
 ~ $ dd if=/dev/cdrom | md5sum
```
is definitely wrong, because md5sum calculate trailing data found after the burned ISO image data, if any exists. In my experience, it usually does.

This is what works for me:
```
 ~ $ dd if=/dev/scd0 bs=2048 | head -c 727488512 | md5sum -
```

where 727488512 is the size of the ISO. Now if you want to verify the Ubuntu CDs that you've received in the mail, you won't know the original ISO size so you'll need to Google it. For images that have jigdo files, you can read the size from the jigdo data in a text editor. Look at the "Image size" line to see where I found the value for this image:

[ubuntu-7.10-alternate-amd64.jigdo]("http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-amd64.jigdo")

---

