---
title: "CD Integrity Check"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Mohammed Abbas on 2006-10-27
Hello there ,

I want start a clean Ubuntu (Edgy) installation . I downloaded the alternate CD , checked md5 hash and all went fine . 

Then , I moved into burning .. done ! I booted my PC with the new burned CD and selected "Check CD for defects" .. No errors with the physical surface .. but when it comes to integrity check , it showed there was error in some package when it was about 50-51%

I burned a new one with less speed this time .. did the check again , same error when the check reached 80-81% ..

*I was told on IRC this is a bug and don't do the check ...*

I'm really afraid about what will happen during installation with a defected CD ! but , in the same time , I won't spend all the time burning and checking CDs ..:confused: 

I seek your help ,
Regards

---

### Post by Drakkor on 2006-10-27
Hmmmmm.............why did you choose the alternate CD,even though,I guess it should be fine,but the desktop .i386 install was fine for me,md5s where fine,and CD defects were none,I"m running Edgy Eft right now.
Edit: clean install on hdd 2 !

---

### Post by rsk02 on 2006-10-27
I'm having the same problem but it also occurs during the install. I downloaded the amd64 alternate install cd because I am using a different boot manager and the standard install hoses the MBR. Well, install starts fine and then about 15-20 mins down the line it fails. The failing process is "Select and Install Software packages". At first I thought that this was because the install was trying to download packages over the net and the servers may have been overloaded. So I chose the option (becomes available after the failure) to reconfigure APT and disabled the download of packages. Still get the same error. The MD5 error is reported about 58% into the cd by the Ubuntu cd check also. I checked my downloaded ISO using the torrent (verified by seeding in Azureus) and no error. I am puzzled...
And "Edgy"less.....

Any help will be appreciated.

Thanks.

---

### Post by Mohammed Abbas on 2006-10-27
How's is a clean installation of 6.10 compared with upgrading to 6.10 from a 6.0.6 clean installation , then ?

I have to say this could be an option cause I don't have CD/DVD writer !

---

### Post by rsk02 on 2006-10-28
I would not risk an upgrade this early in the innings. I am doing a clean install because my upgrade from Hoary to Dapper had not gone too well. Network intensive and then a bunch of miscellaneous errors. Never got HW acceleration to work with my Radeon 9550 afterwards. 

With regard to your comment on the CD, how did you burn your first ISO? I was having the same problems as you but I downloaded another copy of the AMD64 Alternate ISO using Bittorrent. I burned this to CD and was able to install in about 40 mins or so. In fact, I am tying this message using Firefox 2.0 on Edgy. It was pretty clean. A few glitches though. It still hosed by MBR and I had to spend about 20 mins reconstructing it. I use BootIT NG and this reduces potentially disastrous problems to minor inconveniences. It also allows me to have as many primaries as I want and so I am indiscriminate about the number of installations of each OS.

I suggest you download another copy of the ISO. I got mine very shortly after the official release yesterday and I suspect that the heavy downloading going on might have something to do with the MD5 errors. The download failed a couple of times before finishing.

Good Luck!

---

### Post by Mohammed Abbas on 2006-10-28
Thanks , I'll take this in mind .

Regards,

---

