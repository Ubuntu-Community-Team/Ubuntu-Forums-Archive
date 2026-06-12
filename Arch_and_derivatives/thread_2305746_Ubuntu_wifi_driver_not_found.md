---
title: "Ubuntu wifi driver not found"
date: 2015-12-08
forum: Arch and derivatives
---

### Post by telmovaz on 2015-12-08
Hi,


I've recently changed to Ubuntu and I wish to make it my main system. However, I'm having problems with wifi network and I believe I could take some advice from you. I know this has to do with Linux because I bought this computer 3 days ago and Windows (which is dual booted for now) recognizes the wifi card - there are wifi networking options appearing, unlike all Linux distros I tried (ubuntu, manjaro, debian). It's like wireless doesn't exist.


Plus, I'm not the only one facing this as five of my colleagues happen to have bought this same computer last weekend and we all came to down to conclude that we are all facing the same issue.
Our computer is "Lenovo U31-70" model with the respective wifi card "Qualcomm Atheros Communications".


Already installed the new 4.3 Kernel but (as you may guess) no success fixing this. I have access to LAN at college so it would be very helpfull if you could help us out. We do believe we could have some firmware missing but we don't know what to download or how to install it. I googled this issue but with no results.


Here is a pic with some of the information:
[ATTACH=CONFIG]266055[/ATTACH]

Thanks you in advance!

---

### Post by coffeecat on 2015-12-08
Welcome to the forum.

I've moved your thread to the ***Networking & Wireless*** section, where you are more likely to attract the attention of those of our members who take a particular interest in wireless issues.

Please have a look at this sticky: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Download and run the wireless info script as described there and post the wireless-info.txt or wireless-info.tar.gz file which will contain specific information which will help troubleshoot your problem.

---

### Post by jeremy31 on 2015-12-08
Please post the result of ```
lspci -nnk | grep -iA2 net
```

From the picture, it just shows an Atheros wifi device with ID of 0041 and that is not quite enough info.

---

### Post by kurt18947 on 2015-12-08
Coffeecat's suggestion to download and run the wireless script is an excellent one. Until we know the identifier of the device, we're just guessing. I did google around a bit and found this post:

[https://askubuntu.com/questions/656760/when-to-expect-driver-support-for-qualcom-atheros-rev-20-wifi-cards](https://askubuntu.com/questions/656760/when-to-expect-driver-support-for-qualcom-atheros-rev-20-wifi-cards)

However this is only applicable if your wifi is "168c:0041" which is one of the things the script will tell us. If you can't get the script to cooperate, even listing the output of the terminal command "lspci" would be a start, particularly the line that contains 'network controller'. A little more informative would be "lshw -c network". Remove any identifying info such as I.P. address before posting.

If there isn't support yet for your wifi card you could use a USB wifi adapter temporarily. That kinda sucks on such a sleek new machine but I've found it useful to have a USB wireless adapter that I know is plug 'n' play even if I don't use it often. I've had machines that had Broadcom wifi. Broadcom works well but requires a network connection to install the closed source broadcom drivers. It seems kinda convoluted to use one wifi adapter the enable another but hey, it works:D.

---

### Post by coffeecat on 2015-12-09
@telmovaz,

We wouldn't normally move a thread more than once, but....

> **telmovaz said:**
> Hi,

I've recently changed to Ubuntu and I wish to make it my main system.

Your added screenshot shows the output of inxi, which itself shows that you are running Manjaro Linux, which is not related at all to Ubuntu. Why do you believe you are running Ubuntu?

*Thread moved to **Arch and derivatives**.*

---

