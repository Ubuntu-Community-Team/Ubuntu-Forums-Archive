---
title: "Linux on Macbook Air"
date: 2011-05-19
forum: Apple Hardware Users
---

### Post by notsalty on 2011-05-19
I'm trying to dual boot Ubuntu with the Mac OS. The issue I keep running into is that the Live CD of Ubuntu cannot detect the hard drive during setup. It doesn't see anything? I've partitioned an extra drive in Bootcamp and it is also not detected by the Ubuntu installer. Can anyone point me in the right direction?

---

### Post by notsalty on 2011-05-21
I've answered my own question. It does not appear to be possible at this moment. Here's a website with the list of MAC's it does work on. You have to check your Macbook Air model first! 

 [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by rg4w on 2011-05-21
Great list. I hadn't come across that before.  Thanks.

---

### Post by ecspike on 2011-05-22
This one is a bit more up-to-date.

[https://help.ubuntu.com/community/MacBookAir](https://help.ubuntu.com/community/MacBookAir)

---

### Post by linuxinstalledfromhdd on 2011-05-22
Just curious, is there a list for PC like that page as well?  Would be really helpful.

---

### Post by notsalty on 2011-05-30
> **linuxinstalledfromhdd said:**
> Just curious, is there a list for PC like that page as well?  Would be really helpful.
I don't know. Sorry.

---

### Post by redil on 2011-06-16
The re: is very fitting. I am shopping around for hardware to replace my
Thinkpad X301 running Ubuntu. Until now I have only looked in the windows
department. But now I see, that standard Ubuntu distros also seem to 
work on Mac Hardware.

My current list of light laptops is: Samsung 900X3A, the Thinkpad X1 ... and
now the Macbook Air.

So my question is: would a MBA be an equal contender as far as software compatibility
goes, meaning that a MBA or an X1 or 900X3A could be used equally well with ubuntu?
Or are there certain aspects that need consideration that would not exist with BIOS/Intel 
hardware?

I would greatly appreciate some comments from folks running ubuntu on MBA.

thanks in advance

---

### Post by parananon on 2011-06-16
It works quite well as long as you do most of the things on [this]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") page.

---

### Post by frankbonatelli on 2011-06-19
Hey all
Just thought I would post that I have successfully installed UBUNTU 11.04 64bit os directly onto my 2010 11 mac book air.
Screen resolution was not right but restricted drivers fixed this
brightness buttons didn't work right but editing my xorg.config adding **Option          "RegistryDwords" "EnableBrightnessControl=1"**

The only issue now is the restart doesn't work. I must shut down for any needed reboot else it hangs.

Battery life is +/- 6 hours
Specs on Hardware
2010 Mac book air 11 inch
128g ssd
4g ram
1.4 core duo processor
no refit no mac os x
only UBUNTU 11.04 64 bit installed from there alternate disc using an external dvd drive.

---

### Post by redil on 2011-06-27
> **parananon said:**
> It works quite well as long as you do most of the things on [this]("https://help.ubuntu.com/community/MacBookAir3-2/Meerkat") page.

hmmm, what means "quite well"? Perhaps you could share what does NOT work?

suspend
sound
video
wireless
which keys do NOT work

anything else?

Do you think Ubuntu on macair runs as well as on BIOS based systems?

---

### Post by dfacto on 2011-07-28
Is applesmc needed for the new macbook air (MacBookAir4,2)?  Does it even support it?  There are some scary posts about the safety of linux on mac and I am wondering what, if any, precautions I can/should take.  From what I gather applesmc does this for Macbook Pro but it is not clear to me that it does anything for the MBA, particularly the new (2011) ones.

Thanks!

---

