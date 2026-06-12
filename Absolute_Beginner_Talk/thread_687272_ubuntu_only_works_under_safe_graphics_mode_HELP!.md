---
title: "ubuntu only works under safe graphics mode HELP!"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Shaun440 on 2008-02-04
Ok i recently had trouble getting ubuntu to work off the live CD, but I finally got it (with some help from you forumers :) (see my last thread) but it will only work under safe graphics mode. I was wondering if this will affect the install and if after it is installed, will linux booting from the hard drive only work under safe graphics mode?

Cheers
Shaun

---

### Post by oedha on 2008-02-04
it will be helped if you mention your display adapter, 
maybe your display card is restricted or need to be tweaked later when the installation finished

---

### Post by xpod on 2008-02-04
> Ok i recently had trouble getting ubuntu to work off the live CD, but I finally got it (with some help from you forumers (see my last thread) but it will only work under safe graphics mode. I was wondering if this will affect the install and if after it is installed, will linux booting from the hard drive only work under safe graphics mode?

Your fine.....
If you have a decent card then use the Resticted Drivers manager in your menus and if not then open a terminal....applications>accesories>terminal and type in(copy/paste)
```
sudo dpkg-reconfigure xserver-xorg
```

Hit enter then you will see a screen pop up offering to detect your GFX(Video Hardware) for you.
Say "yes" then just accept the defaults for everything else,although you might want to choose your correct resolution once at that stage of things......use the up/down arrows & space bar to chose your desired resolution then carry on accepting the defaults.

Tab enter,tab enter,tab enter.
Thats how i do it anyway:)

EDIT:If your not sure what GFX or Hardware you have you can use
> lspci
For devices

And...
> lshw
For a more complete list of all your hardware

Again,in the terminal ;-)

---

### Post by Shaun440 on 2008-02-04
ok i tried that, and it says to pick my "X server driver". what do i choose there?

btw, i have a galaxy 8800GTS 512 (g92) graphics card :)

---

### Post by xpod on 2008-02-04
You can choose the open source NV driver for now.........then finish the rest of the re-configuring procedure,just choosing the defaults untill you get to the Res stage.
Once thats all finished hit CTRL-ALT-Backspace to reboot your X-Server(display). 
If all is well then you can go to System>Administration>Restricted Drivers Manager and install the propriety Nvidia drivers.

Once thats done you will then be told to restart your machine.......and bingo,your up and running.
In theory of course:)

Your getting there though=D>

EDIT:You should have a little green icon on the right hand side of your top panel indicating the Restricted Drivers Manger too.
Just click on it:-)

---

### Post by Shaun440 on 2008-02-04
ok thanx for all your help :) i'll try all this out and if i find another problem, i'll get back to you :)

cheers

---

### Post by xpod on 2008-02-04
> ok thanx for all your help  i'll try all this out and if i find another problem, i'll get back to you


As long as your card is compatible....which i believe it is then you dont even need to do the "sudo dpkg-reconfigure xserver-xorg" part as the safe(vesa) driver will suffice until you download the Restricted Nvidia driver,via the Restricted Drivers Manager.

IF you have any compatible wireless card then their drivers  should also be installed by the Restricted Drivers Manager as far as i understand.

Bar the laptops i just plug my wireless usb adapters in and i`m off & running although i rarely use the wireless.....unless i`m doing my "penetration testing",as i tell my better half.

*That* one always gets a response.......or a slap:)

---

### Post by Shaun440 on 2008-02-04
yeah well the restricted driver manager says: your hardware does not need any restricted drivers

---

### Post by xpod on 2008-02-04
>  yeah well the restricted driver manager says: your hardware does not need any restricted drivers


You could try Envy then
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Mabey someone else knows more about that particular card in Ubuntu/Linux than i obviously do.:)

EDIT:The only time i`ve been told i dont need any restricted drivers like that is when the actual card has been quite old or it`s been some basic onboard type.

---

