---
title: "Edgy upgraded, Net. Man error"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by newlinuxuser on 2006-10-27
Hi i recently upgraded to edgy from dapper - all went fine. The wireless was working and now it isnt, when I clicked on the network manager it displayed: 

"SIOCGIFFLAGS error: No such device" 

so I thought right, i had this once in dapper - I just typed in the terminal "sudo modprobe ndiswrapper" and poof its working, though in edgy I got this message... 

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument"

I did try a clean instal of edgy but same problem when typing "sudo modprobe ndiswrapper" while installing the driver.

I would really need some help and I've posted before but to no avail, I've posted as much information I can - the thing is it worked perfectly in dapper so its a little dissapointing. 

Thanks in advance! :KS 

Mike

---

### Post by chuckyp on 2006-10-27
How did you install ndiswrapper?

---

### Post by newlinuxuser on 2006-10-27
i downloaded it using XP, "**ndiswrapper-utils_1.8-0ubuntu2_i386.deb**" and then installed it. I tried this with a clean install of edgy, it installed fine on dapper but as soon as i upgraded i ran into problems, obviously I didnt reinstall after the update I just ran "sudo modprobe ndiswrapper" to bring up the card but hit the above errors.

---

### Post by newlinuxuser on 2006-10-27
Anyone got any ideas? I really could do with some help... Thanks again.

Mike

---

### Post by newlinuxuser on 2006-10-29
I could really do with some help, I saw some threads that installing ndiswrapper manually using "SPM" - ( dont know what SPM stands for) seems to fix this, could someone give me some help on how to do this without an internet connection. At the moment im using XP so any files I may need I guess I could use a usb stick to transfer them. Thanks.

Mike

---

### Post by kanapee on 2006-10-29
You could try these: 
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) < including installing with no internet-connection

I'm sad that's the only way I can help, but good luck.
I had some problems with my wlan, mainly becouse the 128-bit wep encoding, but if you say it worked on dapper, that can't be the cause.

EDIT: Which thread did you see it on?

---

### Post by newlinuxuser on 2006-10-29
Thanks for your reply, these sites seem to be be aimed up to Dapper users, I had no problem installing my windows driver using ndiswrapper on Dapper, it was easy - im just running into problems with edgy :confused:

---

