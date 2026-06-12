---
title: "Changing graphic card, how do I install it in Feisty"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by boyturtle on 2007-05-02
New to the whole Linux thing and loving Feisty, but its all a bit strange to me and learning is proving arduous and slow!!

Was having all sorts of problems with my Radeon 9550, finally got it to work nicely, but sadly it doesnt support composite extension so no really nice graphics for me (really like those wobbly windows). So have decided to take the jump and get a GeForce 7300GT and have to admit that I havent got a clue what to do about the install

I could do it windows, no problem, but this is an all together different animal. Can someone give me a step by step instruction on what to do or point me to a link with full instructions. I already have the latest driver downloaded from nvidia. The card is in the slot and i am about to boot up; grub will give me the choice of ebuntu regular or recovery mode; what next?:confused:

Thanks guys, envy worked a treat. You rock :guitar:

---

### Post by viciouslime on 2007-05-02
When you select a normal boot, does ubuntu actually load? If so it is simply a case of logging in, going to system/administration/restricted drivers and ticking the box "enable" then pressing ok.

If ubuntu fails to boot and drops you into a command line, then try running: sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by bodhi.zazen on 2007-05-02
Boot ubuntu normally.

Enter these commands, either at the terminal or command line :

```
mkdir -p ~/src/envy
cd ~/src/envy
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu5_all.deb
sudo dpkg -i envy*
sudo apt-get install -f
sudo dpkg -i envy*
sudo envy -t
```

Yes, I know sudo dpkg -i envy is in there twice ...

Then, in a terminal, type ```
envy -t
```

Select install nvidia driver :)

restart X ~ log out, at the log in screen type Ctrl-Als-Backspace

Then, in a terminal : ```
gksudo nvidia-settings
```
Set up your monitors for twinview, set the resolutions, ect, then click the "save 							settings" button.

---

### Post by tcrroadie on 2007-05-02
I'm not at my Feisty install at the moment, but if I remember correctly, the proprietary Nvidia driver should be in Ubuntu's repositories.  

If when initally booting Ubuntu you are droped to a terminal, simply login and install the proprietary nvidia driver. 

If you like, you can first search Ubuntu's repositories to see if the Nvidia driver is actually there.  

```
sudo apt-cache search nvidia
```

You should get a listing for a package called nvidia-glx (if I am remembering correctly) which is the Nvidia graphics driver.  

Then you can insall the Nvidia driver by running 

```
sudo apt-get install nvidia-glx
```

Next you will need to reconfigure your xorg.conf file. 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Next restart your machine.  

```
sudo reboot
```

If the Nvidia graphics driver installed properly and the xserver was reconfigured correctly to use your Nvidia driver, you will see a Nvidia splash screen when your xserver starts up, just before the login manager comes up.   

If not, you will need to edit your /etc/X11/xorg.conf file to change your video driver to nvidia.

As for Beryl on Feisty.  Please see the link below on instructions for installing Beryl and setting up your xserver for Beryl and Nvidia. 

[Installation of Beryl on Feisty ]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia")

---

