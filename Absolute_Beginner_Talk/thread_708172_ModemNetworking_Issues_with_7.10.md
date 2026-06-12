---
title: "Modem/Networking Issues with 7.10"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Pwhdavey on 2008-02-26
Hey :KS

Just tested out and installed Gutsy Gibbon today as a dual-boot with Vista. Its a great OS. Although I'm dismayed to be having problems already.

Went into Network to set up a modem connection (I use a dial-up connection) and the three options there are invalid/white overlay/no colour. The space in the top of the window (drop-down menu) is empty. All I can do is run around blindly in "Properties", as although I've entered my dial-up details, "Okay" is invalid, as is everything else.

**Modem**: HDAUDIO Soft Data Fax Modem with Smart CP

I'm assuming this is Ubuntu itself, or some configuration I haven't set. The modem hasn't displayed incapabilities itself since obviously the system can't recognise the inactive Ethernet cable.

Thoughts?

---

### Post by spiderbatdad on 2008-02-26
[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

There are several methods outlined by the link above. I recommend gnome-ppp or kppp. Both are available for download through the repositories...though of course you would need access to a working connection. Both are also frontends to wvdial, which is installed by default.

You could try ```
wvdialconf
```then edit /etc/wvdial.conf from the terminal to include your username, password, and phone number. Then use ```
sudo wvdial
``` to connect.

---

### Post by Pwhdavey on 2008-02-26
Thanks... but if there is no option to download the drivers I am powerless to operate a network with which to actually download the features. What do you suggest I do?

My only option is to download the drivers via Windows Vista, slap them on a CD and load it onto Ubuntu. However, the download will be configured for Windows and may not work on Linux... and here we go again.

---

### Post by zvacet on 2008-02-26
> My only option is to download the drivers via Windows Vista, slap them on a CD and load it onto Ubuntu.

That is what you have to do.You will download linux drivers so it is irelevant which Os you are use to download it.

---

### Post by Zeotronic on 2008-02-26
While it may further complicate the process for you, I will point out that you could just read the files (after you download them of course) from the Windows hard drive, rather than writing them onto a disk.

---

### Post by Pwhdavey on 2008-02-26
> While it may further complicate the process for you, I will point out that you could just read the files (after you download them of course) from the Windows hard drive, rather than writing them onto a disk.

Maybe then, someone could guide me through that. I also have a USB flash drive... I'll actually transfer the stuff to that rather than wasting a blank disc.

---

### Post by Pwhdavey on 2008-02-26
Here is a screenshot of what I get when I open Administration>Network:

[http://img174.imageshack.us/my.php?image=screenshothd0.png](http://img174.imageshack.us/my.php?image=screenshothd0.png)

So what drivers exactly do I have to download from the site that came from spiderbatdad's link? I'm completely clueless at this.

---

### Post by spiderbatdad on 2008-02-26
That site was intended to show you the various ways of configuring dial-up. This link is the best source of dial-up support. [http://132.68.73.235/linmodems/index.html](http://132.68.73.235/linmodems/index.html)

You will want to download the scanModem.gz onto your flash drive and transfer it to Ubuntu. Then run the tool from your desktop, and read the files inside the folder it creates. They will tell you what needs to be done. But, first, have you tried running ```
sudo wvdialconf
```in a terminal just to see if you modem gets detected by wvdial?

Actually...it's small enough, so here it is:
Copy it to your desktop. Then right click on the package and choose extract here. A file named "scanModem.2008022545" will be created. Rename the file (this is important or it wont write the files you need.) Rename it simply: scanModem, dropping the date and period. Now open a terminal:```
cd Desktop
chmod a+x scanModem
./scanModem
```Pay attention to capitalization of the "M." Now read the files in the output folder: 1st read.txt and ModemData.txt.

---

### Post by Pwhdavey on 2008-02-27
Thanks :) I did all that.

The sudo command didn't detect a modem.

Your second code did not work either. Correct me if I'm wrong, but I pressed enter after each line break (i.e. after the "p" of Desktop, etc). And yes, I typed it all exactly. Don't get me wrong, I was still able to view all the files from that extraction (i.e. the .txt files).

Okay, so after that I went back into Network. I battled through the Properties of Modem Connection and finally managed to enter the *sufficient *details for it to show "Okay" which I clicked and followed instructions to enable a tick next to the box of that connection. 

After failing miserably to achieve a connection yet, I returned to Windows and was told that by ticking the box beside Modem Connections, it should begin to automatically connect. Of which, it didn't.

I am familiar with Windows networks, which, when you press Connect, a new window appears showing the progress of connecting (i.e. Dialing XXXXXXX...). Nothing happened Ubuntu which I suppose is ordinary, but no sign of any connecting was apparent. 

So, where do I go now?

---

### Post by nixeagle on 2008-02-27
Can we see the contents of the  1st read.txt and ModemData.txt.files please. I'm assuming that program ran well. Just pastebin the information somewhere and post links to the info. Thanks!

---

### Post by spiderbatdad on 2008-02-27
Yes everything ran as it was supposed to if scanModem produced a folder full of files for you...and you said it did. ModemData.txt and 1stread.txt should tell you pretty much everything you need to know. You can contact the linmodems site for a driver. You most likely need slmodemd, as well from synaptic. The catch is it is difficult to set up an internet connection without an internet connection. If you had, at least temporary access, you would probably be able to enable the restricted driver and slmodemd with a couple of clicks. I would stop trying to use pppoe. It is very good and has a lot of stability issues. That's the program packed in with network manager you keep trying to use. I would stick with wvdial for now until you can download the front end...gnome-ppp. You could also get gnome-ppp and transfer it to your desktop. Without gnome-ppp, you will need to edit /etc/wvdial.conf manually to include user information. But it looks like first you need a driver.

---

### Post by Pwhdavey on 2008-02-27
Okay... I transferred copies of several .txt files to Windows. If I were to paste all the content all here, it wouldn't do much justice, and I can't find different segments of the text to highlight and post here because Windows Notepad screws up these Linux files and makes them look all funky. See the link - it's impossible to navigate that unless I read it on Ubuntu.

[http://img256.imageshack.us/my.php?image=29007305ff8.jpg](http://img256.imageshack.us/my.php?image=29007305ff8.jpg)

Because my printer is an older model, more complications have arisen. It would involve even more work on my behalf to install the drivers and transfer it to Ubuntu, then extract them, configure them... :|

*Urge to give up on Ubuntu rising... rising... lowering if this work could be less self-automated...*

---

### Post by Pwhdavey on 2008-02-27
Re: Windows Notepad. Files have been opened in WordPad which makes them easier to follow... I will post snippets as I go along.

---

### Post by spiderbatdad on 2008-02-27
ModemData.txt should contain a section listing the needed driver:```
CLASS="Class 0703: 8086:2486"
NAME="Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller "
PORT="modem:1"
PCIDEV=8086:2486
SUBSYS=1014:0223
SUBven=1014
IRQ=11
IDENT=slmodemd
SLMODEMD_DEVICE=modem:1
CODECp=SIL27
Driver=snd-intel8x0m
SOFT=8086:2486.MC97
```

---

### Post by Pwhdavey on 2008-02-27
> ModemData.txt should contain a section listing the needed driver:
Code:

CLASS="Class 0703: 8086:2486"
NAME="Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller "
PORT="modem:1"
PCIDEV=8086:2486
SUBSYS=1014:0223
SUBven=1014
IRQ=11
IDENT=slmodemd
SLMODEMD_DEVICE=modem:1
CODECp=SIL27
Driver=snd-intel8x0m
SOFT=8086:2486.MC97



Yes. Now what? And I am not posting anymore information from the .txt files; it's irrelevant. I've e-mailed LinModems. I'm pretty *frustrated* (substituting that word for one more obscene) with this, so don't expect a friendly reception.

---

### Post by spiderbatdad on 2008-02-28
Do you have an option in the restricted drivers manager to enable a driver for this modem; shown in the screenshot below? Sorry, you're having such a tough go of it. Dial-up can be difficult to set up in linux unless you're a software engineer or at least have a working internet connection in the environment you're try to set up. Not sure you can enable the restricted drivers without internet...maybe someone else can offer better help.

---

### Post by Pwhdavey on 2008-02-28
Well, I may be able to have a working Internet connection in the environment I am trying to set one up in. My school has a wireless network. On Windows, it wasn't too difficult to configure the computer for this network. Of course, the computer technology person done it, who has had experience with all the other Windows computers. My networking details on the Compaq Presario V6412TU; for your reference:

```
High speed 56K modem, integrated 10/100 LAN, choice of 802.11b/g WLAN,
Intel® PRO/Wireless 3945ABG Network Connection or Intel® PRO/Wireless
3945ABG Network Connection & Bluetooth™
```

While I can enter the details and passphrase for this wireless connection, I remain adamant that something isn't going to work. Not only is a dial-up connection out of the question:

[LIST]
My printer, which works perfectly with Windows XP and would do on Vista if I had the drivers, appears "too old" to work with Ubuntu. 
[/LIST]
[LIST]
My graphics media accelerator is hardly given justice on Linux. Regardless of its capabilities I can hardly believe my eyes when, 3D Chess which works perfectly on Vista, won't run due to me graphics set on Ubuntu.
[/LIST]

I did my research. Everybody who was aware and helping me convert to Ubuntu knew perfectly well I used a dial-up connection as my primary network. No one stopped me. I found out about the Intel GMA 950 with relation to Ubuntu and there didn't to be any problems.

They all boast that Ubuntu is a free, affordable and powerful alternative to Windows. If so, then one would expect basic features like dial-up for some people without the necessary funds to purchase a cable connection to be perfectly compatible.

---

### Post by nixeagle on 2008-02-29
As far as the networking, Hang on and see if anyone can come up with some drivers for your modem. I tried looking, but I was stumped, then again this is not my main distro. I do know there is a modem project around here.

As far as the printer, it is probably not an issue of "too old" but an issue of nobody has bothered to write the drivers, yet. What kind of printer do you have? Can you give us specific brand and model number? I recall speaking on IRC looking something up but I can't remember what it was exactly. 

As far as your graphics card, can you elaborate on what kind of card it is? You probably can get drivers for that if/once you get the modem working. That was the case for me when I was running ubuntu a while back.

---

### Post by Pwhdavey on 2008-02-29
**Printer**: Canon MP110

**Graphics card**: the one and only Intel Graphics Media Accelerator 950

---

