---
title: "Noob with wireless problems"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Revmann on 2006-05-14
I am absolutely new to Linux and Ubuntu and am having a lot of growing pains. I am running an Acer Aspire 3003LCi laptop with SIS 900 wireless. Of course, the wireless doesn't work and I am trying to remedy it. I did find a driver or something for it in the  .tar.gz format. I read the sticky thread about installing things. I read the readme file from the driver after I "unzipped" it. It looks like a foreign language. I am so confused and I just want it to work. Ever seen a 6'3 balding 320lb man cry? Anyone got a webcam?? :P Any help to get this installed would help me immensely. This wireless issue is the only problem I have left keeping me from totally getting away from windows for the most part.

---

### Post by Jagot on 2006-05-14
According to a few things I've looked at about your laptop it would appear that the wireless is actually a Broadcom, so you will need to install ndiswrapper to sort this.  

So, firstly:

```
sudo aptitude install ndiswrapper-utils
```

Now you will need to get your wireless drivers.  I have a Dell with a Broadcom wireless card and I actually had to use Acer's drivers for the same card to get it working, so you will be able to go to Acer's website to download the correct driver - it will be a .inf file, possibly even the same as the driver I use: bcmwl5.inf.

Now you will need to install the driver with ndiswrapper (this assumes your driver is put on the desktop - if it isn't then just change according to wherever you've dumped the driver):

```
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
```

Then, to check it is installed properly:

```
sudo ndiswrapper -l
```

Now we need to probe the module:

```
sudo modprobe ndiswrapper
```

And finally:

```
sudo ndiswrapper -m
```

Now you will need to go to the network settings (System -> Adminstration -> Networking) and you should now find the wireless card there, so all you need to do is ensure it is selected and you enter any settings necessary, such as WEP keys or whatever.  Make sure you click to activate the wireless card.

---

### Post by Revmann on 2006-05-14
Thanks, I noticed this a few minutes ago, but I needed to clear my head :p

Btw, also a forum noob as well. Accidentally sent a reply as a bad post report instead. My apologies.

---

### Post by Revmann on 2006-05-14
I want to thank you so very much for doing this for me. I go it working within 5 minutes of reading your post. It is working great and I am so happy. 

Thanks again :)

---

