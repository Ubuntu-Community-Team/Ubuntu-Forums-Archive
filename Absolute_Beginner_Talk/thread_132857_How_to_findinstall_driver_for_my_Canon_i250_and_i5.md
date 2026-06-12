---
title: "How to find/install driver for my Canon i250 and i560 printer?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-02-19
Hi Everybody

I have been trying to connect my Canon i250 and i560 printers on my computers but cannot find an appropriate driver for the same on the install CD. It only comes up with Canon BJC printers which mine isn't?

Is there somewhere else that I should be looking at?

I desperately need help!!!!!!!!!!!


Best regards


Deepak Agarwal

---

### Post by el3ktro on 2006-02-19
Take a look at linuxprinting.org, on the left there's a link to the driver database!

Tom

---

### Post by hanspb on 2006-02-19
I don't know about these specific printers, but I have an i550, which I use with the BJC-7000 driver, with pretty good results. Photo quality is not as good as under Windows, though, and there is no warning when you get low on ink and so on. I guess you could just try different BJC drivers and see what works for you.
Hope this helps.

---

### Post by Klaidas on 2006-02-19
I have Canon i250 too. I have searched the canon website, I have read the manual, searched linuxprinting.org with no results so far :/

---

### Post by dvarsam on 2006-02-19
I (also) have a Canon i550 & installed the "BJC-7100", but the Photo quality is NOT good.

I found a site for Canon Printer Drivers, although I have not tested:


        [http://www.leenooks.com/i550](http://www.leenooks.com/i550)

	[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

The Drives for the Printer i550 should be the following:

	bjfilterpixus550i-2.2-1.i386.rpm

Since this is an ".rpm" file you should be able to use the program "alien" (download it from Synaptic), to convert the ".rpm" file to a ".deb" one.

I have NOT yet tried this, because I am trying other stuff.

However if you try it & make it work, please inform me.

Thanks.

---

### Post by 15index on 2006-02-19
Hi,

I am new but if these are 4 cartridge printers, the S800 drivers should work okay. You have to set the dpi for 600 x 600 for good quality print. When you pick a driver to try, look below the window and see if it compatible with the Gimp. These drivers will give the best results after a little trial and error. I am using a Cannon i550 with the S800 at 600 x 600 dpi and I like the results.

The drivers mentioned in the one reply are used with the CUPS system which I believe is for Servers only and will not work with a desktop/ laptop only system. It does give one heck of a good quality test print. It does not have the US standrad letter format, so if you try to print an Open Office letter you typed, it will start to print about six inches down the page.

---

### Post by agarwaldvk on 2006-02-19
Hi Everyone

Thanks for all your replies.

My reputation of being an ABSOLUTE novice is here coming to the fore.

Yes, this printer of mine (i560 from Canon) does have 4 printer cartridges.

For starters, what is GIMP and what is CUPS.

My intent is to use this thing on Ubuntu at home using a simple desktop -  no laptops either.

And say if I pick up the driver that you mentioned on your reply (15Index), then do I need these GIMP and CUPS bit?


Best regards


Deepak Agarwal

---

### Post by 15index on 2006-02-19
Hi,

When you add a new printer and choose the S800 driver, everything will be okay automatically. I am using a desktop system only. The Gimp is for Image Editing. You can find information on CUPS somewhere else on the forum. I hate to be vague, but since I don't have to use a server, I am not worried about what doesn't work.

I know this driver, S800, works. That is through trial and error.

---

### Post by agarwaldvk on 2006-02-19
15Index

But don't I have to download this driver (S800) or would it be available on the install cd for Ubuntu Hoary?

Sorry for being so ignorant but hopefully I will get there sooner or later!


Best regards


Deepak Agarwal

---

### Post by dvarsam on 2006-02-19
[QUOTE=agarwaldvk]15Index

But don't I have to download this driver (S800) or would it be available on the install cd for Ubuntu Hoary?


Response:

From the Menu, select: "System\Administration\Printing"

A window will come up:

Double-click on the "New Printer" icon.

Then select from the List of Printer Drivers the "S800".

Then follow on the Wizard.

There is nothing that you have to download from the Internet.

The drivers are inside somewhere in your Ubuntu & after you specify which Drivers you want to install, they will get installed automatically.

I hope I helped a bit.

---

### Post by agarwaldvk on 2006-02-19
dvarsam

I am sure it will!

I will try that at home tonight!

And thanks to all of you who have borne with my ignorance on the matter!

Best regards


Deepak Agarwal

---

### Post by agarwaldvk on 2006-02-20
dvarsam

I did install S800 driver for my Canon i560 and it works ok! I haven't tested it for  pictures but I am not in to printing photos anyhow. Text is fine.

Thanks a lot for all  your  help guys, appreciated most sincerely.


Best regards


Deepak Agarwal

---

### Post by dvarsam on 2006-02-20
I tried to use the S800 driver for my Canon i550 & text is fine.

But the problem is NOT the text.

Printing Text is fine - even if you install other Canon drivers for your Canon Printers...

The problem is with printing Pictures!

With the S800 driver (set to 600x600 dpi) I still do NOT get Good Color Quality, for my i550.

It just prints photos, as if I selected a "Draft" Print (the worse quality & fastest possible print)...

So, can anybody suggest other Drivers for the Canon i550 or i560 or generally the "i" series Printers - that can print Photo's with Good Quality Results?

---

### Post by CameronCalver on 2006-03-22
yeah i also have a i550 and i have heard that the bjc7000 is good i havent tested but have a try and tell me what u rekon

---

### Post by dvarsam on 2006-03-23
[QUOTE=CameronCalver]yeah i also have a i550 and i have heard that the bjc7000 is good i havent tested but have a try and tell me what u rekon[/QUOTE]

I think I have already tried that too!

bjc7000 & bjc 7100 - unfortunately nothing makes pictures print fine...

How about you, did you get any results out of those?

Try them out & tell us...

---

### Post by martbd on 2006-08-03
Printer Works Hooray :D :D

---

### Post by mwob on 2006-08-04
Did you ever get your i250 working? I gave up after trying various routes, it was going nowhere :(

---

### Post by soonindallas on 2006-08-04
I print to an i560 using cups and the BJ7000 driver over samba to the printer hooked to a WinXP box and text is OKish.  Colour is not great and I don't print pictures, but basic printing of text is draft quality.

---

### Post by kurniawands on 2006-08-04
> **mwob said:**
> Did you ever get your i250 working? I gave up after trying various routes, it was going nowhere :(

get the driver from [www.canon.co.nz](www.canon.co.nz)

they have i250 and i255 linux driver (on tar.gz and .rpm format) or i can send you both the drivers if you have a limited internet connection. (pm me your email address for that)

but, unfortunately, you might need some hardwork to make the printer works.

installation guide mode is on :D 

---------------------------------------------------------------------------

there will be 2 files (bjfiltercups_2.3-1_i386.rpm and bjfilteri250_2.3-1_i386.rpm)

1. convert both .rpm files to .deb using ***sudo alien filename.rpm***

2. do ***sudo dpkg -i bjfilteri250_2.3-1_i386.deb***

3. do ***sudo dpkg -i bjfiltercups_2.3-1_i386.deb***

4. here is the hard work !!!! hehehehehe:

   a. do ***ldd /usr/local/bin/bjfilteri255*** and see what is missing.

   b. missing files are actually there with different names, so open
      your synaptic and look for something close to the missing file.
      i.e. ***libpng12.so.**0* for ***libpng.so.2***

   c. now, link those looks alike file with the missing files........
      ***cd /usr/lib***
      ***sudo ln -s libpng12.so.0 libpng.so.2***

   d. do b & c step for other missing files till all missing files are
      linked.

   e. is that all ? no, we're still half of the way, hehehehe.........
      now do ***dpkg-deb -c bjfilteri255_2.3-1_i386.deb***,
      _see /usr/local/bin sections_,
      do a, b & c step over again to those files (which writen on that)
      i.e. */usr/local/bin/bjcmdi255*.

   f. if e step is finished, do ***dpkg-deb -c bjfiltercups_2.3-1_i386.deb***
      and do a,b & c step once more. (see e step for comparation)

   g. now open a browser and go to [http://localhost:631](http://localhost:631) then
      click printers > add printer.

   h. fill in the data, continue...

   i. device: USB Printer #1 (Canon i250)
      make: Canon
      model: Canon i250 ver.2.3 (en)

   j. DONE !!!!! :D  now print a test page.....

------------------------------------------------------------------------
installation guide mode is off.

hope this can help you all. guide written above is also made for i255 using i255 driver....:D

* *tutorial is translated from other laguage on the other site*.

---

### Post by benmoreassynt on 2006-08-04
> **agarwaldvk said:**
> Hi Everybody

I have been trying to connect my Canon i250 and i560 printers on my computers but cannot find an appropriate driver for the same on the install CD. It only comes up with Canon BJC printers which mine isn't?



There is a website that provides a lot of Canon drivers, with easy installation instructions which mean you do not need to understand CUPS and all that stuff.

It is [www.turboprint.de/english.html](www.turboprint.de/english.html)

The one catch is that you have to pay a small fee for the driver and software. I paid (for a Canon Multipass printer), and the printer works 100% perfectly, no dodgy pictures or wierdness. It is the only thing I've ever needed to pay for with Ubuntu, so I reckoned it was a small price to pay.

---

### Post by kurniawands on 2006-08-04
> **benmoreassynt said:**
> There is a website that provides a lot of Canon drivers, with easy installation instructions which mean you do not need to understand CUPS and all that stuff.

It is [www.turboprint.de/english.html](www.turboprint.de/english.html)

The one catch is that you have to pay a small fee for the driver and software. I paid (for a Canon Multipass printer), and the printer works 100% perfectly, no dodgy pictures or wierdness. It is the only thing I've ever needed to pay for with Ubuntu, so I reckoned it was a small price to pay.

yes and it'll cost you US$ 39. i can buy a new printer with that money. ;)

---

### Post by benmoreassynt on 2006-08-05
> **kurniawands said:**
> yes and it'll cost you US$ 39. i can buy a new printer with that money. ;)

Yeah, fair enough. I guess it depends on how much you value your own time. In other words, I could probably earn more than $39 in the time it can take to find a driver and get it working. But I appreciate that there is always a free [in both sense] option.

---

### Post by kurniawands on 2006-08-06
> **benmoreassynt said:**
> Yeah, fair enough. I guess it depends on how much you value your own time. In other words, I could probably earn more than $39 in the time it can take to find a driver and get it working. But I appreciate that there is always a free [in both sense] option.

:) heeeehehe... yup, you're 100% right. wish i can do the same thing... money is always become problem here, since i live in a country that appreciate diploma lot more than skill...:(

---

### Post by mwob on 2006-08-09
> **kurniawands said:**
> get the driver from [www.canon.co.nz](www.canon.co.nz)

they have i250 and i255 linux driver (on tar.gz and .rpm format) or i can send you both the drivers if you have a limited internet connection. (pm me your email address for that)

but, unfortunately, you might need some hardwork to make the printer works.

installation guide mode is on :D ...


Thanks very much! I'll try that soon and let you know how it goes. I might have to "clean up" a bit from my old attempts.... but that should be easy enough!

---

### Post by mwob on 2006-08-12
Unfourtunately, that howto won't work :( When I try to install the bjfilter driver .deb file I get:

dpkg: error processing bjfilteri250_2.3-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bjfilteri250_2.3-1_i386.deb


And also this folder does not exist...

ldd /usr/local/bin/bjfilteri255

Any ideas?

---

### Post by mwob on 2006-08-12
Correction, the missing file error was caused by me installing the wrong file - the file i d/l'd was "bjfilteri250_2.3-0_i386.deb", not "bjfilteri250_2.3-1_i386.deb"!

I'll try again!!!

---

### Post by mwob on 2006-08-13
Hi,

The output of the ldd command tells me this:

~$ ldd /usr/local/bin/bjfilteri250

        linux-gate.so.1 =>  (0xffffe000)
        libcnbpcmcm180.so => /usr/lib/libcnbpcmcm180.so (0xb7f16000)
        libcnbpess180.so => /usr/lib/libcnbpess180.so (0xb7ee2000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ebf000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ebc000)
        libtiff.so.3 => /usr/lib/libtiff.so.3 (0xb7e79000)
        libpng.so.2 => /usr/lib/libpng.so.2 (0xb7e56000)
        libcnbpcnclapi180.so => /usr/lib/libcnbpcnclapi180.so (0xb7e4b000)
        libcnbpcnclbjcmd180.so => /usr/lib/libcnbpcnclbjcmd180.so (0xb7e46000)
        libcnbpcnclui180.so => /usr/lib/libcnbpcnclui180.so (0xb7e40000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d11000)
        /lib/ld-linux.so.2 (0xb7f33000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7cf2000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7cde000)


I don't know from that info what I am supposed to do next - can you be more specific please?

---

