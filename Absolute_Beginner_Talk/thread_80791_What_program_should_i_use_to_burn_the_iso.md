---
title: "What program should i use to burn the iso"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by brutaldrummer on 2005-10-23
I burned a copy of the live cd and the install cd using nero, i clicked "File > burn image" and burned it.

The cd doesn't boot. I tried it in my newest computer, then I tried it in my alt computer. I've installed linux mepis and gentoo using my alt computer before. So it's capable of booting from the cd rom. It must be the cd, what program should i use to burn the .iso ?:confused:

---

### Post by aysiu on 2005-10-23
Sounds as if it could be a bum ISO image if you've burned ISOs before. Do you know how to do checksums?

---

### Post by brutaldrummer on 2005-10-23
sounds familiar.... how do i do it?

---

### Post by aysiu on 2005-10-23
If you're using Windows:
[http://support.microsoft.com/default.aspx?scid=kb;en-us;841290](http://support.microsoft.com/default.aspx?scid=kb;en-us;841290)

If you're using Linux:
[http://ubuntuguide.org/#checkmd5](http://ubuntuguide.org/#checkmd5)

---

### Post by idn on 2005-10-23
Once you have the md5sum just right click on the ISO and select burn to CD...

Put a blank CD in and away you go, I love this feature so much.

---

### Post by patrick295767 on 2005-10-23
Still user of wine ... I use rather total commander to check some md5 and do several operations... 
  
Concerning burning ISO, k3b software is rather the best ! U'll be able to do it. I tried nero linux and the result: i couldnt burn dvd video 'cos it wasnt possible with the program (or maybe i didnt spend time enough)

Best regards, 

Patrick

---

### Post by brutaldrummer on 2005-10-24
[QUOTE=patrick295767]Still user of wine ... I use rather total commander to check some md5 and do several operations... 
  
Concerning burning ISO, k3b software is rather the best ! U'll be able to do it. I tried nero linux and the result: i couldnt burn dvd video 'cos it wasnt possible with the program (or maybe i didnt spend time enough)

Best regards, 

Patrick[/QUOTE]

I'm using nero on windows, not linux. I read the Checksums thing and i don't quite understand it. I'm guessing it checks for errors on the cd? or the iso file, either or I still do not thoroughly understand it.

---

### Post by LHZ on 2005-10-24
A checksum program takes a file, and calculates a value based on that file. For instance, a very simple checksum would be: "take the file as a binary number, and tell me whether it's even or odd". Real life checksum programs typically generate values that are pretty big, but fit on one line.

If you have a file whose integrity is critical (such as an ISO that needs burning, where a one bit difference can ruin the entire CD), you can calculate this checksum, and make the result public. Anyone who downloads the file can calculate the checksum of their downloaded file, and see if it matches. This is a good way to check if the file downloaded completely and correctly.

So in this case, you should calculate the checksum of the .iso file, and match it with the given checksum (I don't know where the given checksum is at the top of my head, but you can probably find it where you found the .iso download). If they are different, your download is corrupted, and you shoulddownload the file again. If they are the same, something else is wrong.

---

### Post by patrick295767 on 2005-10-24
[QUOTE=brutaldrummer]I'm using nero on windows, not linux. I read the Checksums thing and i don't quite understand it. I'm guessing it checks for errors on the cd? or the iso file, either or I still do not thoroughly understand it.[/QUOTE]
  
Hi,

--------------------
I tried to find out how to check a checksum in windows 
for free and very easily ...
  
Once u download the checksum file, just rename it as .sfv
(place it in the same folder of ur ISO file of ur linux CD)
  
Then install total commander from ghisler site :
[http://www.ghisler.com/](http://www.ghisler.com/)
(like mc under linux)
  
Then, click in the menu of total commander, Verify CRC !
  
and wait and see the results !
 
----------------------------------
Concerning ISO burning, if you burnt it with nero under windows, it should normally be well burnt. If you burn an ISO, the boot of the ISO should be present in the file and it'll result in a bootable CD without any problem. 
(u can check the boot of the cd with Winiso for instance (long but u can))
  
For instance, results are similar with K3b for linux...
   
So, sthg is wrong either in the burning or in the boot of ur pc maybe (try F11 - f12 or check in the bios maybe), or hardware prob ... or ISO corrupted or ... lot of possibilities ... 
    
I hope that'll help you a bit !!
 
Good courage and let us informed about ur progress !!
 
Best regards, 
 
Patrick

---

### Post by brutaldrummer on 2005-10-24
Ok I checked the iso and this is what i got using that program.

ubuntu-5.10-install-i386.sfv:

Errors: 0
OK: 0, not found: 0, read error: 0, wrong checksum: 0

Does that mean the disk is fine? I'm really confused. I've loaded linux gentoo, and linux mepis on my other computer but this disk won't run on this computer or my other one.

---

### Post by brutaldrummer on 2005-10-25
Ok so I pulled out the cd's that I thought I burned ubuntu on and looked at them, and noticed that they were even burned on. So I put it in my cd drive and explored them and there is nothing on them. I think I used my dvd burner to burn them instead of my other burner. Which might explain a lot of things. I'm burning them with my cd burner now.

---

