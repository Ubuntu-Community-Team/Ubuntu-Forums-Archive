---
title: "Ubuntu hangs configuring network..."
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-26
I have installed wireless drivers with success but on restart the machie hangs indefinately at 'configuring network interfaces'. How do I remove the changes that cause this?

---

### Post by dddouglas on 2006-05-26
I have been having a similar problem. I will have wireless up and running at night and the next morning nothing. Then start the intall over get it it up then the next day no-go. I havent been going about it very Scientifically so I have yet to post my pains ](*,) ](*,) BTW where do I want to put my driver?

---

### Post by redistributer on 2006-05-26
use the fail safe mode upon bootup and remove the changes made to the network interface.

Consult the manufacture's website and see maybe if there is an updated driver you can download and install. 

If not you can find a wireless card that will support linux (any card with a realtek chipset)

---

### Post by mithion on 2006-07-02
I have the same problem.  I have a WMP54G wireless network card from linksys.  And it is the latest generation of the card, which I believe it to be the RT61 chipset.  I have had the strangest of problems I have seen so far.  The first time I installed dapper on my computer, everything went well.  No lock ups at boot, the network card was working fine.  Then, when the newest kernel came out, vs. 2.6.15-25 I believe, the problem started.  After the update, I rebooted my computer and then afterwords, the computer locked up at the "configuring network interface" step at boot up.  So I initally thought something wrong with the newer kernel, so I decided to reinstall from scratch.  Well now, I get the same problem with the original dapper install.  My computer locks up.  And what worries me is that I can't even boot in recovery mode since the same boot up routine is present for the safe mode.  Anybody have a solution?

---

### Post by Postino on 2006-07-02
I would like to add my two cents in...
I have a similar problem...
When I boot from Live CD on my second computer, it comes to 'Configuring network...' and it just hangs there.
The computer is an AMD 1.4GHz Athlon and it has a wireless networking card from d-link.

---

### Post by neveceral on 2006-07-03
Hi, i have the same problem with rt61, please look at [pages]("http://www.ubuntuforums.org/showthread.php?t=132980&page=9&highlight=rt61")  
9 and 10. I moved the old discussion here. 
I mean that the problem is DHCP, but i don't why?
Daniel

---

