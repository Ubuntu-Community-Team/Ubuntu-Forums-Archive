---
title: "Can't Connect 2 Web,need eth1 !"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by guitronics on 2008-01-22
G.G. 7.10, AMD64. When installing to HDD,stops at 82% and "Is looking for security updates".

After much mucking about, Re-installing, giving up...reinstalling M$,this has been going on for almost a week,every day.

I check the "Wired Connection",check 'roaming', uncheck 'roaming',look up the troubleshooting files....

I have it set for DCHP,Ubuntu is looking for a connection on eth0....but my Vonage (Cable) router is putting the 'phone on (I think) eth0.

How do I get Ubuntu to look for an ethernet connection at eth1 ?

    Yeah, I'm a NooB:confused::confused:


              If I could just connect to the internet, I'd be able to use Linux!

                          As it stands now, I give up and re-install WinDoze....so I can connect.

                                                         HELP, PLEASE!

---

### Post by Nano Geek on 2008-01-22
Do you have more than one place to plug your internet cable in to your computer? 
If so, try plugging it into the other one.

---

### Post by mikeyphi on 2008-01-22
Confirm that you have 2 wired ethernet cards in your system?
If so - they should both show under System/Administration/Network, if so you should be able to select and setup the 2nd connection as required.

Most systems come equipped with one wired and one wireless connection

The other option is to disconnect your network cables whilst install Ubuntu - at the 'looking for security updates' phase the system will note the missing Internet connection and continue with the install!

What service is connected to eth0?

---

### Post by woknblues1 on 2008-01-22
from one to another ;)

anyways, after spending about 4 days worth of spare time, I figured out that I was not "right clicking" **_directly_** on the little orange triangle on my network launcher on the panel. Once I did that (yes, it took about 4 days to get it right), I connected again. That was really one of the worst weekends I have had in a long time.... I can laugh about it now though....

---

### Post by guitronics on 2008-01-23
Cable Modem,Vonage-supplied Linksys router.Telephone has two inputs (1 and 2) for two telephone lines.I have only one line, so Telephone uses "Telephone 1".

Three Computer ports...Computer plugged into computer port 1. Modem plugs into router.

I have no idea about Yellow triangle being "network connection" ...haven't seen that.

I have the ubuntu guidebook....not much information.

I'm sure if I plugged directly into the modem (bypassing the router)...it would work.

I don't want to do that, I need telephone service.

I saw during troubleshooting, the progress meter stops at 82%, and it looks only at 'eth0' .

Whatever I'm doing wrong, I'm sure others' are having the same problem...this is important.

Thanks ahead of time.

---

### Post by guitronics on 2008-01-23
PS: Not 2 wireless cards, no wireless. One wired card, only.

It works under windows.

---

### Post by mikeyphi on 2008-01-23
OK! First things first!!
If you are still trying to install Ubuntu - disconnect your network cables whilst installing Ubuntu - at the 'looking for security updates' phase the system will note the missing Internet connection and continue with the install!

After that we can look again at the Internet connection and the security updates!

---

### Post by guitronics on 2008-01-28
Thanks, MikeyPHI.

      After much thought and some reading,It came to me....Device Drivers! dll's! I'm in dll hell!

 My Motherboard has an  > M$ < compatible  installation disk (CD-Rom), and it has the drivers for the onboard sound,and N.I.C.!  [It's a Foxconn MX622 and a core duo celeron 64].

 And I also [now] understand that I need a working computer,internet connected;in order to make inquiries and discover tidbits of wisdom on the 'net.

 So: Before I go down the path to Ubuntu,I'll need another computer to run it on, and one to fall back on.

  I have the stuff to put together 3 'puters...I was gonna put Ubuntu on them anyways.....

  When the weekend comes, I'll be putting the hardware together.

         Thanks to one and all, you've been very helpful,and friendly.

                I'll be back, soon.

                                         Mike (guitronics).:guitar:

---

### Post by bumanie on 2008-01-28
I am aware of many people who had their install hang at 82%. If you wait 20-30 minutes it should continue with the install and the install should be fine.
With regards to internet connection, I suspect you are suffering the ipv6 problem, that many have had with gutsy. Once you have installed I would blacklist ipv6 and see if that allows you to connect. Try one of these two methods.
Method 1.
gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Method 2 (is to diable ipv6 in firefox)
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true
Hope this helps.

---

### Post by guitronics on 2008-02-02
Ahhhh....Now I'm beginning to understand the plausability of the IPv6 problem....

   I believe you're right on, bumanie! After some Googling, I came up with these links.....

  [http://ubuntuforums.org/showthread.php?t=202838](http://ubuntuforums.org/showthread.php?t=202838)  ,  and  [http://en.wikipedia.org/wiki/IPv6](http://en.wikipedia.org/wiki/IPv6)

                             The Wiki is quite lengthy, but after rolling it down a bit, it gives links to the problem right here on this forum!

          Thank you all, But I'm gonna wait until I assemble another 'puter,so I'll have this one to search for problems with.(Once bitten, twice shy).

                                                                   Thanks for your help.You folks are great.

                                     :guitar:

---

