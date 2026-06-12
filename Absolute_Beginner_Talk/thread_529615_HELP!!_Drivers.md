---
title: "HELP!?! Drivers"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Decatur on 2007-08-19
I am building a computer and I have downloaded Ubuntu on a disk and I do not have the computer yet but I dont have the drivers for ubuntu so I went to MSI's website to download them but they did not support Ubuntu. 

WHAT DO I DO??
<im a noob>

---

### Post by Hobo Joe on 2007-08-19
What card do you have and what manufacturer is it?

---

### Post by Decatur on 2007-08-19
I have this...[http://www.newegg.com/Product/Product.asp?item=N82E16856167009](http://www.newegg.com/Product/Product.asp?item=N82E16856167009)

---

### Post by Decatur on 2007-08-19
I think im going to have a parallel structured seizure.

---

### Post by RomeReactor on 2007-08-19
Hi. Ubuntu will provide you with drivers for your hardware (as long as it's supported). When you get your computer, try Ubuntu (in BIOS, choose to boot from CD) and check that everything works. Ubuntu will run from the CD, so it won't do anything to your hard drive until you choose to install it.

If something doesn't work, it's still possible to get it to work after installing Ubuntu.

---

### Post by Decatur on 2007-08-19
now what? Do you think i will be fine?

---

### Post by Decatur on 2007-08-19
ill just be happy when my fiesty makes it with the fawn

---

### Post by Hobo Joe on 2007-08-19
Ok, so you have an integrated nVidia card.

First things first. *Don't freak out.* We will help you, but you have to do what we say.

Now, Envy will install and setup your drivers for you, so, download [this]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb") , and then open the file(it will most likely download to your desktop), and it will install itself.
Then go to 'Applications > System tools > Envy' Once it's open just click 'install nVidia driver'. It will install automagically for you. But when it asks you if it can configure your xorg file, make sure you say YES.

Good luck. :)

Also you don't need to post twice a minute, we are typing!

---

### Post by Decatur on 2007-08-19
I dont have Ubuntu installed yet. I dont even have mycomputer. so i was hoping i could put them on a CD.

---

### Post by Hobo Joe on 2007-08-19
Oh, my mistake.

Ok, go ahead and install, and it will install all the default drivers for you, except for the graphics card. 

HOWEVER, it will give you generic drivers that will enable you to run it until you install the proper drivers.
So you really don't have anything to worry about.

---

### Post by Decatur on 2007-08-19
wait so my graphics card is the only non compatible thing and i now have it.

---

### Post by RomeReactor on 2007-08-19
When you get your computer, run the Ubuntu CD. At first it will use an open source driver to get the display working. This driver works very well except for the fact that it doesn't give you direct rendering (acceleration so you can play 3D games or use Desktop Effects. For that, you install the official Nvidia driver, but that's after installing Ubuntu. Once Ubuntu is installed, the **easiest** way to enable the acceleration on your Nvidia 6100 is to go to "System->Preferences->Desktop Effects"; Ubuntu will ask you if you want to install the official Nvidia drivers. Answer "Yes", and it will get them for you and install them. This should work perfectly for your 6100, so I don't think you need to install Envy.

From the hardware specifications, the one thing that I think **might** be troublesome is the Realtek soundchip, but as I said before, try the CD to see what works and what doesn't.

---

### Post by Hobo Joe on 2007-08-19
> **Decatur said:**
> wait so my graphics card is the only non compatible thing and i now have it.

NO, it's perfectly compatible, it's just the Ubuntu doesn't install the proprietary drivers by default, it gives you generic drivers until you install the proper ones.

---

