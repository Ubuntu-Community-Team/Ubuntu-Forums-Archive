---
title: "iMac G3 SE 400MHZ"
date: 2006-07-20
forum: Apple PPC Users
---

### Post by notgotanubunclue on 2006-07-20
Is there a custom build ISO file for Ubuntu 6.06 for an iMac DV-SE G3 400 MHz 128MB with Mac OS 9.04/os x 10.2.8, video card ATI 128VR, 640MB ram, 12GB hard drive ?

It would make this whole custom process much easier for me as I have no linux experience beforehand and I have had no joy following instructions for creating an xorg.conf file. Do Live CD's exist with this file modified for my machine? or is it possible for some genius Ubuntu to make the required file or share an existing one which I could use to make my own custom CD by placing the required files in the correct directories on the CD (I might need some direction)

I’ve been searching the forums here for 2 days while trying different things, if someone could help me out that would make my week.

---

### Post by phibxr on 2006-07-20
Have you tried putting Vesa as your driver? You won't get any 3D-acceleration, but in the meantime, I think you could live with that until you find a way to get your ATI-drivers working, as it seems you have already installed Ubuntu if you have tried to edit your xorg.conf.

By the way, does the Live CD display correctly? If it does, at least you know that there is a way to get it working.

---

### Post by notgotanubunclue on 2006-07-20
I've not gotten further than putting in the Live cd and letting it load for a while then the screen goes blank and I hear the chime of a start up sound and then nothing but a BLACK screen. I've then tried pressing Ctrl Option F1 to give me the terminal and I tried to type in things which were posted here on the forum but I am unable to type or edit the xorg.conf file.. so really I've gotten nowhere with running the CD never mind an installation :(

---

### Post by linear on 2006-07-20
This is the usual drill for an iMac G3 (remember, commands are case-sensitive):

After booting is complete,
1. **ctrl-option-F1** (should give you a command prompt - may take a few tries)
2. type: **sudo nano /etc/X11/xorg.conf** (return)
3. make your edits (see below)
4. **ctrl-O** (return) to write edited file
5. **ctrl-X** to exit nano back to command line
6. type: **sudo /etc/init.d/gdm restart** (return) to restart Gnome (note: with the Dapper Live CD, use **sudo killall -HUP gdm** if Gnome won't restart.)

Modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

HOWEVER, I don't think you can run Gnome with 128MB of memory anyway. Xubuntu may be a better bet.

---

### Post by RHTopics on 2006-07-20
Here is a shorter method for fixing /etc/X11/xorg.conf which causes the blank screen problem for iMac G3s.

1. Wait until you hear no activity and the screen is blank.

2. Press the following keys all at the same time:
   ```
 "control", "alt", "F1"
```

   You are now in a console screen.

4. Enter the following two lines exactly as shown below:

```
    sudo sed -i s/28-51/60-60/ /etc/X11/xorg.conf
    sudo sed -i s/43-60/75-117/ /etc/X11/xorg.conf

```
5. **Optional** step to confirm the changes have been made. 
   Enter the following command exactly as shown below:

    ```
grep -A 1 HorizSync /etc/X11/xorg.conf

```
   You should see the following:

```

     HorizSync       60-60
     VertRefresh     75-117
```

6. Press the following keys all at the same time:
    ```
"control", "alt", "F7"
```

   You are now back to the blank X session screen

7. Press the following keys all at the same time:
    ```
"control", "alt", "Backspace"

```
   Use **"delete"** instead of **"Backspace"** if using
   original keyboard.

   The X session should be restarted with the Ubuntu
   login screen appearing.


The above works for a slot-loading iMac G3 350mhz

---

### Post by Skia_42 on 2006-07-20
You don't need custon build to install Ubuntu on a computer such as yours, my first install was on an iMac G3, all you need to do is tweek the Xorg.conf file like linear and RHtopics suggested.

---

### Post by notgotanubunclue on 2006-07-20
Thanks for all the help, I will try each of these methods tomorrow. I am also wondering can I edit this file on another computer and burn a new CD so then I will not need to type anything to get the CD to load up. Im not ready to install it onto the old Mac yet, so loading up from the CD a few times is mostly what I am after at the moment.

---

### Post by linear on 2006-07-20
Re-mastering an Ubuntu Live CD is non-trivial. Moreover, xorg.conf doesn't exist on the Live CD, it's created at boot time.

---

### Post by Skia_42 on 2006-07-21
> **linear said:**
> Re-mastering an Ubuntu Live CD is non-trivial. Moreover, xorg.conf doesn't exist on the Live CD, it's created at boot time.

Just wondering, how are the graphics configured when booting from a live disk?

---

### Post by linear on 2006-07-21
I'm guessing it's **dpkg-reconfigure -phigh xserver-xorg** (configures with few or no questions). You might find it in a script if you dig around.

---

### Post by Skia_42 on 2006-07-21
okay, so it is pretty much the same way it is done after you install ubuntu only it does it every time you load the live cd. (because it doesn't write the file xorg.conf. Thanks

---

### Post by ruthie on 2006-07-26
An Ubuntu newbie here.

Reading this thread has been an invaluable help - so thanks to everyone!

Using the 'alternative' iso image,I've managed to install ubuntu on an original (tray load) iMac, and get the gnome desktop working. 

Initially, I could only get the desktop in 512x384 - pretty useless! - but after adding another 128MB RAM, I'm in the slightly better position of having a 640x480 desktop, with a large border. The screen resolution control gui gives me no alternatives.

I've tried editing xorg.conf, as described earlier in this thread (Hsync to 60-60, Vrefresh to 43-117), but still can't get anything better than 640x480.

Is this the best I can expect or does anyone know of something else I can tweak?

---

### Post by 3rdalbum on 2006-07-26
In your xorg.conf file, do you have entries for higher resolutions? In Section "Screen", Subsections "Display", for each colour-depth it should list different resolutions. For instance, under 24-bit colour on my computer it says:

        SubSection "Display"
                Depth     24
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection

Then immediately under the Screen section, there should be an option for colour-depth. Set that to whatever colour depth your desired resolution is under.

Because I know first-hand 640x680 isn't the best resolution an iMac G3 can do!

---

### Post by ruthie on 2006-07-27
Thanks for that info.

Under all the 'depth' sections, there were only entries for "800x600" "640x480".

I've added a "1024x768" entry to each.

I've tried with the Default depth set to 24, but this results in me being given only 640x480. Setting the default depth to 16 at least gives me an option of 1024x768 or 640x480 (no 800x600, curiously!).

It's an improvement at least! :-)

btw I've also tried commenting-out "Load dri" (don't know what that is/does), and it seemed to make little difference.

ps after the log-in screen, it takes around 2 minutes for the desktop to appear. Is this normal?!

---

### Post by RHTopics on 2006-07-27
ruthie,

How much memory do you now have installed and what is the speed of your CPU in your iMac?

Less than 256MB of RAM and a CPU speed of less than 333mhz will give you the startup times you are experiencing when using Gnome.

If you are not certain. To determine what you have, do the following command from a Terminal window:

```
dmesg | less
```

On the screen you will see information about your CPU and amount of memory installed.  Press the 'q' key to exit the screen.

A possible solution to getting 800x600 resolution is to adjust the HorizSync in **/etc/X11/xorg.conf** from **60-60** to **58-62**.  This change allowed my iMac to get 800x600 resolution.

---

### Post by Gossie on 2006-08-03
> **RHTopics said:**
> Here is a shorter method for fixing /etc/X11/xorg.conf which causes the blank screen problem for iMac G3s.

1. Wait until you hear no activity and the screen is blank.

2. Press the following keys all at the same time:
   ```
 "control", "alt", "F1"
```

(...) 



Hello RHTopics,

Do you do this with the Dapper Drake live cd inside?

My OS 9 is not working anymore since the first time I put the live cd in it...

[http://www.ubuntuforums.org/showthread.php?t=223752&page=3](http://www.ubuntuforums.org/showthread.php?t=223752&page=3) is my post about this.

With or without a live cd (Dapper Drake, Breezy Badger or linux YellowDog 4.1), the ctrl-alt-F1 gives no result. Like Notgotanubunclue, who started this thread, there is only the blank screen.

I will try to put another cd-rom player in the G3.

Good night!
Gossie

---

### Post by RHTopics on 2006-08-04
Gossie,

Yes, the process I outlined for solving the blank screen problem for iMac G3s uses the Live CD version of Ubuntu 6.06.  It is also known as the Desktop installation version.

From the description of your problem, it appears you are not getting to the point in the boot process where you can switch screens by doing "control", "alt", "f1".

When I boot with the Live CD in the iMac, the following things happen;

> 1. The screen is gray for a short time

2. The screen is white for a short time

3. The boot screen is shown.  The screen has a black background with white text.

4. After about 10-15 seconds the boot process starts.

5. The graphical boot screen now appears with the Ubuntu logo and progress bar.  Text appears under the progress bar describing the boot process,  with text like "loading essential drivers" and "adding live cd user".

6. After a few minutes, the screen becomes blank.

7. After a little bit longer with the screen still blank, I hear the Ubuntu startup music.

8. I wait about 10 seconds longer just to make sure nothing more is happening.

9. Now I do the "control", "alt", "f1" to switch to a console screen and make the necessary changes to /etc/X11/xorg.conf.

You may be on the right track in replacing your CD drive.  You might also want to try the free ShipIt CD.

---

### Post by Gossie on 2006-08-04
Hi RHTopics!

Thanks for your patient description of what I will hopefully be wrestling  with and/or whistling about soon. 

In the thread [http://www.ubuntuforums.org/showthread.php?t=223752&page=4](http://www.ubuntuforums.org/showthread.php?t=223752&page=4), where I originally posted the description of my problem, I have understood in the meantime that it may have to do with the resolution. 

However I cannot change the resolution right now: I can boot from the OS 9 installation disc, but it doensn't recognise the harddrive. So I cannot install.

Also I cannot start up anymore from the OS 9.1 that is/was on the harddrive, it wants a disc.

Tommorrow I will go to a computer club with the machine. They have ship-it cd's there. So more news later. This Nerdic Walking is exciting!  Will it ever work?!!

See you later! 
Gossie

---

### Post by RHTopics on 2006-08-04
Gossie,

I hope the computer club will be able to help you get things sorted out and get your iMac to boot up with Ubuntu!

---

### Post by Gossie on 2006-08-06
Well, the people from the computer club were busy with something important, so I took the Mac back home by the bus. Then I opened it and pressed the harddrive wires and then the harddrive worked again,

So now I have OS 9.2.2 (wow!).

But the problem remains ([http://www.ubuntuforums.org/showpost.php?p=1345343&postcount=35]("http://www.ubuntuforums.org/showpost.php?p=1345343&postcount=35")) However I found something that IDE harddrive would word and SCSI not work (see the link I just gave)

Greetings!

---

### Post by aperkins on 2006-09-02
If this is similar to my iMac 400, there's an additional monitor plug hidden underneath one of the bottom panels of your iMac.  There are two panels: one you open via a coin to insert more RAM, the other panel, or grill, you can remove with a small screwdriver.  iMacs came with a replacement for these panels that were molded plastic so you could access the secondary display connection - most people said "what the hell is this?" and threw them away with the boxes.](*,) [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

  I had the same problem as you've been describing, and was able to see the screen on an external vga.  The same cannot be said for the "Snow" iMac I was trying to install on.  It appears that the video graphics card won't show 60Hz on the built in monitor.  Additionally, "Edubuntu" worked just fine on the internal and external monitors.  Could it be a driver issue?  If so, I'd love to know how to install the driver from Edubuntu onto the iMac once I've installed Ubuntu.

  Will post if I've had any luck with the "Snow iMac".

---

