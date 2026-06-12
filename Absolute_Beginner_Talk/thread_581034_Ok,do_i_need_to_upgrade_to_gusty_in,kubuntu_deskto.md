---
title: "Ok,do i need to upgrade to gusty in,kubuntu desktop"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-10-19
i have ubuntu fiesty fawn,i updated last nite to gutsy  7.10
i have an error and it will not boot, 
i get busybox  v1.1.3/debian 1.1.1.3-5ubuntu7 built in shell (ash)

anyway i have managed to boot  @ grub,  
i can also change desktop to kubuntu,

any1 have any ideas how i can boot up normally   :confused:

thanks

---

### Post by skymera on 2007-10-19
you can stay at feisty for as long as you want.

updates carry on for another year? or half a year?

but you can stay :wink:

---

### Post by bapoumba on 2007-10-19
Hmm, did you upgrade on a separate partition? What do you mean stating you still have feisty? The feisty kernel? What  is your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by nikef on 2007-10-19
> **skymera said:**
> you can stay at feisty for as long as you want.

updates carry on for another year? or half a year?

but you can stay :wink:

thanks,i want to move on to gutsy

---

### Post by nikef on 2007-10-19
> **bapoumba said:**
> Hmm, did you upgrade on a separate partition? What do you mean stating you still have feisty? The feisty kernel? What  is your sources.list?
```
cat /etc/apt/sources.list
```


thanks,here is my sources list

## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
# deb [http://falcon.landure.fr](http://falcon.landure.fr) feisty pidgin
# deb-src [http://falcon.landure.fr](http://falcon.landure.fr) feisty pidgin


i tried to upgrade the kubuntu desktop,and it starts then tells me i am up to date :confused:

---

### Post by nikef on 2007-10-19
Any1 got any ideas as to what went wrong

when i turn on pc,it starts to load into the kubuntu splash then just sits there

i leave it and get this error 

Busybox v1.1.3/debian 1.1.1.3-5ubuntu7  built in shell (ash)     :confused:

---

### Post by Garfeild on 2007-10-19
I think, i have the same trouble.
What you see, when make in busybox this:
```
ls /dev |grep sd
```

---

### Post by Frak on 2007-10-19
run
```
sudo editor /etc/apt/sources.list
```
Then remove the # signs in front of
> # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
so it looks like
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse


Then press Ctrl+x, y, enter

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by nikef on 2007-10-19
> **Frak said:**
> run
```
sudo editor /etc/apt/sources.list
```
Then remove the # signs in front of

so it looks like


Then press Ctrl+x, y, enter

```
sudo aptitude update
sudo aptitude upgrade
```



Hi Frak 
when i enter sudo editor /ect/apt/sources.list

i get some thing different to what i posted earlier ,here is the list 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main $
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
                               [ Read 50 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by Frak on 2007-10-19
OK, nevermind then. I'll think of something ;)

---

### Post by nikef on 2007-10-19
ok,thanks for your help  :)

---

### Post by Frak on 2007-10-19
run
```
lsb_release -a
```
and paste the output

And restate your problem, as I've gotten lost.

---

### Post by nikef on 2007-10-19
here is what you asked for,my problem is i updated to gutsy last night,but it will not load,the splash screen comes up then i get an error message saying 
Busybox v1.1.3/debian 1.1.1.3-5ubuntu built in shell (ash)


trish@trish-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
trish@trish-desktop:~$ 


thank you so much for trying to help me :)

---

### Post by Frak on 2007-10-19
run
```
startx
```

And paste the output. I suspect an X issue.

---

### Post by nikef on 2007-10-19
Sorry but my terminal will not open  :confused:

---

### Post by Frak on 2007-10-19
> **nikef said:**
> Sorry but my terminal will not open  :confused:
Do you have a GUI, or are you stuck at the CLI?

---

### Post by nikef on 2007-10-19
> **Frak said:**
> Do you have a GUI, or are you stuck at the CLI?

ok,i am not sure what u meen,i have pressed escape @ grub,it gave me option to boot into,a couple would not work,but the one i am in in now looks like ubuntu ,with some gutsy icons,like the little green man for log off ,switch user and some of my other icons have changed,anyway i logged out and back in to get my terminal to work again,here is the out put you wanted 

trish@trish-desktop:~$ startx
xauth:  creating new authority file /home/trish/.serverauth.27897
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console
trish@trish-desktop:~$

---

### Post by Frak on 2007-10-19
GUI is the Graphical User Interface, while the CLI is the Command Line Interface.

Other than that, stumped.

---

### Post by Lord_Dicranius on 2007-10-19
First off, I'm no X guru at all, I'm just trying to help out here haha  But you could try and run the code below to reconfigure the X server:

```

sudo dpkg-reconfigure xserver-common

```

Got that idea after seeing this:
> X: user not authorized to run the X server, aborting.
...in the error above when you tried to run the "startx" command.

---

### Post by nikef on 2007-10-19
> **Frak said:**
> GUI is the Graphical User Interface, while the CLI is the Command Line Interface.

Other than that, stumped.

its the gui as i can see my desktop and all my applications

thank you for trying to help,i have confussed you and also my self :confused:

---

### Post by Frak on 2007-10-19
> **Lord_Dicranius said:**
> First off, I'm no X guru at all, I'm just trying to help out here haha  But you could try and run the code below to reconfigure the X server:

```

sudo dpkg-reconfigure xserver-common

```

Got that idea after seeing this:

...in the error above when you tried to run the "startx" command.
I was going to suggest that, but since he's in the GUI, there's no point really.

---

### Post by Lord_Dicranius on 2007-10-19
> **Frak said:**
> I was going to suggest that, but since he's in the GUI, there's no point really.
Ah, gotcha :)

---

### Post by nikef on 2007-10-22
Thanks guys,so does any1 have any ideas :confused:

---

### Post by Frak on 2007-10-22
Try
```
sudo aptitude reinstall usplash
```

When I was trying to help before, I was helping seven people at once, but now I actually read and understood it, I should be able to help fix this pretty simply.

---

### Post by nikef on 2007-10-23
Thankyou
i have done that ,it installed lots of stuff,i re-booted and its still the same :confused:

do you think i should close this post and make a new one more clearer ,as at the time of making it,i thought i was still booting into fiesty fawn,but i am not 
i am booting into gutsy 7.10 ?

trish

---

### Post by Frak on 2007-10-23
> **nikef said:**
> Thankyou
i have done that ,it installed lots of stuff,i re-booted and its still the same :confused:

do you think i should close this post and make a new one more clearer ,as at the time of making it,i thought i was still booting into fiesty fawn,but i am not 
i am booting into gutsy 7.10 ?

trish
Click the REPORT button at the top of your post and tell the mods to rename it.

Try
```
sudo update-alternatives --config usplash-artwork.so
```
and choose the right value (there should only be one)
then
```
sudo update-initramfs -u
```

---

### Post by nikef on 2007-10-24
Thanks i did the first bit in the konsole,but not sure what to do here 

have copied and pasted,could you tell me what to do please 

trish@trish-desktop:~$ sudo update-alternatives --config usplash-artwork.so
[sudo] password for trish:

There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/usplash/usplash-theme-ubuntu.so
          2    /usr/lib/usplash/usplash-theme-xubuntu.so
*+        3    /usr/lib/usplash/usplash-theme-kubuntu.so

Press enter to keep the default[*], or type selection number:

---

### Post by nikef on 2007-10-24
ok,please read first post again
i am very sorry for the confusion ,i confussed my self   :confused:
but now i am a lot clearer as to whats happening 

thanks

---

### Post by Frak on 2007-10-24
try
```
sudo dpkg-reconfigure busybox-initramfs
```

Also, never uninstall it, it will cause your system to not boot.

---

### Post by nikef on 2007-10-25
thanks,i did this in konsole

sudo dpkg-reconfigure busybox-initramfs

it asked for password,i entered it,but nothing came up :confused:

---

### Post by Frak on 2007-10-25
> **nikef said:**
> thanks,i did this in konsole

sudo dpkg-reconfigure busybox-initramfs

it asked for password,i entered it,but nothing came up :confused:
Reboot and see if it works now. dpkg-reconfigure basically resets the package back to factory default settings.

---

### Post by nikef on 2007-10-28
sorry i have not been on for a few days ,been busy

i re-booted and its still the same  :confused:

thanks for sticking with me on this
i can't understand the problem here,because in fiesty fawn,it booted just fine,the only problem i had on that was,it would not shutdown properly ,i get the same in gibbon :confused:

---

