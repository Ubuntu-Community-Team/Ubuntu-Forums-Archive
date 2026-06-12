---
title: "Legacy chipset drivers"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Blue_Eagle on 2007-12-28
I recently decided that i would give linux a go after considering it for ages. However it will be on an old computer (like 6/7 years) and i dont know where i would go to get drivers. 
I believe that linux comes with graphics drivers (and they seem easy enough to find from nvidia or here, thanks to the search function) but i dunno about the chipset ones because it took me ages to find ones for windows and they were like sorta 1 sizes fits most for multiple chipsets.

Anyway, the mobo is an Asus A7V  KT133 rev 1.02, with a A7V ACPI bios.   (with a 900Mhz althon thunderbird, so it is socket A, i think?)

as i said, i found them for windows but will these work with linux? and where can i find linux ones if not?


thanks for your help in advance :)


p.s will it comes with sound drivers as well, because i have not a clue what card it has, i have looked through the control panel, dxdiag and physically inside the case and found nothing more specific than sound blaster PCI :( will it just be detected?
p.s.s lol: how hard is it likely to be to get it connected to the internet wirelessly? i will be using either a [d-link DWL-G122](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=172384) or a [Edimax EW-7128G](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=152539) will drivers for them come with ubuntu or will i need to get them somewhere else? and how much of it is automatic? like will i just be able to search for networks, select mine and enter the security details and go?

---

### Post by disturbed1 on 2007-12-28
Besides the wireless everything will work out of the box. You don't need to hunt drivers for your devices. Linux has **most** drivers built in. This includes chipset, IDE/SCSI/RAID, networking, usb, sound, graphics and just about everything else.

If you have an ATI or nVidia graphics card Ubuntu will prompt you with a choice to install the binary driver or continue to use the built in driver. This is the same as you having to go to nVidia's webiste, and finding, downloading, installing the driver in Windows. The built in driver(s) work great for most graphics cards, except ATI cards beyond the x1xxx series, they also lack 3d support for nVidia cards. All other chipsets (Intel, VIA, Matrox ....) work as expected.

Not sure at all about the wireless cards :(. I do know that some work with no fuss at all. Others just don't work period. Do a forum search for something like "netgear wireless" or what ever.


Best advice I can give is to put the disc in, and power the machine up. Post here, or in a new correctly titled thread describing the problem (if any) that crops up.

Welcome aboard :guitar:

---

### Post by Blue_Eagle on 2007-12-28
Ok cool, sound good. I am not too fussed about proformance because it is really only going to be used to basic stuff, no games or anything. I'll have a look for wireless threads (there seemed to be plenty lol)

thanks :)


p.s been looking for about 10mins and i am scared lol.....really complicated

---

### Post by CREEPING DEATH on 2007-12-28
Use 7.10/Gutsy, most of the wireless issues have ben fixed.

CD

---

### Post by Blue_Eagle on 2007-12-29
ok, well got ubuntu installed and it works ok on the stock drivers but it says if i want any 3D stuff or 2D acceleration i need extra drivers. So i grabbed them off the nvidia site (the linux ones) but am not sure how to install them lol. If i just double click it says that it doesnt recognise the coding and to check if it is binary lol.
If i double click and run in the therminal, it tells me to run it as root.......which i understand to be putting sudo before the command?   
but that didnt work either, it just says it cant open the file (i typed sudo sh <file name> dunno if that it right though)

So yea, any advice?

---

### Post by Sef on 2007-12-29
To install the restricted drivers in Ubuntu the easy way:

System > Administration > Restricted Drivers Management.

---

### Post by overdrank on 2007-12-29
> **Sef said:**
> To install the restricted drivers in Ubuntu the easy way:

System > Administration > Restricted Drivers Management.

+1  and what is the model of the nvidia card?

---

### Post by Blue_Eagle on 2007-12-29
Ok, tried that and there is a wee button to enable a driver but it gives this message:

"the software source for the package
nvidia-glx
is not enabled"

i assume that means the drivers it wants to enable are not installed?


It's a GeForce 2 MX400

---

### Post by overdrank on 2007-12-29
> **Blue_Eagle said:**
> Ok, tried that and there is a wee button to enable a driver but it gives this message:

"the software source for the package
nvidia-glx
is not enabled"

i assume that means the drivers it wants to enable are not installed?


It's a GeForce 2 MX400

Yes and I have not had good experience with this model. You can go to synaptic manager and search for nvidia-glx and install. I am not sure if that model will need the nvidia-glx-legacy instead. You can do a quick search of the forums and I am sure find some help. Good luck.

---

### Post by RomeReactor on 2007-12-29
Hi. Try opening Synaptic (System->Administration->Synaptic), go to "Settings->Repositories" and check all the cases in the first tab (except for "Source" and "CD-Rom"; close that window and, still in Synaptic, press the blue "Reload" button. Afterwards, close Synaptic and try the Restricted Drivers Manager again.

Just as a comment, hunting for drivers on websites is something you won't do much of in Ubuntu, with the notable exception of some wireless cards. Ubuntu will install any driver needed provided they are available in the repositories, which are huge pools of software where Ubuntu draws from. You can install practically any driver not installed or a vast amount of programs using the [package managers]("https://help.ubuntu.com/7.10/add-applications/C/index.html") built in: Add/Remove (Applications->Add/Remove), Synaptic (System->Administration->Synaptic), or from the terminal using apt-get or aptitude. More on software installation in the [community documentation]("https://help.ubuntu.com/community/InstallingSoftware") pages, [Ayisu's Psychocats page]("http://www.psychocats.net/ubuntu/installingsoftware") or [this site]("http://monkeyblog.org/ubuntu/installing/").

Welcome to the community!

---

### Post by Sef on 2007-12-29
> "the software source for the package
nvidia-glx
is not enabled"

Have you opened the Universe and Multiverse repositories?  If not, then Applications > Add/Remove > change the top right box to 'All Available Applications' > Search: NVidia > Click on "NVidia Bianary X.Org 'legacy' driver " (4th from the top) > Apply Changes > Apply > OK.  

Then Application > Accessories > Terminal

type in ```
sudo nvidia-glx-config enable
```


From Add/Remove:

> NVidia binary X.Org 'legacy' driver
NVIDIA binary XFree86 4.x/X.Org 'legacy' driver 
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server and supports the TNT, TNT2, TNT Ultra, GeForce, and GeForce2 chipsets. AGP, TV-out and flat panel displays are also supported.
This is the 'legacy' driver for older chipsets.
Unless your chipset is explicitly listed in the above paragraph, please use the nvidia-glx driver, which is much more up to date.
To enable the driver, run "sudo nvidia-glx-config enable".

Canonical Ltd. provides technical support and security updates for NVidia binary X.Org 'legacy' driver

---

### Post by Blue_Eagle on 2007-12-29
hmm..ok, i did stumble across that Nvidia binary X.org thing but now i cant enable it because after ticking the boxes in Synaptic, it says the list of applications is not up to date and that i should refresh it but that requires an internet connection (which it doesnt have) so i cant enable anything from there now :(


Also it doesnt say what your says (in the quote box) it instead says it "cannot be installed on my computer type (i386) Either the application requires special hardware features or the vendor decided not to support your computer"   

:(

---

### Post by Blue_Eagle on 2007-12-30
so is there a little box i can tick somewhere or soemthing to stop the automatic update request?

---

### Post by overdrank on 2007-12-30
> **Blue_Eagle said:**
> so is there a little box i can tick somewhere or soemthing to stop the automatic update request?

Yes you can turn off automatic updates under system, administration, software sources. The under the update tab. Good luck!

---

### Post by Blue_Eagle on 2007-12-30
hmm......that didnt seem to help, i still get the wee message wanting me to reload the list of available applications :(   surely it is possible to get rid of that message because it is preventing me installed anything from the add/remove section

---

### Post by overdrank on 2007-12-30
> **Blue_Eagle said:**
> hmm......that didnt seem to help, i still get the wee message wanting me to reload the list of available applications :(   surely it is possible to get rid of that message because it is preventing me installed anything from the add/remove section

Ok if you have changed or added things in synaptic then that is why it is telling you to refresh (reload) . Did you fix your internet connection?

---

### Post by Blue_Eagle on 2007-12-30
no, it doesnt have a wireless card atm, although i suppose i could borrow the one from this computer for testing (bit of a pain not having the internet to check stuff then as i cant really move it back and forth quickly) 

Can i just reset the stuff in Synaptic?

---

### Post by overdrank on 2007-12-30
> **Blue_Eagle said:**
> no, it doesnt have a wireless card atm, although i suppose i could borrow the one from this computer for testing (bit of a pain not having the internet to check stuff then as i cant really move it back and forth quickly) 

Can i just reset the stuff in Synaptic?

Yes I believe all you have to do is quit. Then it will ask you if you are sure.

---

### Post by Blue_Eagle on 2007-12-30
erm...lol, i did it yesterday so quit ages ago. Should i just reinstall for simplicity?

bw, for the wireless thing....i have a RaLink RT6 based card, can i follow [this](http://ubuntuforums.org/showthread.php?t=132980&highlight=RT6+wireless) guide, even though it was made ages ago and for breezy 5.10 when i am using 7.10?

---

### Post by overdrank on 2007-12-30
> **Blue_Eagle said:**
> erm...lol, i did it yesterday so quit ages ago. Should i just reinstall for simplicity?

Well if you reinstall without the internet I believe you will have the same issue's. I have seen several user's that install without internet that the repos are not enabled. So if you can hardwire the internet connection and then fix your repos I think things will work.

---

### Post by Blue_Eagle on 2007-12-30
right ok, might give that a try. I was just hoping to get it as operational as possible before giving it an internet connection (as i havent bought a new card for it yet)

---

