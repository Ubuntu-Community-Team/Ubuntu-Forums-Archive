---
title: "Need MAJOR Help!  Too new at this"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by rock0nman on 2007-12-13
I just trudged my way through a painfull Ubuntu installation process.  I have an HP pavillion dv6500.  It has an Nvidia 7150.  Ubuntu doesn't seem to get along with HP.  My problem is:

I can't get my resolution above 800x600.  I've taken care of the restricted software thing.  I've even downloaded a supposed appropriate driver.  But i can't get the driver installed.  This is my very first experience with anything Linux so be gentle.  WHAT DO I DO!!??

---

### Post by Dr Small on 2007-12-13
Greetings, and welcome to Ubuntu Forums. We will try to be as helpful as possible in solving your problems :D
Could you please explain how you are trying to install this driver ? You should be able to install the driver right from System > Administration > Restricted Drivers

Dr Small

---

### Post by RomeReactor on 2007-12-13
> **rock0nman said:**
> I just trudged my way through a painfull Ubuntu installation process.  I have an HP pavillion dv6500.  It has an Nvidia 7150.  Ubuntu doesn't seem to get along with HP.  My problem is:

I can't get my resolution above 800x600.  I've taken care of the restricted software thing.  I've even downloaded a supposed appropriate driver.  But i can't get the driver installed.  This is my very first experience with anything Linux so be gentle.  WHAT DO I DO!!??

Hi. Did you download the driver from nvidia's website? the easiest way to install programs in Ubuntu is through it's package manager, Synaptic; and to install the nvidia driver, you go to "System->Administration->Restricted Drivers Manager". If you did install the driver downloaded from nvida's site, you'll need to uninstall it before using the one from the repositories. This [community documentation]("https://help.ubuntu.com/community/SoftwareManagement") page may be of help in learning about packages and repositories, and program installation in general.

If you have questions, please post back. And welcome to the community!

---

### Post by rock0nman on 2007-12-13
Howdy.  Thanks for the welcome.   I already did that.  It still won't go above 800x600.  From other forums I've read I need a different driver.  But the explanations they give are written in linux...I still speak windows.  Not bi-lingual quite yet.  I'll try to find the posts i've read and see if someone can translate.

---

### Post by Dark_Stang on 2007-12-13
Click on the link in my sig and go through the guide there. If you have the 7150 then you have the amd processor and the broadcom wireless card too, all of that is taken care of in that.

---

### Post by rock0nman on 2007-12-13
> **RomeReactor said:**
> Hi. Did you download the driver from nvidia's website? the easiest way to install programs in Ubuntu is through it's package manager, Synaptic; and to install the nvidia driver, you go to "System->Administration->Restricted Drivers Manager". If you did install the driver downloaded from nvida's site, you'll need to uninstall it before using the one from the repositories. This [community documentation]("https://help.ubuntu.com/community/SoftwareManagement") page may be of help in learning about packages and repositories, and program installation in general.

If you have questions, please post back. And welcome to the community!

I downloaded the driver from nvidia but can't figure out how to install it.

---

### Post by Dr Small on 2007-12-13
> **rock0nman said:**
> I downloaded the driver from nvidia but can't figure out how to install it.
Could you please supply us with a link to where you downloaded the driver from?
Then we could supply you with a command to install it with.

Dr Small

---

### Post by philinux on 2007-12-13
Maybe he needs this,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by logos34 on 2007-12-13
> **rock0nman said:**
> 
I can't get my resolution above 800x600.  I've taken care of the restricted software thing.  I've even downloaded a supposed appropriate driver.  But i can't get the driver installed.  This is my very first experience with anything Linux so be gentle.  WHAT DO I DO!!??

Did you use the nvidia config utility?

**$ sudo nvidia-settings**

---

### Post by shae on 2007-12-13
What is the output when you enter the following command in terminal?
```
glxinfo | grep direct
```

---

### Post by rock0nman on 2007-12-13
> **Dark_Stang said:**
> Click on the link in my sig and go through the guide there. If you have the 7150 then you have the amd processor and the broadcom wireless card too, all of that is taken care of in that.

I must say thanks to everyone that has provided support tonight.  But this post here just cured my linux illness.  That was perfect information and thanks to the person that posted it.

---

### Post by Dark_Stang on 2007-12-13
> **rock0nman said:**
> I must say thanks to everyone that has provided support tonight.  But this post here just cured my linux illness.  That was perfect information and thanks to the person that posted it.
Glad I could help. :-)

---

