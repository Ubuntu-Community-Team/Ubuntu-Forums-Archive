---
title: "Wireless Woes"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-06-29
I was wondering if anyone could get me going on how to install the correct drivers for my Dell Wireless 1500 Draft 802.11n WLAN Mini-Card? Thanks a bunch.

---

### Post by overdrank on 2007-06-29
> **Bofur said:**
> I was wondering if anyone could get me going on how to install the correct drivers for my Dell Wireless 1500 Draft 802.11n WLAN Mini-Card? Thanks a bunch.

HI this thread had the most promising outlook.
[http://ubuntuforums.org/showthread.php?t=285166&highlight=Dell+Wireless+1500](http://ubuntuforums.org/showthread.php?t=285166&highlight=Dell+Wireless+1500)
Hope this helps and good luck!

---

### Post by Bofur on 2007-07-02
Ok, I went into Synaptic and had it install ndiswrapper-common, ndiswrapper-source, and ndiswrapper-utils-.1.9.

I also downloaded the correct dell drivers from the site and unzipped the .exe file and extracted the files to a folder.

Now, how exactly do I go by installing the drivers with ndiswrapper? Thanks!

---

### Post by Bofur on 2007-07-02
Bump

---

### Post by Bofur on 2007-07-02
Anyone, please?

---

### Post by Bofur on 2007-07-02
Bump

---

### Post by OldGaf on 2007-08-26
I actually did this the other day. I had it working on Edgy for about a year, and now have done it with Feisty. I got errors when not using sudo for some of the commands so I put sudo where you need use them.

P.S. - I got the latest windows driver from Dell, installed it on the windows side and then copied the "driver" folder over to my Linux home dir. There are about 5 files in it.


1. Make sure you have the headers:
> sudo apt-get install linux-headers-`uname -r`

2. Grab the latest Dell drivers from this link:
> [Dell]("http://www.dell.com")

3. Grab the latest Ndiswrapper from thier site:
> [Ndiswrapper]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=515643")

4. Go to the downloaded file (move it to your home folder if it is not their) and extract it:
> tar -zxvf ndiswrapper-1.47.tar.gz

5. This will create the ndiswrapper-version directory. Change to that directory:
> cd ndiswrapper-1.47

6. Once in the source-directory run:
> sudo make distclean

7. Then run:
> sudo make

8. Making sure you are still in the source-directory, run:
> sudo make install

9. Then run the following to install the drivers (change path as required):
> ndiswrapper -i /path/to/driver/bcmwl5.inf

10. > sudo ndiswrapper -m

11. > sudo depmod -a

12. > sudo modprobe ndiswrapper

You may need to reboot.

---

