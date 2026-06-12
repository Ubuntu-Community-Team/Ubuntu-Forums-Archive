---
title: "Dapper Modem Problem"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by tomos on 2006-06-02
I was able to install Dapper on my G4 powerbook.  But since I am forced to use dial-up, my soft modem is of no use to Dapper.  I also have a Zoom USB modem, and it did not work either.

Has anyone been able to make a dial-up modem work on a powerbook?

(I do have Breezy on a Cube, so I am not completely doing without.)


tomos

---

### Post by autocrosser on 2006-06-02
Well-your choices are limited, but there are choices--I'd bet your Zoom modem is a 3090 or newer--in other words, also a "softmodem".  I use a Zoom USB 2986L "hardmodem" & it connects regularly at 44,000 or better-- I've heard that the older Supra Express (SUP#2780) USB modems work also--You could cruise eBay for these & I find looking at  [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)  help me decide what I want to buy---You need to know that Linux support is often a couple of years behind OSX or Windoze--but I find that my computing experence has been enriched many times over by working with the Linux community--I just was involved with beta-testing Dapper & had a good hand in Breezy too--Hang in there & I think you will like the stay:-D

---

### Post by tomos on 2006-06-03
Thanks for the info and the encouragement, Dean.

My Zoom USB modem is a 2986 (no L).  Is there some configuring to make Ubuntu recognize a USB modem?  When I use Networking, I am afraid Ubuntu is looking toward my soft powerbook modem and of course, it finds no modem.



Thanks again
tomos

---

### Post by autocrosser on 2006-06-03
Good-I have a wvdial.conf that is optimised for that modem series--

#1--open a terminal and   sudo gedit <return> you will be asked for your password
#2--paste the contents of the wvdialconf.txt into your document
#3--look carefully--I've **** the areas you need to change for your ISP--make sure to delete the Phone3/Phone4 stuff you do not use
#4--Save the document to /etc/wvdial.conf (do not capitalize)
#5--After it is saved to /etc--then rename it to .wvdial.conf & save it to your home folder.
#6--Close gedit
#7--Now type wvdial & <returm>
#8--your should get a dialup from your modem

The important thing is that your modem is at /dev/ttyACMO (common for most all ACM USB Modems)

Good Luck & E me with problems!!!;)

Once you get the modem up regularly--download gnome-ppp & use it to connect--you can just gui your way thru, just remember /dev/ttyACM0

---

### Post by tomos on 2006-06-04
Great!  It works, Dean.  The only problem I have is that gnome-ppp disappears (without connecting) when I hit the connect button.  But that is minor compared to not having a connection.


Thanks again
tomos

---

### Post by autocrosser on 2006-06-04
Hummmm--When it comes up with the second text box, tick the log button & see what it outputs--Did you input the modem Init script with the Script button in the First text box? Glad it worked for you--I worked for quite a while to make that script](*,)

---

