---
title: "Using a mobile phone as a modem"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-01-06
One other thing I can do in Windoze which I would like to do in Ubuntu is to use my mobile phone as a modem with my laptop running 6.10. Useful when you can't get a connection any other way. In Windoze I plugged in a blutooth dongle, paired the dongle with my phone and it worked, but it required the software that came with the dongle.

In Ubuntu, I installed the bluetooth program that allows you to transfer files between bluetooth devices as the nearest thing to the Windoze set up, but it doesn't work with the dongle. Can anybody offer me any guidence on this, please?

Thanks

---

### Post by puneit on 2007-01-07
Hi, 
I use my Bluetooth enabled Nokia 6255 as a modem to connect to the Internet when I am on move.
I am using Ubuntu Edgy, but what I am going to share with you, worked on SuSE also. So, even if you are on a different flavor or version, this should work
```
sudo gedit /etc/bluetooth/rfcomm.conf
```
You need to change few things in the file... Following are the contents of my file.
```
# RFCOMM configuration file.


rfcomm0 {
	# Automatically bind the device at startup
	bind yes;

	# Bluetooth address of the device
	device 00:02:EE:9B:09:7C;

	# RFCOMM channel for the connection
	channel	1;

	# Description of the connection
	comment "Ubuntu Edgy";
}
```
Replace device **00:02:EE:9B:09:7C** with your bluetooth hardware mac address.
Once you have done that, save the file and close it
Now, I use Gnome PPP to connect to internet using bluetooth.. but basically the following you should be knowing
The modem device is ```
/dev/rfcomm0
``` Kindly note that this won't get detected on its own, so you will have to type it out
Type in user name and password you use to connect to the internet and supply the phone number. All these you can get from your mobile service provider. 
Also sometimes, you need some Init Strings, which are analogous to Extra Settings of a modem in Windows. This is also service provider specific. So, you can get these from your service provider.

---

### Post by Charlie Chick on 2007-01-08
Thanks very much for your reply. It's a bit technical for me as I'm an Ubuntu beginner, but I'll give it a go.

---

### Post by puneit on 2007-01-08
What did you find techy? feel free to ask

---

### Post by Charlie Chick on 2007-01-10
All of it! :)

---

### Post by puneit on 2007-01-10
Understanding will come gradually; for now you try out what I have advised. And tell me where you get stuck.
I am no expert myself. Switched to Linux only in September 2006. 
Its just different. Different is not difficult. It seems difficult because its not in our comfort zone. Give it some time, you will start finding this also comfortable.

---

### Post by hayz on 2007-01-26
Can anyone tell me how to connect my nokia 3250 as modem[Gprs] On Ubuntu?
I use a Data Cable.

---

