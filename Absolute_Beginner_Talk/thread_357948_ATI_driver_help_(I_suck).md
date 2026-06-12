---
title: "ATI driver help (I suck)"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by jexdawg13 on 2007-02-10
First off: I am, as many new users are, ubuntu-retarded. So... keep that in mind.

I'm trying to install my ATI drivers so I can turn direct rendering on, as when I run glxinfo it says "Direct rendering: no". I don't have any noticeable problems but I'd like to start Beryl soon, and I need that direct rendering on.

I've tried a lot of the guides and I always seem to encounter problems right away - though I assume I messed something up, as the guides seem to work for others.

I'm using the following guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

The first thing it does is tell me to do "sudo gedit /etc/X11/xorg.conf" in terminal, and when I do it prompts me for a password, then doesn't allow me to type mine in. The only thing I can hit is enter, which prompts me for the password again and still disallows me access to any key save enter. 

So since I can't use that command, I open it manually (which took a bit of searching.... this really is a different OS than windows, haha) and edit the lines they require into the bottom, save, close, and continue.

The next line to enter is "sudo apt-get update" which I do. It prompts me for my password, I can't type it for two attempts, and then, after telling me that it is sorry and wants me to try again, it does the command anyway.  ...? Moving on...

I do the next lines mostly without a hitch, though "sudo depmod -a" doesn't do anything.. should it?

I run sudo gedit /etc/default/linux-restricted-modules-common and edit the value to disable the value so it looks like: DISABLED_MODULES="fglrx". Save, exit, continue.

For some reason my pre-command-line thing (the bert@berts-computer: ~/ etc) is gone, so I open up a new terminal and fire away the sudo dpkg -i xorg-driver-fglrx_8.33.6-1*.deb to install the debian packages (damn I sound sophisticated... debian packes... i am 1337, haha). It prompts me for my password again and still won't let me enter it. Oh well. This time, though, I can't seem to get anywhere. This happens:

bert@berts-computer:~/easyubuntu$ sudo dpkg -i xorg-driver-fglrx_8.33.6-1*.deb
Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt

So it appears I'm stuck. Any advice? Am I doing this all wrong? Is it time for me to see sunlight yet?

Thank you in advance, you kind, kind, e-folk. May the power to assist be with you.

---

### Post by konst88 on 2007-02-10
When sudo asks for passwords, you dont see the password on the screen.
Just type it and press enter.

---

### Post by Zzl1xndd on 2007-02-10
it wont display any thing when you go to put in your password just try typing it all.

(beaten to the punch)

---

### Post by Maestro23 on 2007-02-10
Stranger behavior indeed.  You are typing the password that you created during the install right?  Remember, it will not display or move the cursor when you type in your password.

I followed that guild myself for setting up my ATI X1600 with no probs, but I have read where others have problems following the guides as well.

I have seen many people post and say they use Envy.  Can be found here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jexdawg13 on 2007-02-10
Thanks guys. I didn't know about the password thing.

I redid the line trying to install the .deb file ( sudo dpkg -i xorg-driver-fglrx_8.33.6-1*.deb) and it says:

bert@berts-computer:~/easyubuntu$ sudo dpkg -i xorg-driver-fglrx_8.33.6-1*.deb
Password:
dpkg: error processing xorg-driver-fglrx_8.33.6-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.33.6-1*.deb


Errr....? 

(Also, thanks a lot for the speedy replies)

EDIT: Wow, Envy look great! I'll give that a try, thanks Maestro.

---

### Post by Maestro23 on 2007-02-10
No prob man, hope it works for you.

---

### Post by jexdawg13 on 2007-02-10
Alright, you guys are going to hate me for this, but I seriously am noobtastic.

I downloaded Envy and installed the package... now where is it? How do I run it? Did it already run? Sorry for rapid-fire posting.

EDIT: NVM figured it out... it's amazing what reading the instructions can do.

---

### Post by jexdawg13 on 2007-02-10
When I said I figured it out, I was lying.

I open up terminal, enter Envy, and a screen with 6 options comes up.

    Envy Menu ver.0.8.1                
       |                                       
       |    1 - Install the NVIDIA driver      
       |                                       
       |    2 - Uninstall the NVIDIA driver    
       |                                       
       |    3 - Install the ATI driver         
       |                                       
       |    4 - Uninstall the ATI driver       
       |                                       
       |    5 - Restart the Xserver            
       |                                       
       |    6 - Exit         

First, I chose 3 (since I have an ATI gfxc), and that killed everything and sent me to a magical land of mystery, where the screen was black and a white underscore ( _ ) encouraged me to type things in. No command I typed did.. well.. anything, so I just restarted the computer manually and tried envy again, this time going with option 5. It did the same thing. Does Ubuntu hate me?

---

### Post by Maestro23 on 2007-02-10
> **jexdawg13 said:**
> Alright, you guys are going to hate me for this, but I seriously am noobtastic.

I downloaded Envy and installed the package... now where is it? How do I run it? Did it already run? Sorry for rapid-fire posting.

EDIT: NVM figured it out... it's amazing what reading the instructions can do.

LOL.. I was getting ready to ask "Did you read the instructions?"

---

### Post by shane634 on 2007-02-10
Ubuntu doesn't hate you lol. Give this a shot:

```
sudo /etc/init.d/gdm stop
```

  This will log you out of the Xserver. When you get to a command prompt ( you will need to login and password ) then type envy and choose the ati option.  Now we need to get back to X so:

```
sudo /etc/init.d/gdm start
```

  This will restart the Xserver. Or you can simply reboot the computer. Good luck.

---

### Post by jexdawg13 on 2007-02-10
I figured out what I was doing wrong and managed to get the ball rolling. Now that I've managed that, I'm really screwed.

The whole ati installation process started and by the end it asked if I'd like to rewrite xorg.conf, I said yes. Then, Restart now? Again, yes.

Then it restarted and got to the black screen with the big Ubuntu Logo and the orange status-loading bar.. the screen that shows up just before you login. 

After that, my monitor refused to show anything.. and I don't mean it's the monitor's fault - it's something wrong with whatever I just did. Like, I could turn the monitor off and back on and it would instantly show "Power Saving Mode" and then turn off, with the "standby" light still on. I'm pretty sure Ubuntu was still running because after my screen went blank it made the startup-noise (which, btw, is beautiful). So I manually restarted three times and got the same problem three times.

My BIOS is still set from when I started installing Ubuntu, so it's at Boot from CD. So I put in my Ubuntu CD and started in safe graphics mode, and thats where I am now.

Haha. Any ideas? Remember, I can't *do* anything unless it is before Ubuntu starts (like BIOS stuff) or on this Live CD. Sheesh.

---

