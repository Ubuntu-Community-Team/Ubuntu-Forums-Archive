---
title: "asus onboard raid w/wine"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by bjstabio on 2008-02-14
I'm building a new Linux box with an ASUS M2N-SLI Deluxe motherboard.  I'd like to use some of the onboard features, like RAID, but it appears they will only work with Windows.  Can I use Wine to utilize some of these features?  Thanks for any advise you can give.

---

### Post by aeiah on 2008-02-14
it will probably be easier to use native linux software raid. it should also be more efficient in terms of speed and reliability.

either way, you wont be able to install ubuntu onto the raid, it will have to be on a different hard drive (i think)

---

### Post by pcjunkie on 2008-02-16
I just built 2 (One a file server) using the same mobo on both. I can state quite honestly its a blazingly fast platform.

AMD 6000+ 64 (duel)
Asus M2N SLI delux. (M2N E (non SLI had sold out, such a shame. ;)
2 GB Generic RAM @1066)
ASUS 8400GS (256) 

I have not been able to configure the RAID as yet, need more reading time. I have it set to boot from sda1 an 80 gb partition with space to grow and upgrade to and a dedicated Boot Partition.

The RAID drives are 2 500 gb drives set to mirror.

The setup was very responsive and Compiz / emerald  worked without problems. 
The boot setup allocates the drive to boot from and after that all works well. Linux did see the RAID drives and as 2 seperate drives which according to the BIOS is incorrect as I had them already in a RAID 1 setup but this could be overcome with Linux after further reading. 

A similar setup with 1 HDD and an 8600 GT (512) was smashingly fast. For what this platform costs (+/- AU$900) I am impressed. (2 Years ago one could pay around 1800 AU using the same "middle road" hardware)

Only thing not tested was Sound...
All else worked without errors apart from the RAID issue....yet to be solved ATM

[https://wiki.ubuntu.com/ASUS_M2N-E_NVIDIA_nForce%C2%AE_570_Ultra%E2%84%A2_MCP](https://wiki.ubuntu.com/ASUS_M2N-E_NVIDIA_nForce%C2%AE_570_Ultra%E2%84%A2_MCP)

I can say Ubuntu installed perfectly without a hitch and did so very quickly, If this platform is what you want then you won't be disappointed, Anything you click on provides almost "instant" response and Ubuntu performs very smoothly with Compiz and Emerald providing a very slick UI. (Even though it is a file, printer and backup server built to last 5 years or more, I did install Compiz quickly and gave some people a show of what Ubuntu and Compiz can do..)

---

