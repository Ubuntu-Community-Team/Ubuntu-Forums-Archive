---
title: "Install issues"
date: 2007-09-13
forum: Apple PPC Users
---

### Post by Lekter on 2007-09-13
Ok here we go.

I burned feisty PPC - check
Booted to it - check
Loads kernal - check

The first graphical Ubuntu LiveCD loading screen is rainbowed like 8 bit or something and stalls. I cant get past this. I've tried doing the following:

xmodule=nv
xserve=nv
live-nosplash

Nothing is working. Any suggestions would be greatly appreciated.

My system specs are as follows:
PowerMac G4 867 - 896 RAM - 32mb NV AGP video - OSX 10.4.10

---

### Post by Midwest-Linux on 2007-09-13
You certaintly have enough ram for the screen to work properly. Do you have another video output, if so try that one instead. I would use the text based alternate installer and make sure you burn it the slowest speed you can like 4X or 8X. This may or may not help you out, but worth a try. If it didn't work, there are some fine people here who can help.

---

### Post by Lekter on 2007-09-15
Thanks I'll certainly give the alternate a go. I was thinking that it may remedy the problem. However, I was also thinking that it may be the Nvidia video card. I read a few few posts that stated that drivers aren't supported or something to that regard. I do have an additional Video input but it is DVI and I cant seem to locate my DVI converter. I was able to burn it at 8x for a more stable burn with Disk Utility. Been quite awhile since I had burned at that speed. Forgot how slow it is.

If I get the Alternate up and running Ill be sure to drop a post here. Thanks for the tips.

---

### Post by Midwest-Linux on 2007-09-16
> **Lekter said:**
> Thanks I'll certainly give the alternate a go. I was thinking that it may remedy the problem. However, I was also thinking that it may be the Nvidia video card. I read a few few posts that stated that drivers aren't supported or something to that regard. I do have an additional Video input but it is DVI and I cant seem to locate my DVI converter. I was able to burn it at 8x for a more stable burn with Disk Utility. Been quite awhile since I had burned at that speed. Forgot how slow it is.

If I get the Alternate up and running Ill be sure to drop a post here. Thanks for the tips.

If you have two video cards, remove one of the cards. It might further help the installation and might draw less resource demands. See I had a major issue, my prob was different. I have a Mac G3 New World 400 Mhz 384 RAM. I had two video cards, when I had Mac 9.0 os on it...both cards would show the Mac 9 OS. but...when installing Ubuntu...only one card would work, and I had the monitor plugged into the the other card and I never got to even see the install menu...a week of countless posts here and hours and days of trouble shooting all boiled down to the monitor plugged into the wrong video card. 

So why did this happen? Both video cards were the same, both video cards were right next to each other on the pci slot, both showed Mac OS 9.0. The top video slot showed everything, which I think was the main card as the computer saw it. The second slot, was the extra video slot (as the computer saw it) even though both cards were the same. So the computer used the first top slot as the main video out and only through the main (top first card) can you view the mac firmware, the ubuntu install menu, and the install of the ubuntu. On the second slot the video instead went white and then black on the monitor and then showed nothing (because in all likelyhood the computer only saw the first video card during the install) but yet was able to see the Mac OS 9.0. 

I will keep posting this from time to time to save everyone the hassles that I went through. Such a simple solution for a big problem. one more tip, if you are still having issues...check the battery..its a 3.6 Lithium...you might have to do a special order on it or go to a specialty shop, and no you cannot use the 3 volt from Radio Shack or Walgreens, it has to be a 3.6 lithium and has to be the same size.  Its not that expensive (under $10.00) and also might be the reason why you might have difficulty installing Ubuntu. But that should be the final reason. if you are using the alternate text installer, your battery is good, have it plugged into the right video card, and have at least a Mac 9.0 firmware...you should be good to go. 

(On a side note, stick with Ubuntu alternate text installer. Don't try Yellowdog 5.0 as it will not work with the G3 Mac. I downloaded six ISO's, burned six ISO's at 4 X, spent two hours installing it to the G3, spend another hour reinstalling it and it never installed and never showed up at the Mac boot firmware...stick with Ubuntu 7.04 PPC alternate text installer...you will be glad you did)

 The best things about the Mac G3 is that it is built solid, its the easiest of any computer made to get into the inside. And it uses common inexpensive PC 100 SDRAM DIMM Ram. 

Moderators, could someone put this in the sticky section for installing/troubleshooting MAC PPC? Thanks

---

### Post by stmiller on 2007-09-16
The Ubuntu Live CD seems to only work on recent Powerbooks, iBooks, and Minis. The alternative CD is the only way, for most.

---

### Post by Radim on 2007-09-17
Hi Lekter, I've got exactly the same Mac (G4 867MHz, 1GB RAM, same video card). I wonder, have you been able to install Ubuntu 7.04 from the alternative CD?

The latest version of Ubuntu I was able to install was 5.10, after that I was not able to install any of the newer version using both normal and alternative installation CD.

---

### Post by Lekter on 2007-09-17
> **Radim said:**
> Hi Lekter, I've got exactly the same Mac (G4 867MHz, 1GB RAM, same video card). I wonder, have you been able to install Ubuntu 7.04 from the alternative CD?

The latest version of Ubuntu I was able to install was 5.10, after that I was not able to install any of the newer version using both normal and alternative installation CD.

No I was not able to install with the Alt CD either. It simply goes black and the burner stops working just like the LiveCD. Im thinking its the lack of support for the Nvidia video cards on MAC. I know they work fine on PC as I used to run Fedora C2 years ago without any problems. Other then that I have no idea what could be halting the install at that point except for a display driver issue. I could be way off with that idea however.

Disappointing really, I honestly dont have much time to mess with this type of thing and it was more of a "treat" if you will, than anything else to play with Linux again. Unfortunately Ubuntu doesn't like what I have in my toy box.

---

### Post by Lekter on 2007-09-17
Midwest-Linux  

I only have the one card. It resides in my AGP slot.

---

