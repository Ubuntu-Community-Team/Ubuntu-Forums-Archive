---
title: "Can not get Ubuntu to install on laptop"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by conbrio on 2006-03-16
Hello all,

After doing a some reading and research on linux distros, I decided to try ubuntu. Well I downloaded the live cd iso and burnt the iso via nero onto a cd. tried out the cd in my laptop and started to boot from the cd. After a couple of seconds (I could see text scrolling up the screen), I got a blank screen. I could not do anything. I could see no text, no cursor, nothing. So I took out the live cd and tried it in my desktop and it loaded up just fine. From that I do not believe I have a bad download or a bad burn on to the cd. 

After I tried the live cd in my desktop, I downloaded edubuntu to try on my laptop. Same thing. It would start to install, I could see text, and then just a blank screen. I am thinking that there might be some sort of hardware issue. Has anyone else had this problem and got it resolved. My specs for my laptop are as follows

Compaq V5000Z Laptop (about 14 days old)
Sempron 3000+
768mb DDR Ram
Dedicated 128mb moble X200 ATI Graphics
40gig HD
Onboard wireless
Dvd-Ram

Thanks,
Con Brio

PS I have read the forums and did a search and tried some of the suggestions others have mentioned.

---

### Post by Pragmatist on 2006-03-16
Did you set your BIOS boot order to boot from the CD first?

---

### Post by taurus on 2006-03-16
It's probably because of your video card!!!  Instead of hitting enter to install Ubuntu, see if you can install just the server version.  So, enter "server" (without the quotes) at the prompt and see if Ubuntu would want to install it...

---

### Post by conbrio on 2006-03-16
Aye, set to boot from cd. I can get the "splash" screen that has the hit enter for install. Once I hit enter I see the text scrolling down the screen and after it finishes scrolling (about 15 to 30 sec) I get just a blank screen. I let it sit there once for 15 minutes to see if something would happen and nothing did.

Con Brio

---

### Post by taurus on 2006-03-16
Again, see if you can install the server version on your laptop and if you can, then you can install Gnome window manager later!!!

---

### Post by conbrio on 2006-03-16
ok just tried to install the server and still back to the blank screen. :(

---

### Post by jml on 2006-03-16
I agree that it may be the video card in the laptop.  Instead of booting into the terminal, you might want to try booting with alternative boot paramaters.  Instead of hitting enter when the live cd boots.  press the appropriate function key to try some options.  For example, booting the live cd with the command "live vga=771" without the quotation marks might work.  But there are a lot of suggestions in the boot help screens.  Look them over and write back with your progress or problems.  Hang in there, we should be able to help you get it going.  :) 

Joe

---

### Post by conbrio on 2006-03-16
ok tried booting with other paramaters. I tried all the ones that seemed likely to try and a few that didn't. The only one that did not go "can not find xxx kernel" and go to a boot promt was live acpi=off. That one started to load and then the blank screen yet again. Not giving up. I really want to try this distro and see what it is about. I really want to try edubuntu, but I want it on my laptop so I can let my classmates see it and to try and get them to try it out. We are in a teacher ed program at the local univ. 

Ok, I just downloaded the install iso for ubuntu and it is almost finished burning at 8x. Got to love those great download speeds. Will update again after I try the new disc.

---

### Post by conbrio on 2006-03-16
think I may have found the answer. I will post back shortly

---

### Post by conbrio on 2006-03-16
ok, First off let me say I am a somewhat of an idiot for not reading everything correctly. I did finally get the installer to work. My problem was when I was going through the other boot paramaters was I left off the front part of the command ie "linux vga=771". I was just doing vga=771. Well as I said I got it to start to install and I get to the partition part of the install and I cannot seem to get my hd to resize. I have read the wiki and done was was posted but the partition stays the same. I do not want to delete the partition and start over, just resize.

---

### Post by taurus on 2006-03-16
You already have XP on it!!!  You may need to use Partition Magic to resize your NTFS to create an empty partition to install Ubuntu on it.  I am not sure if the LiveCD comes with gparted for you do resize your HD though!!!  :-k

---

