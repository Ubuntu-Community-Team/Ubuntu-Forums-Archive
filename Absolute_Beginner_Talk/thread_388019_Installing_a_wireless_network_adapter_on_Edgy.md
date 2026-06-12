---
title: "Installing a wireless network adapter on Edgy"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by karactor on 2007-03-19
Hey Guys

Complete newbie to Ubuntu here. Just installed ver 6.10, but am still isolated from the world as I do not have any connectivity.

I still haven't figured out a way to connect to the internet, problem being an inability to get my wireless network adapter working. I use a linksys wireless adapter(and a linksys wireless router, if it is relevant), but have no idea how to get it installed, to get it up and running on my newly installed Ubuntu.

Any help in this regard would be greatly appreciated.

Thanks and regards...

---

### Post by digital_sabotage on 2007-03-19
I'm a recent newbie too ...but I had luck setting up my wireless.
Go to menu 'System'... 'Administration'... 'Networking'... you should see your wireless connection there if it's been detected.  Mine wasn't but I was able to use ndiswrapper to install a windows driver.  Then I was able to go to 'Networking' and the wireless card showed and I was able to configure it from there.  I hope this helps:-)

---

### Post by karactor on 2007-03-19
Hi

Thanks for your reply. I'll definitely try out your suggestion later today when I get back. Could you also let me know how I could use 'ndiswrapper' that you have mentioned, in case I face the same issue as well?

Also, in a worst case scenario, is there any way the drivers could be downloaded and installed?

Thanks again. :)

---

### Post by digital_sabotage on 2007-03-26
Sorry for the delayed response karactor... I installed ndiswrapper using synaptic and then I was able to run it from >System >Administration >Windows wireless drivers ...click on "install new driver"  ...it then asks you to navigate to the cd or folder that contains the Windows ".inf" file for your wireless card.  That worked for me.  Then went back to >Networking to set my ssid and password to my router.  Hope this helps:-)

---

