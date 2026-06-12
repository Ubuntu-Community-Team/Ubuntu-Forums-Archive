---
title: "Installing Ubuntu over OSX"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by dawozman1 on 2008-08-21
I have been using OS X for the past few years but have no solid ties. As I have been working closely with a missions organization setting p used computers for their school in Haiti I have become more fond of Linux, specifically the Ubuntu distro. Rather than dealing with two OS, dual booting and the like, I figured I would install Linux over OS X. I have been having trouble getting the formatting right, I can get Ubuntu to install fine, but reguardless of how many wireless setups for the broadcom drivers the wireless wont work, then I realized Ubuntu wouldn't show my hard drive, I was having to mount it, but even when I would mount it from the terminal I couldn't access it correctly in the desktopr or places, or through terminal. Im not sure if i have some settings wrong or something but if you can help me out of point me to a tutorial for installing Ubuntu over mac OSX that would be great

---

### Post by cyberdork33 on 2008-08-21
> **dawozman1 said:**
> I have been using OS X for the past few years but have no solid ties. As I have been working closely with a missions organization setting p used computers for their school in Haiti I have become more fond of Linux, specifically the Ubuntu distro. Rather than dealing with two OS, dual booting and the like, I figured I would install Linux over OS X. I have been having trouble getting the formatting right, I can get Ubuntu to install fine, but reguardless of how many wireless setups for the broadcom drivers the wireless wont work, then I realized Ubuntu wouldn't show my hard drive, I was having to mount it, but even when I would mount it from the terminal I couldn't access it correctly in the desktopr or places, or through terminal. Im not sure if i have some settings wrong or something but if you can help me out of point me to a tutorial for installing Ubuntu over mac OSX that would be greatWhat type of mac is this?

---

### Post by dawozman1 on 2008-08-21
Its a macbook 4,1 according to :

root@mdwozniak-macbook:~# sudo dmidecode | grep Product
	Product Name: MacBook4,1
	Product Name: Mac-F22788A9

thanks

---

### Post by cyberdork33 on 2008-08-21
In that case, you just boot the liveCD, start the installer, and when prompted, choose to use the entire hard drive. This will completely erase everything and repartition and format everything.

For your wireless, check the Macbook4,1 wiki page:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by dawozman1 on 2008-08-21
thanks, ive installed from the Live CD a few times, this most recent time, it left me not having sudo priviledges, there was no root created during the install for the entire hard drive, the hard drive wouldnt show up once i installed, i followed all the directions on the santa rosa macbook  ubuntu community about wireless and it has not worked any of the times i have installed. any ideas about what could be causing this? its strange because i have reinstalled with the "entire hard drive"option through the Live Cd installer 3 or 4 times but keep having these problems.

---

### Post by cyberdork33 on 2008-08-21
> **dawozman1 said:**
> thanks, ive installed from the Live CD a few times, this most recent time, it left me not having sudo priviledges,strange

> **dawozman1 said:**
> there was no root created during the install for the entire hard drive, the hard drive wouldnt show up once i installedSo you couldn't boot into the installed system at all? or you could boot into it and then you couldn't see something...?

> **dawozman1 said:**
> i followed all the directions on the santa rosa macbook  ubuntu community about wireless and it has not worked any of the times i have installed.If you have no (working) install I don't know how you are trying to install drivers for your wifi hardware... You have to have Ubuntu installed before you can start configuration.

Your statements above seem contradictory which is why this is very confusing. Are there any specific error messages you are getting? Does grub show after the install?

---

### Post by dawozman1 on 2008-08-21
ubuntu will install and load up to the os, once i have logged in i cannot see my HD.

the last part i said about the santa rosa tutorial/help not working, I meant that each time i had installed ubuntu new, I would follow tutorials,everything worked fine in the terminal no error messages, but nothing would come of the work I was doing, no wireless, no HD showing up etc

---

### Post by cyberdork33 on 2008-08-21
> **dawozman1 said:**
> ubuntu will install and load up to the os, once i have logged in i cannot see my HD.OK, well Your HD does not show on the Desktop by default as it does in OS X. If you click on the "Places" menu item and choose "Computer", you can see the drives listed. You will usually only ever want to access your home partition (and the folder it contains) which are directly under the Places menu.

> **dawozman1 said:**
> the last part i said about the santa rosa tutorial/help not working, I meant that each time i had installed ubuntu new, I would follow tutorials,everything worked fine in the terminal no error messages, but nothing would come of the work I was doing, no wireless, no HD showing up etc
can you give the output of 'ndiswrapper -l' (that's a lowercase L) in your installed system after you have tried to get the WiFi working?

---

### Post by dawozman1 on 2008-08-21
well the reason I realized I couldnt see my hard drive(in places) was because I wasnt able to save a driver to a place where the driver installer could access it. 

Im in the process of reinstalling on the macbook again, this time I will check and double check everything to a T as I work on the wireless and any other issues. So if it happens this time ill post error codes as I go.

---

### Post by cyberdork33 on 2008-08-21
> **dawozman1 said:**
> well the reason I realized I couldnt see my hard drive(in places) was because I wasnt able to save a driver to a place where the driver installer could access it. Save save the driver file to your Desktop. Once you isntall it you can remove the files there because ndiswrapper copies what it needs elsewhere.

---

