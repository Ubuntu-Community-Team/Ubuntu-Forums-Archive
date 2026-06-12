---
title: "Downloads timing out"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Binary_2 on 2007-06-08
Any download is timing out.  Whether it is through the browser or aptitude or apt-get, they time out eventually.  There is no particular rhyme or reason.  It also doesn't matter what site I am downloading from, whether it be java.com or security.ubuntu.com.  Now I know that it is not this computer, because I've plugged it into another network and had it download successfully.
Now here comes the weird part.  I can download things, i.e. the alternative install iso from ubuntu on another (windows) box on this same network.  With this computer the internet works fine, i can download torrents, i can ping IP's and Domain Names without problem, but downloading from http and ftp fails eventually.  any ideas?

Edit:  some short downloads will finish.

---

### Post by dannystaple on 2007-06-08
Hmmm - this sounds interesting.
How is it connected to the network? Does it have static IP or DHCP setup? I think a connection is being reset or cleared away regularly. BitTorrents will work as they are made of many small downloaded chunks.
Can you try a long download from a command line? 

To do this, first make sure you have wget (I think it may be in the standard ubuntu install but there is no harm in checking):
> sudo apt-get install wget

Then you can go and find a big download, like one of those ISO images or something. Copy that URL.

Type:
> wget <put your URL here>

And paste us the results. Maybe we can work from there.

---

### Post by Binary_2 on 2007-06-08
ok sounds great, thanks for your help.
Downloading now from wget.

---

### Post by Binary_2 on 2007-06-08
```
~$ wget http://ftp-mirror.internap.com/pub/ubuntu-releases/7.04/ubuntu-7.04-desktop-i386.iso
--14:07:33--  http://ftp-mirror.internap.com/pub/ubuntu-releases/7.04/ubuntu-7.04-desktop-i386.iso
           => `ubuntu-7.04-desktop-i386.iso'
Resolving ftp-mirror.internap.com... 64.74.207.33
Connecting to ftp-mirror.internap.com|64.74.207.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 731,797,504 (698M) [application/x-iso9660-image]

48% [================>                    ] 354,878,418   --.--K/s  ETA 1:44:55

```

so this is how far it got before stopping.  When I copied this the ETA was climbing and it hadn't transferred a bit in about 30 minutes.  You can see that it connects and starts the transfer, then it stops, seemingly for no reason.  Now where I work, we have a backup ISP in case our primary goes down, if I plug into that one I can download all I want.  I can also download on the primary internet connection on every computer in the office but this one.  ODD!!??!!

---

### Post by taurus on 2007-06-08
Try

```

wget -c http://ftp-mirror.internap.com/pub/ubuntu-releases/7.04/ubuntu-7.04-desktop-i386.iso

```

---

### Post by Binary_2 on 2007-06-08
i tried that and it is now at 17:32:30 and climbing about 1 hour every 5 seconds.  Transfer rate is at --,--

any ideas?

---

### Post by Binary_2 on 2007-06-08
bump....
sorry, but I'm really hoping there is a solution to this maddening problem.

---

