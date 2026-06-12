---
title: "Can't access the internet"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by jessicadrian on 2007-01-15
We are having problems accessing the internet.  First, let me explain that we have a desktop computer running a linksys router.  We have Ubuntu installed on a Dell B130 notebook, and we're trying to use the wireless card to access the internet.  The card is compatible with Ubuntu, and the status shows that it is receiving the signal from the router usually anywhere from 91 - 99%, and says that it's receiving packets.  But, when we try to load a website on Firefox, it doesn't work (Firefox says "Server not found").  What can we do to access the internet?  Is there a firewall that we need to turn off?  We are only in the absolute beginning stages of learning Linux, so we are totally clueless as to what to do.  We also tried to ping Yahoo's ip address as a test to see if we get a response, but there's no response.  Please help!  Thanks in advance!

Jessica & Adrian

---

### Post by crispy_420 on 2007-01-15
Are you able to get to your home page, most likely not?

From your desktop, access the routers admin pages. Not familar with linksys, but can you look at connected devices.

As with any compatible wireless card and Ubuntu, I suggest networkmanager. It solves most connection issues but "sniffing" out the best connection.

---

### Post by tronica on 2007-01-15
If you have WEP or any other type of encryption, disable to help get it going. Then once you have it going, enable them.

---

### Post by carlosfocker on 2007-01-15
Try accessing [http://192.168.1.1/](http://192.168.1.1/). (Unless you have already done this and change the defualt settings)

If you cant get there like crispy said then you are not receiving and ip address.

If you haven't set the password then use linksys with no user. 

Go to status and under IP Address is there a number other than 0.0.0.0?

---

