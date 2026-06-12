---
title: "cd/dvd for full (non image) disk"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by yatesDELTA on 2006-02-28
okay then i was going to use nero to burn my ubunto disk however my nero trial is all weird so im going to download a program called cheeta burner. however there is one that has a dvd and one that doesnt on it. im only only going to download the necasery one so which?
do i need DVD or not?

thanks inadvance, alex

---

### Post by Kapre on 2006-02-28
[QUOTE=yatesDELTA]okay then i was going to use nero to burn my ubunto disk however my nero trial is all weird so im going to download a program called cheeta burner. however there is one that has a dvd and one that doesnt on it. im only only going to download the necasery one so which?
do i need DVD or not?

thanks inadvance, alex[/QUOTE]

yatesDelta - would suggest to d/l the DVD because it has the livecd and the installer (all in one). If you get it to d/l and burn it onto a DVD you can try it out first then if you liked it, you can do a full install (which you already have coz you got the DVD version)

K

---

### Post by ddt on 2006-02-28
I am using Ubuntu under VMWare, and I was trying to add the samba package, when it said, "Please insert the <Breezy cdrom name- i forget exact> into /cdrom".  I don't have the CDROM, just the Ubuntu application from the VMWare site.  Is there a way I can do the installation without having to burn a CD?  I picked Ubuntu because I'm familiar with Debian, btw.

Thank you!

        =-ddt->

(I was the guy who ported Doom, Quake, and Abuse to Linux, btw)

---

### Post by Qrk on 2006-02-28
Yes, you should be able to:

```
sudo gedit /etc/apt/sources.list
```

Comment out the lines that refer to the cd (add # in front of them) or delete them entirely. 

Then you can install samba via synaptic or apt-get, whichever you choose. It will download the package from the online repositories.

(I havent tried vmware, but it shouldn't make a difference)

---

