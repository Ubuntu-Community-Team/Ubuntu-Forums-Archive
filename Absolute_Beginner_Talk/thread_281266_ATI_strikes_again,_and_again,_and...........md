---
title: "ATI strikes again, and again, and.........."
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-10-20
I wanted to update the driver on my ATI rage fury 128 and tried one of the wiki's and the result shut down my xserver.
So I did:
```
sudo dpkg-reconfigure xserver-xorg
```
and that set me free. I was happy but still could not use Google Earth, so I went to:[URL="http://ubuntuforums.org/showthread.php?t=75428&highlight=how+to+get+the+current+ATI+drivers+working"]http://ubuntuforums.org/showthread.php?t=75428&highlight
=how+to+get+the+current+ATI+drivers+working[/URL]
I followed those instructions and on reboot lost the xserver again.
this time```
sudo dpkg-reconfigure xserver-xorg
```
did not help at all. SO I went to:
[http://ubuntuforums.org/showthread.php?t=277498]("http://ubuntuforums.org/showthread.php?t=277498")
and did everything there but still have no xserver. Now I'm stumped and would really like to have some help.

Thanks in advance.

---

### Post by podunk on 2006-10-20
This is a very old card - yes? I had a hell of a time getting my Radeon 9200 to work (ATI dropped support) so I bet you'll really have a hard time.

Doing a search for "linux drivers for ATI Rage 128 Pro" I came up with these - but they are old! Red hat 7? RPM? I ain't got a clue whats going to happen when you do the alien thing

[http://www.pcauthority.com.au/download/dell-dimension-ati-rage-128-pro-driver.aspx](http://www.pcauthority.com.au/download/dell-dimension-ati-rage-128-pro-driver.aspx)

This is only 29 bucks - it says i will fit a 2X slot - and it looks right for it:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1163915&Tab=0&NoMapp=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1163915&Tab=0&NoMapp=0)

As far as getting your xserver back - when I trashed mine I couldn't get it to work again - I reinstalled Ubuntu and learned to back up before I changed it. :-(

[code]sudo cp /etc/X11/xorg.conf /etc/X11/xrog.conf_back_up

---

### Post by kindafunnylookin on 2006-10-21
Thank you for the back up code. I really did not want to spring for another card right now but from what I have been reading it seems to be unavoidable.

I wonder if it's possible to install a new card without loosing any of my file. Well, it certainly won't be the first time.

---

