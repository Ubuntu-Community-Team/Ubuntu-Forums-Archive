---
title: "ASUS X101 with Ubuntu 11.10"
date: 2011-10-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pagereborn on 2011-10-21
Has anyone install the newest Ubuntu 11.10 on this netbook yet?
How is it?
and how did you install it?

---

### Post by Liam2010 on 2011-10-29
Well I am have 11.04 installed on asus x101, it is working great so far.  Maybe not as fast as meego but still pretty fast.  I am sure 11.10  would work just as well.


To install:     1.  Download "universal usb installer"  from  [www.pendrivelinxcom](www.pendrivelinxcom)  
                    2.   Download the ubuntu 11.10 iso from [www.ubuntu.com](www.ubuntu.com)
                    3.  Insert a blank thumbdrive
                    4.   Run your universal usb installer program and follow the on screen instructions to download 
                          the iso to the thumb drive.
                    5.   restart your asus and press f2 to enter the bios
                    6.   Alter the boot order so that the asus will boot from your thumbdrive
                    7.   You asus will now boot to ubuntu, click on "install ubuntu" and follow the on screen instructions.


Sorry if you already knew any of this!

Liam

---

### Post by Liam2010 on 2011-10-29
Sorry, the "linx on a pendrive installer"  is a window program.  If you are already using ubutnu you can get an installer package fro the software centre, it's called, "unetbootin"

Good luck

---

### Post by G1sbert on 2011-10-30
It works great at my X101, the only thing not working is the Resume from Suspend. It always shuts down when i want to suspend. Anyone else with the same Problem?

Greets G1sbert

---

### Post by Janeleaper on 2011-11-23
Hi, I tried following the instructions but it didn't work out.  Can someone tell me what I'm doing wrong:

To install: 1. Download "universal usb installer" from [www.pendrivelinxcom](www.pendrivelinxcom) [COLOR="Red"]Installed Unetbootin on my Ubuntu desktop. the application that you give in the next post for ubuntu.  [/COLOR]
2. Download the ubuntu 11.10 iso from [www.ubuntu.com](www.ubuntu.com) [COLOR="red"]Yes - onto my desktop.[/COLOR]
3. Insert a blank thumbdrive [COLOR="red"]Yes into my desktop.[/COLOR]
4. Run your universal usb installer program and follow the on screen instructions to download 
the iso to the thumb drive. [COLOR="red"]Yes[/COLOR]
5. restart your asus and press f2 to enter the bios [COLOR="red"]Yes, having first inserted the thumbdrive[/COLOR]
6. Alter the boot order so that the asus will boot from your thumbdrive. [COLOR="red"]No.  No boot order showed up, only Meego.[/COLOR]
7. You asus will now boot to ubuntu, click on "install ubuntu" and follow the on screen instructions.

---

### Post by Janeleaper on 2011-11-24
Hi I'm still struggling to get the x101 to work with one version of ubuntu or another.  

I first installed 10.04 from cd, but could not get a wifi connection, so then tried Lubuntu 11.10.  Same problem.  

I'm not sure how to deal with this, since the x101 does not have an ethernet port.

---

### Post by Janeleaper on 2011-12-01
I just want to report that I did sort out the problem, and Lubuntu 11.10 is working well on my x101 now.

---

### Post by kidd79 on 2011-12-04
> **Janeleaper said:**
> Hi, I tried following the instructions but it didn't work out.  Can someone tell me what I'm doing wrong:

6. Alter the boot order so that the asus will boot from your thumbdrive. [COLOR="red"]No.  No boot order showed up, only Meego.[/COLOR]
7. You asus will now boot to ubuntu, click on "install ubuntu" and follow the on screen instructions.


Hello Janeleaper

I have exactly the same problem, I tried diferent drives and different live USB creating software, but no luck, MeeGo keeps loading as if there were no live USB at all.

As I see rom your next posts, you have resolved this issue, so could you please share your wisdom :)

---

### Post by Janeleaper on 2011-12-04
To get into the bios, keep Fn pressed while tapping F2, while booting up.  You can then change the boot order.  I installed lubuntu 11.10 from a cd using an external cd drive.  It all went smoothly.

After I'd installed Lubuntu 11.10, the x101 was slow to make connectivity.  But it did so eventually, and there has been no problem since.

---

### Post by kidd79 on 2011-12-05
Oh no, I suppose you get me wrong.
Actually I got into BIOS and changed the boot order.

The problem is, when I quit BIOS with thumbdrive inserted, netbook still loads MeeGo.

---

### Post by Janeleaper on 2011-12-05
I'm sorry to hear about that.  I haven't got anything to suggest.  I'd not got into the bios.  The splash screen says to press F2 to enter setup, but actually you have to press Fn while tapping F2. 

In Bios Setup select Boot Device Priority.  Change to 1st Boot Drive Removable Device.  That worked for me.

If you've tried that and it doesn't work, all I can suggest is doing what I did, and using an external cd drive instead of a thumb drive.

---

### Post by Janeleaper on 2011-12-05
As an afterthought.  If you just press F2, I think you get a boot priority screen (as you do with Ubuntu), but I found I could not change the boot order on it, which is why you need to get into setup.

---

### Post by kidd79 on 2011-12-05
> **Janeleaper said:**
> I'm sorry to hear about that.  I haven't got anything to suggest.  I'd not got into the bios.  The splash screen says to press F2 to enter setup, but actually you have to press Fn while tapping F2. 

In Bios Setup select Boot Device Priority.  Change to 1st Boot Drive Removable Device.  That worked for me.

If you've tried that and it doesn't work, all I can suggest is doing what I did, and using an external cd drive instead of a thumb drive.

Yes, that's exactly what I did, but that is not working for me at all :(

---

### Post by Janeleaper on 2011-12-05
Sorry.  I've no technical knowledge, so I can't go further.

---

### Post by Janeleaper on 2011-12-05
Just a thought.

Have you tried altering the boot order on the setup (Fn + F2) and then rebooting pressing F2 and looking at the boot page?

---

### Post by kidd79 on 2011-12-05
> **Janeleaper said:**
> Just a thought.

Have you tried altering the boot order on the setup (Fn + F2) and then rebooting pressing F2 and looking at the boot page?
Yes, it only shows MeeGo as a sole boot option (also prompts "Press TAB to edit options", which is irrelevant in my case):cry:

---

### Post by Janeleaper on 2011-12-05
Excuse me if you've done this correctly, but I can't help thinking that you are not altering the boot order correctly.

When you are on the change boot order page, you use the + and - keys to alter the order.  Actually, I found the - key worked and the + key didn't for some reason.

---

### Post by kidd79 on 2011-12-05
> **Janeleaper said:**
> Excuse me if you've done this correctly, but I can't help thinking that you are not altering the boot order correctly.

When you are on the change boot order page, you use the + and - keys to alter the order.  Actually, I found the - key worked and the + key didn't for some reason.
Yes, of course I did.

Actually, for the moment I tried 5 different USB Flash drives, 1 to 16 GB from different vendors, and 4 different Live USB creating utilities, 2 under Xubuntu and 2 under Windows7, all this in all possible combinations, I suppose (and in every one of two USB ports on x101). Everything works fine on my other netbook (Lenovo S10-2), but nothing worked on x101. Needless to say every USB Flash drive work just fine under MeeGo.

So I suppose now the problem is NOT with USB drives nor my ISO nor USB ports on x101. The only possible cause, as I see it, is the x101's BIOS which refuses to accept USB Flash drives at all as valid bootable devices. I applied to ASUS' support via [http://support.asus.com](http://support.asus.com) and wait now for their reply.

---

### Post by Janeleaper on 2011-12-05
I think you must be right, given the only difference between us is that I used an external cd drive.

---

### Post by kidd79 on 2011-12-06
> **Janeleaper said:**
> I think you must be right, given the only difference between us is that I used an external cd drive.

BTW, speaking about differences, have you updated BIOS on your x101?

---

### Post by Janeleaper on 2011-12-06
I don't know how to do that.  Total lack of technical training, you see.  I have updated Lubuntu.

---

### Post by kidd79 on 2011-12-08
> **Janeleaper said:**
> I don't know how to do that.  Total lack of technical training, you see.  I have updated Lubuntu.I contacted ASUS Support, they said they have right there x101 with updated BIOS 0502 (the one OOTB is 0301), and everything works fine for them. However they suggested downgrading BIOS back to 0301 and re-trying USB-boot.

BUT! When I started BIOS downgrade, I got the messages that x101 "sees" the USB Flash drive but can't read BIOS file there for updating.

So I suppose something just went wrong and my x101's BIOS just can't read USB drives, that's why all the troubles with Xubuntu not loading from Live USB Flash drive.

I guess I have to take my x101 to ASUS tech guys and pray they will fix it :(

---

### Post by wildpredator on 2012-01-28
hey! i spent almost 8 hours solving  same problem, i had a flash drive just like you. then i came across this: [http://myx101.wordpress.com/2011/10/08/howto-boot-from-a-usb-flash-drive/](http://myx101.wordpress.com/2011/10/08/howto-boot-from-a-usb-flash-drive/) 

it appears that all I had to do was hold Esc button. so simple it makes me want to cry... 

hope it helps.
good luck.

( this reply is for those who are trying to put something useful on X101 instead of original operating system that came with the netbook )

---

### Post by kidd79 on 2012-01-29
Thank you for your reply.

However, this does not help. I've seen already that page and tried of course myself to do the same. in my boot device selection screen there is no USB flash drive, only the main system :(

---

### Post by CptGrinch on 2012-02-21
hallo...i had the same problem.try this:

go to the boot menu in your bios.

now go to "hard disk drives". 

select your usb device as 1st.

now you should be able to set the usb on top in the boot priority list


hope it works for you as it did for me :)

sorry for my english, i m still learning

---

### Post by jessel on 2012-03-01
My wife has the Asus X101. She was having problems with chromium browser to the point where it was useless. It was giving a certificate error, even non-secure web pages. I went to update, and the update utility was broken, so I went to install another browser and the application installer utility was broken too. She was running meego v. 1.09, I went to the meego website and downloaded and installed the meego v. 1.20 (for netbooks). The wife did not like it, though it seemed to work. Her biggest complaint was that it didn't have the soduku game she got in the habit of playing.

So I installed Ubuntu 11.10. It works well, and has soduku, of course. I'd recommend a standard ubuntu install over the meego any day. I though there might be problems but it works well.

I think that the x101 is a pretty cool netbook, because of the SSD.  But getting the thing to boot a usb thumb drive was very frustrating. It took a while to figure it out. What really got me was that I initially knew to hit esc to prompt the boot menu, but didn't realize I had to reconfigure the BIOS.

---

### Post by Kangarooo on 2012-04-15
When booting using USB press ESC to open boot order and choose USB.
This was also problem i found later is on x101.. ESC is needed to press on starting while black screen bios info coming

---

