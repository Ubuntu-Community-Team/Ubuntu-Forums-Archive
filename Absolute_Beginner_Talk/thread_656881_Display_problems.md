---
title: "Display problems"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by gundam_v6 on 2008-01-03
Dear All Friends in Forum
Sory if my english not good.

My Name Eddo, i'm using Distro Ubuntu 7.10. and i'm using laptop
BenQ R42E, Proc Celeron, VGA VIA/S3 P4M890, but until now, i'm still can't config my display, i ready contact VIA support, then they give me link : [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=169](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=169) 
OS : LINUX UBUNTU 7.10
Proc : Celeron 1.6
Laptop : BenQ R41E
Chipset VGA : VIA/S3 P4M890 UniChrome Pro integrated graphics 
 
If some one can give me a solution, i promise to give some think from BALI, INDONESIA.
PLEASE HELP ME............................

Tks........
this is my personal e-mail : *remove*

---

### Post by ~LoKe on 2008-01-03
Open up a terminal and type this:
```
sudo dpkg-reconfigure xserver-xorg
```
It should give you step by step choices on how you want it configured.

---

### Post by RomeReactor on 2008-01-03
Hi. Are you having problems with your screen resolution, or you don't have a display? If your problem is not being able to use desktop effects or play 3D games, that's because of the integrated VIA video card; there are no Linux drivers for that card that can do that.

---

### Post by ahaslam on 2008-01-03
> **RomeReactor said:**
> Hi. Are you having problems with your screen resolution, or you don't have a display? If your problem is not being able to use desktop effects or play 3D games, that's because of the integrated VIA video card; there are no Linux drivers for that card that can do that.

Wrong, only for the k8(m/n)800 (due to bugs). He needs help installing what's linked, which is harder than it should be.

PS. I'd see if the openchrome driver suits your needs before you get your hands dirty with this.
```
sudo apt-get install xserver-xorg-video-openchrome
```

---

### Post by ahaslam on 2008-01-03
Your're lucky, there's also a binary for your chipset:
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=169](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=169)

You should: 
Extrtact it, backup your xorg.conf, execute the .run file & Ctrl-Alt-Bckspce.

But do try openchrome 1st ;)

---

### Post by gundam_v6 on 2008-01-04
Dear All, 
My Problem is, i can't change my Resolution to Wide Screen, only 600x800.

i can't change my grapich drive ti VIA/S3, i already to contact the VIA, then they give me the Link 
[http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=169](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=169) 
i already try down load all from that link, but what i must to do?because this is my First linux, i don't know how to installed.

Please help me, standart config for my grapich card is Vesa, but my Chipset is VIA P4M890 IGP.

PLease.....Please..... ok may be some one can Chat with me using YM??
please send message if some one ready to chat +62-361-8584606

---

### Post by RomeReactor on 2008-01-04
Try ~LoKe's suggestion: Press CTRL+ALT+F1 to switch to a terminal; then make a backup of your current configuration:
```
sudo cp /etcX11/xorg.conf /etc/X11/xorg.conf.backup
```
this will make a backup of your configuration, called **xorg.conf.backup**; then:
```
sudo /etc/init.d/gdm stop
```
to stop the Gnome Display Manager; and finally:
```
sudo dpkg-reconfigure xserver-xorg
```
accept the defaults it suggests, and when you get to the resolution screen, make sure the ones you want are marked; if not, press the UP or DOWN arrows to highlight the one you want and press the SPACE bar to mark them (can't remember if this is the correct way to select them; someone else might comment with the correct method). Once it finishes, your display should start automatically. If it doesn't, enter:
```
startx
```
or:
```
sudo /etc/init.d/gdm start
```
or reboot:
```
sudo reboot
```

If for any reason you're not satisfied with the changes and want to revert to the previous configuration, open a terminal and run:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
then press CTRL+ALT+BACKSPACE to restart the display; or reboot the system.

---

### Post by ahaslam on 2008-01-04
That link is the source version of the binary I linked. The difference is that If you were to run Ubuntu Desktop 6.10/7.04 you'd get 3D support with the compiled source. As you're running 7.10, I'd recomend that you try the binary I posted if you really want Via's own driver.

Honestly though, the openchrome driver will prove much better. Not only because Via's drivers are tripe, but you should also be able to get 3D with the mesa package. More info here: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by ahaslam on 2008-01-05
Seriously, use the Openchrome driver.

With the premise of 3D for the notorious K8M800, I borrowed my old laptop & tried the source. It didn't go well: [http://www.linuxquestions.org/questions/linux-hardware-18/unichrome-xorg-40072d-display-driver-611022/](http://www.linuxquestions.org/questions/linux-hardware-18/unichrome-xorg-40072d-display-driver-611022/)

:(

---

