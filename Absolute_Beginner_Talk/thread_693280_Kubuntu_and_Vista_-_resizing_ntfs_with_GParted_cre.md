---
title: "Kubuntu and Vista - resizing ntfs with GParted created problem!!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by baucha_linux on 2008-02-10
Vista and kubuntu with GParted -- a big problem!!
Hi, I would be very very grateful if someone can help me out of this problem. Here goes my problem details.

I have sony viao vgn-nr160e/t with 160GiB (available 141GiB) of HDD, came with Vista preinstalled with one hidden recovery partition of about 7GiB.

I partitioned resized the Vista drive with vista disk mgmt and freed upto 20GB (I had about 80GiB empty disk space out of 141GiB but it didnt allow me to resize further). So in that 20GiB I installed kubuntu gutsy gibbon. I was very happily using it. But I wanted to free up fruther 40GiB from my vista ntfs partition(121GiB). So I used ntfsresize first, which allowed me to resize only upto further 20GiB. After that i booted from Vista and it showed my ntfs vista partition has been reduced(101GiB). I was happy. But when i checked in vista disk mgmt, it didnt show any free space and it showed vista ntfs partition as the previous size 121GiB. I cudnt figure out why it hapnd. So from kubuntu i used this GParted to resize the 121GiB ntfs vista partition. After that now I cant boot from Vista. I got boot error as below:

File : \windows\system32\winload.exe
Status: oxC0000225
Info: The selected entry could not be loaded because the application is missing or corrupt.

It asked me to use Vista CD or contact manufacturer. I dont want to lose data in the Vista drive. So can anyone please help me. I tried to boot from Kubuntu but it doesnt accept my password that i had been using to login. I had snapshots of GParted but that is in linux partition. Now I'm using kubuntu live CD but cant access my HDD. I found qtparted in live CD and tried to use but it wont let me do anything saying my sda is busy. I want to included the GParted snapshot but wondering how to embed the image file.

I'm kinda novice to linux. So please help me with this. I would appreciate ur time n effort in helping me to get back my system working.

Thanks

---

### Post by baucha_linux on 2008-02-10
Can anyone help please!

Now I hav run GParted again from Live CD (i downloaded it) and resized the ntfs vista partition back to 121 GiB size but still it wont work. same error message.

Please help!!!!

---

### Post by baucha_linux on 2008-02-11
Now i can get into my kubuntu. Finally i have reset the password. I'm trying to get my data back from vista partition.

I'm still searching a way to repair my vista. anyone has any idea how we can do it?

---

### Post by baucha_linux on 2008-02-12
no post!!!!!!!!!!! no replies!!!!!! can this happen in ubuntuforums.org.. i didnt expect this. No help form anyone so I had to format and restorte ma vista .. :(   too bad.. but i got back ma important data.

This seemed to problem for others also. U can stil post a solution if u hav one. it wil help other novices like me who wants to switch to Linux/ubuntu from windows. they will definitely bless You.

---

### Post by oedha on 2008-02-12
have you try to recover your vista by using vista cd ?

---

### Post by baucha_linux on 2008-02-13
well, asi told, i dont hav vista CD as they dont ship these days. I had the recovery drive. I used that one.

---

### Post by Presto123 on 2008-02-13
Sorry, man. Unfortunately, I have watched your thread for a few days and didn't know how to help you. All I can tell you right now is to not try to redo anything in two different programs as it could cause issues like this.

Hope everything works out for you. This issue just looks like one that not many had a fix and those that might have been able to help probably missed it.

---

### Post by bumanie on 2008-02-13
Are you still able to get into your kubuntu install? I use gnome and don't know much about the kubuntu desktop environment, but if you can still get into kubuntu, are you able to go to /home and see if there is a section on the left, named 121gb volume?

---

### Post by max renn on 2008-02-13
You should probably borrow a Vista disk from somewhere.  You shoudl aslo see what you can find out about your errors at support.microsoft.com.  I don't have Vista, but you are actually booting, so your partition is probably still intact.  Worst case, you can still grab your data off and FFR.
 
Your computer OEM might support you?

---

