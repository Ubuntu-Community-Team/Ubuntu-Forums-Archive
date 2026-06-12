---
title: "Installing wine complications"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by simon_shaft on 2007-03-18
configure: WARNING: X development files not found. Wine will be built without
configure: WARNING: X support, which currently does not work, and probably
configure: WARNING: isn't what you want anyway. You will need to install devel
configure: WARNING: packages of Xlib/Xfree86 at the very least.

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:

configure: WARNING: Your system appears to have the FreeType 2 runtime libraries
configure: WARNING: installed, but 'freetype-config' is not in your PATH. Install
configure: WARNING: the freetype-devel package (or its equivalent on your distribution)
configure: WARNING: to enable Wine to use TrueType fonts.

configure: WARNING: FontForge is missing.
configure: WARNING: Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished. Do 'make depend && make' to compile Wine.

Install the X development headers and try again.
_____________________
Okay, can anyone tell me what is this?
I managed to came up to this script after LOADS of packages installed manually. Maybe I'm goin to be cr4zy after this lol...
And I don't have any internet connection in Ubuntu, Im a M$ Win background kid. Only have internet connection in M$ Win.

---

### Post by eljalill on 2007-03-18
Hello!

Your error message means, that wine needs packages that re not on your computer. You can search for them on synaptic. They seem to be the xlibs.dev  and fontforge and maybe x11proto-gl-dev.

However, if you don't need to recompile because you are using a patch or so, it might be easiest to install all of wine through synaptics. You will get the newest version if you edit your sources.list and add 
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main .

But of course for this it would be better to have an internet connection...
So maybe you would want to fix that first?

---

### Post by simon_shaft on 2007-03-18
I'm afraid it might not be possible since my modem's driver only supports M$ Win All. Yes, no Linux :(
OR is there any alternatives so that I can install my modem driver into linux and use it to download the package?

---

### Post by eljalill on 2007-03-18
What Modem do you have?

---

### Post by simon_shaft on 2007-03-18
Aztech DSL 206U USB modem. If I can install this, it means that I can go to the internet and install wine. Cool hypotesis, though I dont know wether it'll work or no

[http://www.aztech.com.sg/prod_adsl_dsl206u.html](http://www.aztech.com.sg/prod_adsl_dsl206u.html)
EDIT: OMFG! WTF was that??!! THe install CD told me that It supports M$ Win ALL but the internet said it supports ALL.

---

### Post by eljalill on 2007-03-18
Well, the manufacturer says, that the modem is compatible with Linux... I have not found Linux drivers on their website, but since they use the Eagle chipset, you should be able to get it working with the eagle-usb packages.

If you still need help with this, let it be known.. But maybe under another thread, so that more people see, what this it about ;) .

---

### Post by AtrejuT on 2007-03-18
well your modem seems to use the eagle chipset and there seems to be a driver developed for usb modems based on that chipset.
maybe you want to have a look around here:
[http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport](http://faq.eagle-usb.org/wakka.php?wiki=ModemSupport)
their list does not contain your modem (I think) but since it is the same chipset you might still have a chance.

If you can find drivers from the manufacturer than that's even better, I guess.

good luck, and if you run into problems just post

atreju

---

### Post by simon_shaft on 2007-03-18
I do saw the Eagle chipset package in the Synaptic b4. Thus, does this means that if I install the package (thru the installer CD) I would be able to use my modem. Izit rite?

---

### Post by eljalill on 2007-03-18
Well, it is definetely something to try!
Since it doesn't hurt to install, just do and if it doesn't work, ask again!

---

### Post by david_kt on 2007-03-18
Instead of using the source and compile it, just download the package here:

For edgy:
[http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb)

For dapper:
[http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.32~winehq0~ubuntu~6.06-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.32~winehq0~ubuntu~6.06-1_i386.deb)

Choose the one according to ubuntu version you are using. After you donwload it (from any other computer), copy it to your ubuntu computer, and double click the file. It will install wine automatically. Unless it complain some dependency issue (it is unlikely).


Regards,
DK

---

### Post by simon_shaft on 2007-03-18
Thanks to david_kt , I managed to install WINE!! Just after installed some dependencies. But now my modem wont install. Take a look at that 
[IMG][IMG]http://i125.photobucket.com/albums/p57/simon_shaft/Screenshot-1.png[/IMG][/IMG]

---

### Post by david_kt on 2007-03-19
Did you try to install modem driver using wine? I doubt it will work at the moment. Wine is just to facilitate windows program to run on linux, but not to improve linux performance itself. If you want install your modem in linux, you should look for a way other than using wine (imo).

Regards,
DK

---

### Post by simon_shaft on 2007-03-21
Im afraid Im using wine to install this thing. Its the modem driver. Thus, does this means: My modem driver wont be alive in Linux? What a pity...

---

### Post by david_kt on 2007-03-23
I check your modem is not supported:
[http://www.aztech.com/support_download_broadband.html](http://www.aztech.com/support_download_broadband.html)

Only DSL Turbo DSL208U is supported. But if you want, you could try your luck by using this driver, although mostlikely it will not work.

[ftp://ftp.aztech.com/download/adsl/DSL208U/Linux.zip](ftp://ftp.aztech.com/download/adsl/DSL208U/Linux.zip)

DK

---

