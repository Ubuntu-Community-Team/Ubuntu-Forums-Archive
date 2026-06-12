---
title: "New kernel killed ndiswrapper"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by lebski88 on 2006-10-01
Hello,

I just ran the ubuntu auto-update which in turn upgraded the kernel from 2.6.15-26-386 to 2.6.15-27-386.

sudo modprobe ndiswrapper returns an error...

This seems to have killed my internet connection which runs through ndiswrapper - which I suppose makes sense as ndiswrapper was built with the previous module. So...

(1) I have downloaded and installed the new kernel headers.
(2) Gone into the ndiswrapper directory and run 'make clean' followed by 'make' then 'sudo make install'.

sudo modprobe ndiswrapper now runs without error but I cannot access the internet.

So my question is (I suppose) how do I fully remove the previous version of ndiswrapper such that I can start again? Although I you think I should have asked a better question feel free to answer that instead...

Thanks,

Ben

---

### Post by lebski88 on 2006-10-01
Well it's fixed. Just in case anyone else has this problem after updating the kernel this is the procedure that worked for me. This assumes that you already had it working but is pretty close to the procedure for installing ndiswrapper anyway.

(1) You will need the latest kernel headers:

sudo apt-get install linux-source ******

where ***** is your new kernel version found by typing uname -r into the terminal window.

(2) ensure that the new kernel hasn't installed the acx module as this conflicts with ndiswrapper (this is the stage that got me...)

type: lsmod | grep acx 

if it finds anything then type:

sudo rmmod acx
sudo mv /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/acx /root/

(3) download the latest ndiswrapper tar.gz from sourceforge.

(4) ensure that you have build-essentials installed if not:

sudo apt-get install build-essential

(5) right click on the ndiswrapper.tar.gz and click extract here.

(6) in the terminal window navigate to the extracted directory

(7) type
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e yourdriver.inf
sudo make uninstall
sudo make uninstall
(do it twice on its recomendation... not sure why!)
sudo make clean
(not sure if this is needed as I'm a newbie but doesn't hurt)
sudo make install
sudo ndiswrapper -i yourdrive.inf
sudo modprobe ndiswrapper

then type iwlist yourinterface scan
e.g. iwlist wlan0 scan

and make sure that it gets some results.

Done!

Hope this works for someone or failing that at leasts gives you an idea.

---

### Post by sbergman27 on 2006-10-01
> **lebski88 said:**
> (2) ensure that the new kernel hasn't installed the acx module as this conflicts with ndiswrapper (this is the stage that got me...)

type: lsmod | grep acx 

if it finds anything then type:

sudo rmmod acx
sudo mv /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/acx /root/

A more permanent way to handle this is to blacklist the acx module.

In a terminal:

```

sudo nano /etc/modprobe.d/blacklist

```

Add a line to the end of the file:

```

blacklist acx

```

This tells modprobe not to ever automatically load the acx module.

Next time you upgrade your kernel, you won't have to worry.

---

### Post by lebski88 on 2006-10-01
Great tip thank you! I've just done that.

---

