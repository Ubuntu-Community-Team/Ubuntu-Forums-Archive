---
title: "Help Bigbabydaddy get his NIC working if possible"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-03-14
So yesterday Bigbaddaddy finally got his dual boot partitions to work (XP/Ubuntu Dapper 6.06) but now there's the problem of his NIC not being recognized. If I understood it correctly, the interface is built into the motherboard. I also know that it's an Intel chipset, but after that, I'm not sure of anything else. Here is a screenshot as a result of looking at the hardware:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=27354&d=1173849245[/IMG]

I also tried locating a list of compatible hardware for him, to see if his particular harware was on the supported list, but couldn't find it. I'm thinking that he should probably just go out and buy a supported network card, but would like other's advice on this before he does this. 

If it should come to buying a stand alone card, which one should he get ? 

Regards, 

Doug

---

### Post by msaied on 2007-03-14
do you know your motherboard make and model number?

---

### Post by BigBabyDaddy1968 on 2007-03-14
I can find out in a few....

BTW, Sweet Spot went absolutely above and beyond the call of duty in helping me set up my comp.  Several hours spent on IM, here, and Mistric River trying to help what must surely be the most insane install ever....    Also, many thanks to all the community members here who offered advice, guidance, opinions, reassurance, as well as the random kick in ye olde pants.  :D

I'll see if I can find the info for you....

---

### Post by msaied on 2007-03-14
you can use HWiNFO for windows XP found in hwinfo.com it will show all your mobo details including model number .. 
also you can use The Intel Chipset Identification Utility fund in the first page of thir support section

---

### Post by jhenager on 2007-03-14
I have trouble with built in VIA nics. The strange 'fix' is to shut down completely, and pull the power cord for about ten seconds.
After restarting, the LAN interface is there. Otherwise, eth0 isn't present at all, similar to your output of ifconfig.
I do recall that my first excursion into Linux (Red Hat 6.2) warned that Linux doesn't always play nicely with the el-cheapo built in nics. I have found that 3Coms are very reliable, and autodeteted. There is a vendor on the net selling them for four to seven bucks.
[http://www.gearxs.com/gearxs/advanced_search_result.php?keywords=3C905-TX](http://www.gearxs.com/gearxs/advanced_search_result.php?keywords=3C905-TX)

---

### Post by BigBabyDaddy1968 on 2007-03-14
> **msaied said:**
> you can use HWiNFO for windows XP found in hwinfo.com it will show all your mobo details including model number .. 
also you can use The Intel Chipset Identification Utility fund in the first page of thir support section
Great utility!  Thaks for that.  Mobo model: Dell, Inc. OWG855; Mobo Chipset: Intel P965 (Broadwater-P) + 1CH8DH.

> **jhenager said:**
> I have trouble with built in VIA nics. The strange 'fix' is to shut down completely, and pull the power cord for about ten seconds.
After restarting, the LAN interface is there. Otherwise, eth0 isn't present at all, similar to your output of ifconfig.
I do recall that my first excursion into Linux (Red Hat 6.2) warned that Linux doesn't always play nicely with the el-cheapo built in nics. I have found that 3Coms are very reliable, and autodeteted. There is a vendor on the net selling them for four to seven bucks.
[http://www.gearxs.com/gearxs/advanced_search_result.php?keywords=3C905-TX](http://www.gearxs.com/gearxs/advanced_search_result.php?keywords=3C905-TX)
Thanks for that as well.  I did try the hard re-boot, but LAN interface did not show.  I'll check out that link, too.

I dunno how I'll ever be able to help anybody else 'round here.  I'm barely keeping my head above water.  Thanks again.

BBD

---

### Post by msaied on 2007-03-14
download and install the driver found here :
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=839&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=839&DwnldID=9180&strOSs=39&OSFullName=Linux*&lang=eng)

---

### Post by msaied on 2007-03-14
after downloading the driver, extract it and cd to the src directory and type:
sudo make 

then :
sudo make install

(im not sure that you will need a reboot .after this)

then load the module by:
sudo modprobe e1000

hope this works.

---

### Post by BigBabyDaddy1968 on 2007-03-14
Thanks!  (Google?)  I'll hafta try that when I get home from work.

---

### Post by Sweet Spot on 2007-03-14
> **msaied said:**
> after downloading the driver, extract it and cd to the src directory and type:
sudo make 

then :
sudo make install

(im not sure that you will need a reboot .after this)

then load the module by:
sudo modprobe e1000

hope this works.

Great stuff guys, thanks ! I'm going to have to say though, that the above instructions may look like Sanscrit to BBD. I personally understand about 98% of it. The part I don't get is the beginning: "cd to the src directory".  What does that mean exactly ? I'm assuming you have to be in that directory in order to run the terminal from it though, right ?

---

### Post by Sweet Spot on 2007-03-15
Bump for the cd to src directory. I downloaded the driver myself just to look at it, and see the src dir. So, what is it exactly that he has to do ?  In layman's please.

---

### Post by msaied on 2007-03-15
after extracting the driver  to a directory .. inside that directory you will fiend another directory called "src" to cd to a directory is to navigate to it in the terminal using the cd command . example: cd directory_name

he has to compile the driver by typing :  sudo make

then he can install the drivers by typing : sudo make install

then he need to load it by typing : sudo modprobe e1000

---

### Post by Sweet Spot on 2007-03-15
Ah, ok. Thanks for being patient and explaining that to us both. Every little bit of info helps for noobs such as ourselves, and that's why I love this community...very helpful. I thankfully haven't run into any driver issues, so obviously haven't had the experience of going through this stuff. And at this point, I'd know to research whatever I was buying if I was planning on using it with an Ubuntu system.  

Doug

---

### Post by msaied on 2007-03-15
Your welcomed Sweet Spot. I can say that 80% of what i know about Linux I learned it here in this forum,  and it's helpful community.

---

### Post by BigBabyDaddy1968 on 2007-03-15
And thanks from me as well, though I haven't had the chance to try those things out (found the driver, though, thanks to you).

---

