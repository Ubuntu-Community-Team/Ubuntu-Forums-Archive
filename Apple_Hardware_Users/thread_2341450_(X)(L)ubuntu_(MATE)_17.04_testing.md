---
title: "(X)(L)ubuntu (MATE) 17.04 testing"
date: 2016-10-28
forum: Apple Hardware Users
---

### Post by xeno74 on 2016-10-28
Hi All,

I successfully updated my ubuntu MATE 16.10 PPC Yakkety Yak to 17.04 PPC Zesty Zapus yesterday. I want to start some testing.

[Update instructions for (X)(L)ubuntu (MATE)]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3554")

[[IMG]https://lh3.googleusercontent.com/-WAQWVTm37kM/WBJnCPOYc6I/AAAAAAAAEPU/N8XfingrABsDg_gL3-ljxIq9jLmjnaaRgCJoC/w530-h398-p/ubuntu_MATE_17.04_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/6fYzPwGLneA")

Cheers,
Christian

---

### Post by ernsteiswuerfel on 2016-11-01
Installing from a daily live iso does not work at the moment (likewiese on amd64): [bug #1637985]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1637985")

---

### Post by eastone on 2016-11-01
MATE 17.04 on G5 almost works ;)
[https://plus.google.com/113510686010520773635/posts/itci5ACWQ7W](https://plus.google.com/113510686010520773635/posts/itci5ACWQ7W)

---

### Post by ernsteiswuerfel on 2016-11-03
[bug #1637985]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1637985") is resolved now. Installing 17.04 on my PowerBook G4 5,6 worked (manual install).

---

### Post by eastone on 2016-11-05
No more garbage on the desktop but cannot set a wallpaper. Have got only black screen.

---

### Post by luigiburdo on 2016-11-06
> **eastone said:**
> No more garbage on the desktop but cannot set a wallpaper. Have got only black screen.

download  src rebuild and install 
libjpeg turbo
libpng 

usually i fix like this this kind of issue

---

### Post by xeno74 on 2016-11-07
The MATE desktop **1.16.1** is available for ubuntu MATE **17.04** PowerPC:

[[IMG]https://lh3.googleusercontent.com/-HNSwf09CuAw/WCCDSnQC7KI/AAAAAAAAESg/Dkpl74RnLq4AImSB3WLSvyMaS3WYYuUzwCJoC/w530-h398-p/ubuntu_MATE_17.04_MATE_Desktop_1.16.1.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/Nsot8NfzmSv")

---

### Post by xeno74 on 2016-12-22
FYI:

[quote="Phoronix"]With Debian Stretch dropping 32-bit PowerPC as a release architecture, Ubuntu is following a similar maneuver and will not be making 32-bit PPC images of future releases.

Steve Langasek confirmed 32-bit PowerPC architecture will be removed from future Ubuntu releases. He commented, "the PowerPC port in Ubuntu has reached the end of its useful lifespan...The Technical Board has therefore determined that the powerpc port should not be included in the Ubuntu 17.04 (zesty) release. In support of this, powerpc will be dropped as an architecture in zesty as of Feature Freeze."

PowerPC 32-bit will continue to be supported for existing Ubuntu releases, including Ubuntu 16.04 LTS that still has a few more years of support (2021).[/quote]

Links:

[Ubuntu To Stop Building 32-Bit PowerPC For Future Releases]("http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-No-New-PPC32")
[Removing 32-bit powerpc architecture from future Ubuntu releases]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2016-December/001199.html")

-- Christian

---

### Post by rican-linux on 2016-12-22
I am not surprised this is happening.

---

### Post by xeno74 on 2016-12-23
Hi All,

Sad news. That means we won't get an official ubuntu MATE 17.04 release. I will update my installed development version of ubuntu MATE 17.04 as long as possible. After that I will try to release an unofficial ubuntu MATE 17.04 USB img for the X5000 and X1000.

The development version of ubuntu MATE 17.04 works very well on my AmigaOne X1000. :-)

ubuntu MATE 17.04 PowerPC with Mesa 13.0.2 and kernel 4.10 alpha5:&#65279;

[[IMG]https://lh3.googleusercontent.com/-FUO0oCkcljs/WFcQlhdR__I/AAAAAAAAEts/TVsRp6116IQVnqhSbzbBzIb2e43Cjm-_ACJoC/w530-h398-p/ubuntu_MATE_17.04_PowerPC_with_Mesa_13.0.2_and_kernel_4.10-alpha5.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/ZsdLrC9Gxd2")

By the way, the DNS service of systemd doesn't work correctly currently. Some web sites aren't accessible.

You can fix the problem with modifying the **/etc/resolv.conf**. I replaced the systemd DNS server with the Google DNS server ip address.

```

sudo vi /etc/resolv.conf

```

I replaced

```

nameserver 127.0.0.53

```

with

```

nameserver 8.8.8.8

```

After a restart, systemd overrides the **/etc/resolv.conf** with his DNS server again. The **/etc/resolv.conf** is a symlink to **/run/resolvconf/resolv.conf**. If you delete the symlink and create a file instead it's content should not be changed by resolvconf/systemd.


Rgds,
Christian

---

### Post by ernsteiswuerfel on 2016-12-23
How sad... :(

Well I guess it's time to go for Gentoo on my PowerBooks then. Works realy well on my G5 anyway.

---

### Post by rican-linux on 2016-12-24
Gentoo works my PB as well

---

### Post by xeno74 on 2017-02-13
Hi All,

Lubuntu and ubuntu MATE have stopped the building of the daily build ISOs for PowerPC but I was able to upgrade ubuntu MATE 17.04 PowerPC today.

Links:

[LIST]
[*][Lubuntu daily builds]("http://cdimage.ubuntu.com/lubuntu/daily-live/pending/") 
[*][ubuntu MATE daily builds]("http://cdimage.ubuntu.com/ubuntu-mate/daily-live/pending/") 
[*][Lubuntu 17.04 (Zesty Zapus) PowerPC Daily Build ISOs to No Longer Be Produced]("http://news.softpedia.com/news/lubuntu-17-04-zesty-zapus-powerpc-daily-build-isos-to-no-longer-be-developed-512659.shtml") 
[/LIST]

The developers of Lubuntu wants to remove the last PowerPC daily build in a few days.

[Lubuntu 17.04 (Zesty Zapus) PowerPC Daily Build ISOs to No Longer Be Produced]("http://news.softpedia.com/news/lubuntu-17-04-zesty-zapus-powerpc-daily-build-isos-to-no-longer-be-developed-512659.shtml")

I downloaded the last ISOs and uploaded them to my web space yesterday. 

Downloads:

[ubuntu_MATE_17.04_2017-02-09-powerpc.iso]("http://www.xenosoft.de/ubuntu_MATE_17.04_2017-02-09-powerpc.iso")
[Lubuntu_17.04_2017-02-08-powerpc.iso]("http://www.xenosoft.de/Lubuntu_17.04_2017-02-08-powerpc.iso")

The daily build ISO for the Ubuntu Server 17.04 PowerPC is still available. (zesty-server-powerpc.iso    2017-02-13 06:49     695M)

Link: [Ubuntu Server 17.04 (Zesty Zapus) Daily Build]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/")

It's very sad because ubuntu MATE 17.04 PowerPC (PPC32) works very well on our AmigaOnes and PowerMacs.

Screenshots of ubuntu MATE 17.04 PowerPC

On a PowerMac G5 Quad:

[[IMG]https://lh3.googleusercontent.com/-0PKiOUN-7K8/WHKcnM-lRjI/AAAAAAAAE8c/o2ojJQ1VOmEb7xZ7nEsRr3LIjSIPHSZRQCJoC/w530-h298-p/ubuntu_MATE_17.04_PowerPC_PowerMac_G5.jpg[/IMG]]("https://plus.google.com/115515624056477014971/posts/ZxTTTL1VygU")

On a new AmigaOne X5000:

[[IMG]https://lh3.googleusercontent.com/-Dt2dNP6K8kM/WJrvyHtcJFI/AAAAAAAAFYs/P6Q5HPYVGMMWwotpc4ZaRvTbpeWT0xP9wCJoC/w530-h298-p/Screenshot_at_2017_02_07_23_59_31.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/Mgi1PUmd4Fc")

With the new Firefox 50.1.0 on an AmigaOne X1000:

[[IMG]https://lh3.googleusercontent.com/-hWF4vIefCRU/WGk8TI016EI/AAAAAAAAE20/LY0WLg_YCkIZZeiOrIFucQKpybZq5E-PACJoC/w530-h398-p/ubuntu_MATE_17.04_PowerPC_Firefox_50.1.0.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/GjCRX8h6Y9F")

With the new Thunderbird 45.6.0 on an AmigaOne X1000:

[[IMG]https://lh3.googleusercontent.com/-ahdrNTVHXfg/WISXA5QsdYI/AAAAAAAAFGw/GmQl0BlXbXoxI3wFVOWUJo85LwjHdFvUgCJoC/w530-h398-p/ubuntu_MATE_17.04_PowerPC_with_Thunderbird_45.6.0.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/S4gKPCVusLs")

With the new MATE 1.17.2 on an AmigaOne X1000:

[[IMG]https://lh3.googleusercontent.com/-cUvoXursW98/WIJOiF8GOaI/AAAAAAAAFEc/rPFTFIxlszYQWgbjnSOSPk8OmJRI8uTNwCJoC/w530-h398-p/ubuntu_MATE_17.04_PowerPC_MATE_1.17.2_kernel_4.9.5.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/SPVARpKXAS5")

More screenshots: [https://plus.google.com/u/0/115515624056477014971]("https://plus.google.com/u/0/115515624056477014971")

ubuntu MATE 17.04 PowerPC test threads for AmigaOnes:

[(X)(L)ubuntu (MATE) 17.04 Zesty Zapus -- Platform: AmigaOne X5000 - Linux Only]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=58&t=3592")

[(X)(L)ubuntu (MATE) 17.04 Zesty Zapus -- Platform: AmigaOne X1000 - Linux Only]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3554")

Rgds,

Christian




&#65279;

---

### Post by este.el.paz on 2017-02-14
Folks:
  Downloaded a daily of 17.04 PPC alpha recently and a couple days ago  found the time to boot it up and give it a test run on my PowerMac 3,1 G4.  Initially there  were a bunch of I/O errors while booting up, which went on for awhile  until we finally got to cursor and GUI session--so that part was fine  and didn't require any boot params to get done.


  But, the "Welcome" screen appeared, however it was devoid of data;  Software Boutique was the same.  I believe that both of these apps  produced a crash report window, can't be sure since the crash window  opened a bit after launching the session--the first one said,  "Executable path--  /usr/lib/powerpc-linux-gnu/webkit2gtk-4.0/WebKitWebProcess" . . . with a  further error when I tried to upload the crash report that it generated  . . . "cannot connect to crash database-plz check internet connection."   I opened a Terminal and ran "ping google.com" and it showed connection  was fine.  Possibly something with apport that is not working?


  No Firefox or any web browser seemed included?
  There was, as mentioned, another crash as I tried to restart out of  the session, possibly from the Software Boutique app that opened to an  empty window--since it was logging out I didn't see if the report said  anything different than the first one.


  "Restart" goes to a blinking cursor on black background . . . "failed  deactivating swap" . . . and then didn't restart after the disk was  ejected--had to hit the power button to shut down.
  That's the report from PPC-land for 17.04 U-MATE, some things like  basic GUI were fine out of the box, but, still very "Alpha" in nature.  Possibly there will be no further efforts made on PPC distros, but, as Xeno mentioned . . . "that is sad" because the computers are still generally working quite well for basic applications and the users are still there.

e.e.p.

---

### Post by luigiburdo on 2017-02-15
I installed it on G5 quad and there is issue with usb . pratically keyboard and mouse dont work on lightdm after installation
I try to swap the kernel with lastest rc without positive result.
I hope will be able to disable lightdm for check if in terminal will be no issue if not mate 17.04 will be out for G5 quad .... 
What i dont understand is : ok you need to kill the ppc32 be but why you kill ppc64 be to? no PPC64 ubuntus at all ... and there are many machine new too ppc64 .
Really bad, really bad at all

---

### Post by este.el.paz on 2017-02-18
> **luigiburdo said:**
> 
What i dont understand is : ok you need to kill the ppc32 be but why you kill ppc64 be to? no PPC64 ubuntus at all ... and there are many machine new too ppc64 .
Really bad, really bad at all

@luigib:

From my post on the U-MATE forum it is very clear that they will be dropping support for PPC 17.04 shortly.  However, another mod there posted a link to "some options" for PPC . . . Debian . . . which of course we know is the reason why ubuntu is dropping support; OpenSUSE, which to my knowledge never had a PPC distro; and finally Fedora . . . hmmm, Fedora, maybe they will have support for PPC?  I clicked on the link and the info page shows "F-25" or F-26???  And it says that they haven't supported 32 bit since F-17??  But they do support 64 bit PPC "big-endian" . . . G5 . . . and then went on to mention "Power 7" and "Power8" as supported . . . .

Unfortunately my PPC machines are 32bit . . . so, if I want U-MATE DE I'll have to re-install 16.04 at some point, or just continue with the XFCE DE that was left "alive" after the DE upgrade failed . . . .  For those of you who have G5 or 64 bit PPC, perhaps Fedora will be the way "forward"???  Seems like they offer "spins" with all of the popular DE's . . . .  Hope that helps . . . 

e.e.p.

---

### Post by luigiburdo on 2017-02-19
hi este,
you true but was im thinking is about new powerpc 64 BE machines, i was not only thinking about powermacs. there are many emb too. 32bit are small parts today in  the scene.
this made me creazy about they totally cut a support of one architecture because are leazy.

---

### Post by ernsteiswuerfel on 2017-02-19
@este.el.paz, luigiburdo:

If you want current software & kernels on you ppc-hardware you can always run Gentoo. stable and testing packackes are a bit behind amd64, but not much. At default settings it does not run MATE and LibreOffice (you have to stick to XFCE4 or Openbox), but you can add that easily. Been running MATE 1.16 under Gentoo for months on my G5 and it works well. The only downside is that it take **much** compile time to build the system on a G4. :D It took my G5 a day to get to the MATE desktop and another one for LibreOffice and Otter-Browser.

But on the other hand, Ubuntu MATE 16.04.2 works comfortably too. And due to more recent mesa & kernel some driver-bugs are gone.

---

