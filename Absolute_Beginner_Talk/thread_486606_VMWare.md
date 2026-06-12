---
title: "VMWare"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by buntutur on 2007-06-28
HI frnds,

I have just joined the great linux club...

I am using ubuntu edgy 6.10.
 Now i want to use a program which is windows based (i.e .exe) I tried to run it using wine but everytime i try to run .exe file there is a error asking me to install IE4.02 SP2 despite the fact i have already got it installed on my LInux.

I know this can be done using VMWare also. I already have a running VMWare player on my PC but that was installed and configured by a technical guy. Now i am on my own, I am not able to figure out how to create a windows server on my PC using this VMWare so that i can install the window based software.

I would be thankful for any help.

---

### Post by koshari on 2007-06-28
so you want to run vwware on a linux host?

or you want to run vmware on a windows host and use vmware installed in linux to connect to the virtual machine on the windows host?

or maybe you want to run a windows client through vmware on a linux host.?
if you want to install vmware on ubuntu its in the conocial commercial repositories already compiled so it can be very easily installed through apt/synaptic.

the setup script is pretty self explanatory

---

### Post by buntutur on 2007-06-28
> **koshari said:**
> so you want to run vwware on a linux host?

or you want to run vmware on a windows host and use vmware installed in linux to connect to the virtual machine on the windows host?

or maybe you want to run a windows client through vmware on a linux host.?
if you want to install vmware on ubuntu its in the conocial commercial repositories already compiled so it can be very easily installed through apt/synaptic.

the setup script is pretty self explanatory

I want to run windows client through vmWare on linux host so that i can send my output from a program running in linux to this windows based software. I already have installed VMPlayer and using it for some other program.

Now what should I do so that i can run this windows based in-house software to run simultaneously on my linux

Thanks a lot

---

### Post by ike on 2007-06-28
> **buntutur said:**
> I want to run windows client through vmWare on linux host so that i can send my output from a program running in linux to this windows based software. I already have installed VMPlayer and using it for some other program.

Now what should I do so that i can run this windows based in-house software to run simultaneously on my linux

Thanks a lot

I don't believe you can install Windows in VMWare Player (other than downloadable customized virtual appliances).. But VMWare Server should be available in the commercial repo.

You should however reconsider running VirtualBox instead. It's very simple and the install on Ubuntu is dead easy (.deb). And, it's under gpl (well, at least the light version).

Check out [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

