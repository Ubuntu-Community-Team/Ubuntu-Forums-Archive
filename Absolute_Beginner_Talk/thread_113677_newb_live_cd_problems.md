---
title: "newb live cd problems"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by gmc1200 on 2006-01-06
Hey, first time poster here and first time linux user.  Im want to see how ubuntu is, so i dled the live cd of ubuntu 5.10 and i burned it to a cd at 8x speed.  i put it into my laptop and it starts up where i press enter to continue. then it asks for language...etc, and then it starts loading. my problem is when it gets to "Loading additional components" it gets stuck at 4% where its "retrieving hw-detect-full" then it tells me theres a problem with my cd-rom. i already burned it 4 times and it still hasnt worked. do i just have a crappy burner? 8x is the lowest i can go so i dont know what to do. if you can help me out it would be greatly appreciated.

---

### Post by Qrk on 2006-01-06
Check the md5 sum of the .iso

I think you'll need to download a program to do in Windows. Once you do, the md5 sum should match those given on the download page on the ubuntu website. 

If they don't match, you'll need to re-download ubuntu. But a good tip is to use bittorrent or a good download manager. These are less likely to only quit after a partial download.

---

### Post by gmc1200 on 2006-01-08
thanks a lot! i redled it on bittorrent and now it works.  i noticed that its kinda slow, so i guess when i get more comfortable with it, ill do the install.  

i still have a couple questions.  i noticed my wireless internet doesnt work.  ive seen countless posts about that topic, but i still cant follow what has to be done to get it to work. also, lets say i save something while working with ubuntu, once i shut off the computer and go back to using windows, will i still have that data? thanks for the help so far.

---

### Post by adssse on 2006-01-08
[QUOTE=gmc1200]
i still have a couple questions.  i noticed my wireless internet doesnt work.  ive seen countless posts about that topic, but i still cant follow what has to be done to get it to work. also, lets say i save something while working with ubuntu, once i shut off the computer and go back to using windows, will i still have that data? thanks for the help so far.[/QUOTE]

As far as the wireless you may need to use ndiswrapper if your wireless card is not directly supported. Is this an internal or external card? If you can give us the chipset or make and model of the card we should be able to help point you in the right direction. (try typing 'lspci' and looking for your wireless)
When using the live cd and saving something it will not be there unless you have a fat parition on your hard drive to save it to, you wont be able to write to a ntfs parition. If you dont you could save to something such as a thumb drive.

---

