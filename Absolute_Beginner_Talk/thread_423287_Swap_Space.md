---
title: "Swap Space"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by gj15987 on 2007-04-25
Hi. I'm currently running Vista and I created a 10GB partition on my hard disc to install ubuntu...i chose for Ubuntu to automatically set up my root partition and swap space etc.

I then read somewhere that the swap space should be about double your amount of RAM. Well on my PC i now have 65GB for windows, 9.5GB for ubuntu and then another 500mb partition which i assume is swap space...will having such small swap space affect system performance much?

Thanks.

---

### Post by taurus on 2007-04-25
Depending on how much RAM you have but 500MB of swap is good enough.

---

### Post by rsambuca on 2007-04-25
Yeah, if you are running Vista, you will be able to run ubuntu quite easily.

---

### Post by gj15987 on 2007-04-25
I have 1GB RAM. Would I notice any difference in performance if I shrunk windows a little bit and made the swap partition larger?

---

### Post by taurus on 2007-04-25
Nope.  1GB of RAM is plenty.

---

### Post by mikewhatever on 2007-04-25
No. You'll hardly ever use any swap at all, in case you stick with the default apps. The only reason to increase it would be to be able to hibernate.

---

### Post by rsambuca on 2007-04-25
I have 1 Gig Ram as well, and I don't think my swap has ever been touched.

---

### Post by gj15987 on 2007-04-25
Thanks alot for your help.

1 more question which I might as well keep in this topic:

I have to connect to a VPN in order to use the internet while i'm here at uni. Is there any way I can follow [these instructions ]("http://ubuntuforums.org/showthread.php?t=91249&highlight=vpn") to install the software to enable me to connect to the VPN without actually being online?

---

### Post by gj15987 on 2007-04-25
I'm sorry to "bump" this, but can anyone help? I don't understand apt-get and all that...is the software there...just not installed? or does it require a net connection to download it?

Thanks.

---

### Post by Delkster on 2007-04-25
> **gj15987 said:**
> I'm sorry to "bump" this, but can anyone help? I don't understand apt-get and all that...is the software there...just not installed? or does it require a net connection to download it?

Some software is available on the original Ubuntu CD, the rest must be installed over the network or manually. Apt can automatically fetch and install software packages from multiple sources, such as a CD or an online software repository as long as it knows where to look for the software.

I'm assuming that you have Ubuntu 7.04 a.k.a. Feisty Fawn which is the latest release and the links in this post lead to packages for that Ubuntu version. If you have an older release these instructions don't apply exactly.

If you're running Ubuntu 7.04, you probably have NetworkManager already. The other package mentioned in the howto for 7.04 (feisty) is network-manager-pptp which isn't installed by default, nor is it available on the Ubuntu CD. You can [download the package manually](http://packages.ubuntu.com/feisty/net/network-manager-pptp), though, just like you'd download any file. Near the bottom of that page, find the download for the architecture you're using (if you don't know, you probably want [the i386 version](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fn%2Fnetwork-manager-pptp%2Fnetwork-manager-pptp_0.6.3%2Bcvs20060819-0ubuntu2_i386.deb&md5sum=f86a4cbb8b891069086ee1ddab64db5b&arch=i386&type=main)). However, apparently network-manager-pptp requires another package called [pptp-linux](http://packages.ubuntu.com/feisty/net/pptp-linux), so download that too ([direct link to the i386 download](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fp%2Fpptp-linux%2Fpptp-linux_1.7.0-2ubuntu2_i386.deb&md5sum=e4a04b2f054b65169fd2c5a5e3cfa499&arch=i386&type=main)).

Download those packages somewhere you can access the 'net, save them on an USB stick or something, bring them to your computer, and install them. On Ubuntu 7.04 just double-clicking on them should work. Install linux-pptp first, then install network-manager-pptp.

The apt-get command in the howto would download and install those packages automatically if a network connection were available, but since you don't have it, you have to do it manually as described above. If everything goes fine and you get them installed, you can probably follow the rest of the howto.

---

### Post by Austin_KW on 2007-04-25
Are you sure that you need the vpn to get out to the net? VPNs are usually used the other way round; when you are on the internet and you need to tunnel into a private network. It is more likely that you need to set a proxy configuration.

---

### Post by gj15987 on 2007-04-25
To be honest I'm not sure, When I turn my laptop on it automatically connects to the first network called uniroam. When I open up a web browser I get the uni's internet page telling me I need to be registered to access the net. Then I connect to another network called nomadic, and then to the VPN and without being connected to all 3 I can't access the net...sounds strange to me.

Going to try installing those pptp files now. Will let you know how i get on.

---

### Post by Austin_KW on 2007-04-25
Ok, sound like they use the VPN to ensure only authorised people access their network connection. I guess it makes sense if anyone can just plug in.

---

### Post by gj15987 on 2007-04-25
Right, i've installed network-manager-pptp and pptp-linux. I have some thing that lets me configure a VPN...but for some reason I can't quite get it to work. The instructions my Uni have given me use the pptp config gui...but I can't download that either without a connection to the net, any ideas?

In the instructions it says to add 

```
# James Cameron's PPTP GUI packaging
deb http://quozl.netrek.org/pptp/pptpconfig ./
```

to the end of /etc/apt/sources.list, and then run 

```
sudo apt-get update
sudo apt-get install pptpconfig
```

Is there any way I can download the correct files from that website and put them on disc and then boot into linux?

---

### Post by Austin_KW on 2007-04-25
That url will be a directory with debian packages (.deb) files and I quess the packages description file.

You can download the latest pptpconfig .deb and either install it with dpkg (the debian package tool). I think it is "dpkg -i pptpconfig*version*.deb"

or you can create a apt-get package ( I think you use dpkg-scanpackages) and install with apt-get. There is a few more steps but it has been awhile so you will need to search the forums.

---

### Post by gj15987 on 2007-04-26
Yay! I am finally posting from within Linux! However, I can't seem to get things like the update manager etc working. Do I need to set the proxy somehow in Linux like I have had to in my browser?

Thank you all for all your help.

EDIT: Figured it out...as if it missed it when it was just in Preferences > Network Proxy!

---

