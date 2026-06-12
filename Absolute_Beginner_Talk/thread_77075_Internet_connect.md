---
title: "Internet connect"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by ian64 on 2005-10-16
I have carried out a default installation of UBUNTU but can find no way to make an internet connection. Any advice would be greatly appreciated. Thanks.
Ian64

---

### Post by natman on 2005-10-16
hi i use the following to connect always ( dont know why it works but it seems to - im using a ethernet cable)
in a terminal type:
>sudo dhclient
it asks for pass type it in
when the box stops printing out stuff, try the internet again, it might be slow at first.
hope this helps

---

### Post by audax321 on 2005-10-16
sudo dhclient will just get you a new IP. But its pretty useless unless you have an ethernet device setup to begin with. Just to make sure you do, go to System > Administration > Networking and configure the device by going into its properties, choosing "ENABLE THIS DEVICE", and then "DHCP" in the drop-down box (unless you want to specify a static one). Click OK and then, with the device selected, click the ACTIVATE button. Click the OK button to exit the dialog when finished. If you have further problems try a good old-fashioned reboot. This sometimes helps, but if it still doesn't post your /etc/network/interfaces file contents.

---

### Post by Kapre on 2005-10-16
[QUOTE=ian64]I have carried out a default installation of UBUNTU but can find no way to make an internet connection. Any advice would be greatly appreciated. Thanks.
Ian64[/QUOTE]

ian64 - what type of internet connection are you going to make? will you be using dial-up or adsl/cable modem? If you going to use dial-up, you have to make sure that your modem was detected during the install, if not go to audax321 suggestion and check if your modem was enabled.

If you are using adsl (make sure your modem is "on"), go to a terminal and type in "sudo pppoeconf" and make sure to answer all the questions and key-in the user name and password your ISP gave you.

K

---

