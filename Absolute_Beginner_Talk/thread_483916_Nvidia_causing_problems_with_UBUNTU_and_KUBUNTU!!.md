---
title: "Nvidia causing problems with UBUNTU and KUBUNTU!!"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by mediapc on 2007-06-25
This is my 1st post, so please accept my apologies if i don't make sense as i'm a total newbie to LINUX.

Okay here i go....

I'm trying to setup LINUXMCE on my pc. I've so far installed UBUNTU twice as I seem to be having problems with the nvidia driver. I even tried switching to the standard open source driver, but this too doesn't make a difference and UBUNTU ends up crashing just before the desktop appears.

I then read that i need to use KUBUNTU and LINUXMCE 1.1 as this has had some bugs fixed. Currently i've just installed KUBUNTU, but i'm still having serious problemS with the nvidia drivers. If I don't install them, the linuxmce won't run, but if i do install them, kubuntu crashes! I don't want to go back to windows vista, so what can i do??? 


My system specs are:-

INTEL E6300
ASUS P5B MOBO
POV NVIDIA 8800GTS (320mb)
1GB RAM
2 X 250GB HDD
NEC OPTIARC DVD-RW

**_PLEASE REMEMBER THAT I'M A TOTAL NOVICE TO LINUX, SO I WOULD BE MOST GRATEFUL IF YOU CAN GIVE ME HELP STEP-BY-STEP!!! - Thank You!_**

---

### Post by testube_babies on 2007-06-25
I might be wrong, but I don't think the 8000 series is supported by the drivers that are offered in the repositories.  Have you tried installing nVidia drivers using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

---

### Post by mediapc on 2007-06-25
> **testube_babies said:**
> I might be wrong, but I don't think the 8000 series is supported by the drivers that are offered in the repositories.  Have you tried installing nVidia drivers using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

Thank you testube for your fast reply.

I haven't tried envy.  A few questions mate:-

1. How do i install it? 
2. Will it work with both ubuntu and kubuntu?
3. After installing to i still need to install any nvidia drivers?
4. Anything else i should know?

Thanks

---

### Post by mediapc on 2007-06-25
PLEASE PLEASE Someone help me as i'm stuck and can't do anything.

Thanks!

---

### Post by neo.patrix on 2007-06-25
NVIDIA causing problem? can't believe it... i have got ATI card. 

I had to clean my entire system recently, I had started using ubuntu with 6.06 LTS, then upgraded it to 6.10 and finally 7.04 , so i had now idea about any problems with LiveCd for Feisty and ATI cards

I finally realized that it was going to cost me enough, i wasted nearly one day working out how to reinstall feisty fawn with LiveCd and Alernate CD. I can use only WLAN, on my Dell Notebook even that is a problem because driver for my WLAN card INTEL 3945 (I think) is also "Restricted" ! God Bless me!!. SO i had no graphics ,because driver for that is restricted , "vesa" is broken with lastest version of Xorg which feisty uses. 

So I had no internet and no graphics!! finally i decided to install Ubuntu 6.10 and then upgrade it to Feisty. ](*,)

---

### Post by mediapc on 2007-06-25
The problems seems to be that nvidia 8800 might not be compatible, but how can i be sure?  Anyone else help me please!!!

thanks

---

### Post by Nekiruhs on 2007-06-25
Just download the .deb off the link given. Click envy on the System Tab, and select install nvidia driver. It detects your card and compiles the porper driver.

---

### Post by bodhi.zazen on 2007-06-25
> **mediapc said:**
> The problems seems to be that nvidia 8800 might not be compatible, but how can i be sure?  Anyone else help me please!!!

thanks

LOL

If you post the exact error message you are getting or the logs we can help decipher them, but that may be more hassle ...

As has been pointed out, the envy script will work for you :

Here is a similar thread with the solution (step-by-step directions to install the nvidia driver from the command line with envy).

Let us know if you get stuck.

---

### Post by BobLand on 2007-06-25
Mediapc,
I feel your pain.  
Envy is locate here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

When you get there, click on this link
envy_0.9.5-0ubuntu4_all.deb

Worst thing to happen is nothing will happen.

---

### Post by mediapc on 2007-06-25
@ bodhi.zazen - thank you for your help.  As you'll be aware i'm a total newbie to linux, so commands or telling me names of applications will be totally mind-boggling :(

Do i need to use kubuntu or ubuntu with ENVY?

Will using the step-by-step guide allow me to use the nvidia 8800gts gfx card or is that not supported?

Also unfortunately there is no link you gave to that step-by-step guide.

Thanks for helpin

---

### Post by bodhi.zazen on 2007-06-25
Oh, sorry :redface:

here is the link :

[http://ubuntuforums.org/showthread.php?t=482096](http://ubuntuforums.org/showthread.php?t=482096)

See post #3

Works with any version of Ubuntu (K/X/Edu/Ubuntu/Fluxbuntu)

The OP in the link reports success.

If you send me your video card I would be happy to take it for a spin and let you know ;)

---

### Post by mediapc on 2007-06-25
hi, sorry about this, but when i click on the envy_0.9.5.deb file on the ENVY website, kubuntu opens an application called kate 2.5.6 (word processor???).  I even tried downloading the file to the desktop and right-clicking and install package.  This results in a window opening and loads of errors showing up.

Sorry..did tell you i'm a total novice.

---

### Post by testube_babies on 2007-06-25
What are the errors it prints out?

---

### Post by Phixion on 2007-06-25
go into terminal (apps > terminal) and type:

```

sudo dpkg -i envy_0.9.5.deb

```

---

### Post by Nekiruhs on 2007-06-25
I know what you speak of. Open the program above. System > Konsole. And type ```
sudo apt-get -f
```That will install it.

---

### Post by testube_babies on 2007-06-25
I believe that should be
```
sudo apt-get **install** -f
```

---

### Post by mediapc on 2007-06-25
right guys, thank you, but you have completely lost me, lol.  Do i download the ENVY program? if so, where do i place it? on desktop?  Also if i use the Konsole, do i need to change directory to DESKTOP, so that the command can find the ENVY.0.9.5.DEB file?

Lastly can you please confirm the full command i need to type as there are 3 different answers there.

Many thanks for your superb support!

---

### Post by testube_babies on 2007-06-25
Alright.  This should take care of everything for you, from downloading the file to installing the driver, all in the konsole:

System -> Konsole
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.5-0ubuntu4_all.deb
sudo dpkg -i envy_0.9.5-0ubuntu4_all.deb
sudo apt-get install -f
sudo envy -t
```

..from there it should hopefully be self-explanatory.

Note:  sudo dpkg -i envy_0.9.5-0ubuntu4_all.deb may spit out errors, but sudo apt-get install -f fixes them.

Note2:  make sure you have [extra repositories ]("http://kubuntuguide.org/Feisty#Add_Extra_Kubuntu_Repositories")enabled

---

### Post by mediapc on 2007-06-25
thanks ttbabies...i typed all the commands you mentioned.  I eventually got to the GUI menu.  I chose option 1 to install Nvidia drivers.  After a while and a few questions, it asked me if i would like to restart X server.  I replied YES. Kubuntu reloaded, showing the logo.  But after this came a blank screen with a _ PROMPT showing.  Nothing happened..i could type anything on the blank screen.  What is wrong here?

---

### Post by testube_babies on 2007-06-25
Did anything weird happen before/after you got to the prompt screen? (ie errors)
Did you eventually get back to the normal GUI?  If you did, then it probably installed the drivers correctly.

---

### Post by mediapc on 2007-06-25
> **testube_babies said:**
> Did anything weird happen before/after you got to the prompt screen? (ie errors)
Did you eventually get back to the normal GUI?  If you did, then it probably installed the drivers correctly.

Nothing out of the ordinary happened mate..I waited for about 5 mins and no GUI came up.  But I could press ALT + F1 and get the login, although even after login, i never get the GUI.

...I'm tearing my hair out..thinking to goto vista mce...i thought it won't be that hard, but boy oh boy, this is a real cracker! :o

---

### Post by bodhi.zazen on 2007-06-25
Go the the terminal (Ctrl-Alt-F1)

Log in

Enter these commands to configure X (For now , X = you gui [oversimplification]):

```
sudo /etc/init.d/kdm stop
sudo nvidia-xconfig
sudo /etc/init.d/kdm start
```


========



Once your gui starts, use the nvidia tool to configure X (resolution) if needed :

Open a terminal (konsole) and enter :

```
kdesu nvidia-settings
```

If you like the new settings select "save settings" ;)

---

### Post by testube_babies on 2007-06-25
Well, it looks like your trouble goes further than just driver installation.  To get back to the GUI, login then:
```
 sudo nano /etc/X11/xorg.conf
```
look for Driver "nvidia" and change to Driver "vesa" (or whatever driver you were using before).  CTRL-X will save the file.  Then "sudo reboot" to restart.

---

### Post by mediapc on 2007-06-25
right, so who do i follow 1st?  bodhi or babies??? lol

---

### Post by bodhi.zazen on 2007-06-25
I am assuming you missed the screen to configure X, so re-try that first.

If that fails, go back to the vesa driver. You do not need to reboot.

Just :```
sudo /etc/init.d/kdm restart
```

Actually you can probably restore xorg form backup (the nvidia installation makes a backup of xorg, look in /etc/X11/ and "sudo mv /etc/X11/xorg.conf<backup> /etc/X11/xorg.conf" )

then post xorg.conf

---

### Post by burt_57 on 2007-06-25
> **mediapc said:**
> This is my 1st post, so please accept my apologies if i don't make sense as i'm a total newbie to LINUX.

Okay here i go....

I'm trying to setup LINUXMCE on my pc. I've so far installed UBUNTU twice as I seem to be having problems with the nvidia driver. I even tried switching to the standard open source driver, but this too doesn't make a difference and UBUNTU ends up crashing just before the desktop appears.

I then read that i need to use KUBUNTU and LINUXMCE 1.1 as this has had some bugs fixed. Currently i've just installed KUBUNTU, but i'm still having serious problemS with the nvidia drivers. If I don't install them, the linuxmce won't run, but if i do install them, kubuntu crashes! I don't want to go back to windows vista, so what can i do??? 


My system specs are:-

INTEL E6300
ASUS P5B MOBO
POV NVIDIA 8800GTS (320mb)
1GB RAM
2 X 250GB HDD
NEC OPTIARC DVD-RW

**_PLEASE REMEMBER THAT I'M A TOTAL NOVICE TO LINUX, SO I WOULD BE MOST GRATEFUL IF YOU CAN GIVE ME HELP STEP-BY-STEP!!! - Thank You!_**

look at this site.....it solved my problem
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

---

### Post by mediapc on 2007-06-26
Hello guys and let me say a big thank you to all those who tried to help.  Kubuntu has now booted with nvidia drivers enabled and to check if this is correct, I installed Beryl to do a test and the 3D screen rotation works.

Just for those who are wondering how i fixed it.  You'll be disappointed to know that i didn't do anything.  I just retried to boot, hoping to type the commands you experts have given, but it booted straight to the desktop!

Anyway I still have more issues which are unrelated to this, so i'll start a new thread for that.

Oh there is one issue though...When installing LinuxMCE, i did a graphics test.  I can't get Composite affect and it seems as though the graphics are corrupt...can this be fixed???

Thanks ever so much!

---

