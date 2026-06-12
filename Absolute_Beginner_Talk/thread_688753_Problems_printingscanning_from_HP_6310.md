---
title: "Problems printing/scanning from HP 6310"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jbrown96 on 2008-02-05
I convinced my dad to use Ubuntu, and I have everything except printing working great. He has a HP 6310 all-in-one. HPLIP detects and installs the printer just fine. He can print fine from OpenOffice Writer. However, he is having problems printing photos and scanning. 

The first problem comes from the programs used to print. Some of them work but most do not. I had him try gThumb, which seems very easy to use, but it won't print. It freezes every time he tries to print. I found that the Gutsy version (2.10.6) of gThumb can freeze when printing. I downloaded a new version 2.10.8, but that doesn't solve the problem. I have had him try several different programs (Digikam, Picasa, F-spot, and maybe a few others - I don't remember). The only way that I have been able to print photos that works is to download from his camera (Linux doesn't support xD cards, so he can't use his card reader) using Digikam and print them using Picasa.

This leads to the second problem. Photos take forever to print. I think this may be a driver program. I think the problem is the amount of data being sent to the printer. Printing four photos on one page was 186MB, according to the printer queue. Is there a way to speed up printing? A better driver, perhaps?

The third problem relates to scanning. Xsane works fine, but my dad finds that too complicated. I found "scan2pdf" in the repos. He really liked how easy it is to use. However, I had to reinstall the printer (deleted it and reinstalled in the system->admin->printing). Now the program keeps giving an error that no scanner is found. Xsane still works, and he is using it in the meantime. I

Could someone please help, espcially with the photo printing. Why would so many programs be completely unable to print? Are there any other suggestions on a very simple photo program? My dad only needs something to import them and select the layout for printing.

I really need some help with this. I installed Ubuntu over Christmas break and have since gone back to school. I can remote desktop into his computer, but that's only helpful if we can fix the problem using Ubuntu. I really don't want to help my dad with Windows... *shudders*

---

### Post by BruisedQuasar07 on 2008-02-06
When I first installed Ubuntu 7.04 and Xubuntu 7.04 on an old laptop,
 I got Xsane working my HP psc 1315 scanner immediately. I was very
 impressed as Xsane was ready to use much quicker and did better scans
 than my HP software did in Win XP. Printing was a different matter.

For some odd reason, I had to remove & reinstall the Cups driver everytime
 I rebooted Ubuntu! The printing system box reported my printer was "ready"
but it would not print. I would check it out and got "1 job", stopped!

I did not shut down my PC for weeks so I did not have to go through a routine
to get printing. Then, I got some fundamental updates that required reboot.
I noticed my printing still worked! Recently, I noticed I can reboot and still
print. Then, yesterday I printed one page. Altered it a little (all with ABIWORD).
The printer settings looked fine but no matter what I did no printing. Then,
I entered another user account and printing returned. I re-entered the user
account that stopped printing and printing was back!

My tentative conclusion is that printing with the Cups utility is unstable with 
some HP printers. Two months ago I bought a budget, older tech HP D2345, 
set it up in a few seconds on my IBM Thinkpad laptop powered by Xubuntu. 
And have absolutely no problems. 

I had a lot of problems with the HP utility you are using. I suspect it does not
handle All-In-One HP printers well. Despite warnings it probably would not my
Cups Driver works my 1315 scanner!

---

