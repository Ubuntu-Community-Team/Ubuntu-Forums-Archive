---
title: "Black laptop screen after boot"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2007-02-25
Hi!

I am trying to install Ubuntu 6.10 on a friends Acer laptop.  I have finally been able to get the installation done by using the Alternate CD.  But now when it boots, after the Ubuntu loading screen, the screen just goes black!  I have reconfigured xserver a few times and ensured the resolution is correct at 1280x800 but I still just get a black screen.  I tried typing in the username and password on the black screen, and I could see the hard drive was then working so I guess it was loading OK, just nothing to see.   Now I read elsewhere something about typing in a parameter:

**linux acpi=off noacpi**


So where would I type this in?

Is there any other solution to this?   I have been telling my friend how fantastic Ubuntu is, but this is not impressing him.  

Russty.

---

### Post by Russty of Oz on 2007-02-25
"bump"

---

### Post by fusiachi on 2007-02-25
**/boot/grub/menu.lst**

If you need more guidance, ask away.  It should be pretty straightforward, though.

---

### Post by Russty of Oz on 2007-02-25
How do I do that if I can't see anything on the screen?

---

### Post by fusiachi on 2007-02-25
CTRL+ALT+F1 should kick you to terminal, once you've loaded up.

---

### Post by ]Nbx*cmD[ on 2007-02-25
When you boot your machine you can see a message for about 3 seconds asking you to press ESC to enter GRUB MENU, press it.
Once you entered the menu, select the FIRST entry and press the key "e".
In the very first line of the new menu you got, press "e" again and add the next parameters at the end of the line: **noapic nolapic**
Press enter (if i remember well, otherwise you can check in the bottom info line) and then press "b" to boot.
Your system will now boot properly.

To avoid having to do this every time you boot, just edit /boot/grub/menu.lst with your favourite editor and with root permision (ex. sudo gedit /boot/grub/menu.lst) and look for the line "Ubuntu Linux.... something" and add the parameters noapic nolapic at the end of that line. Save and you got it!

---

### Post by Russty of Oz on 2007-02-25
Thanks guys, I will give it a go!  

I told my friend that it was so easy to install and use Ubuntu, so  at the moment I am not looking too good, but hopefully this will get my cred back!

Russty

---

### Post by fusiachi on 2007-02-25
If (s)he actually uses Ubuntu for awhile, have no fear.  Your "cred" is in safe hands.

---

### Post by Russty of Oz on 2007-02-25
I don't seem to be getting anywhere with this!

I tried the /boot/grub/menu.lst  but it said "Permission Denied"
So I tried sudo /boot/....... and it said "command not found"

SIGH! :( 

I also tried the other method, but no luck there either.   When I press e the first line is " root (hd0,3) and when I added  noapic nolapic to that and then pressed b it just booted as before and then a black screen.  ANOTHER SIGH :( 

I must be missing something here!

---

### Post by fusiachi on 2007-02-25
You'll need to use something like vim or nano to edit the text file from terminal.

```
sudo nano /boot/grub/menu.lst
```

or

```
sudo vim /boot/grub/menu.lst
```

---

### Post by Russty of Oz on 2007-02-25
right!  I have got into edit the menu list, but now I am confused a little,  what I read before said to put in "linux acpi=off noacpi"  but ]Nbx*cmD[ said to put  "noapic nolapic"  so which do I use?

---

### Post by fusiachi on 2007-02-25
Try the first.  If it doesn't work, comment it out or remove it.

And with that, I'm headed to bed.  Best of luck.  Hopefully someone more knowledgable will take over.  If not, I'll be around in the afternoon (US EST).

---

### Post by Russty of Oz on 2007-02-25
Thanks, pleasant dreams!:)

---

### Post by Russty of Oz on 2007-02-25
I am still getting nowhere with this thing, and now my friend says I should remove it.  I will give it one more try though.

This is what his /boot/grub/menu.lst looks like, what should it look like to make it work?

# menu.lst - See: grub(8), info grub, update-grub(8)
                                 gurb-install(8), gurb-floppy(8), 
                                 grub-md5-crypt, /usr/share/doc/gurb
                                 and /usr/share/doc/gurb-doc/.

---

### Post by fusiachi on 2007-02-25
That can't be the entire thing.

Are you certain?

---

### Post by Russty of Oz on 2007-02-25
Hi again  fusiachi,

after the menu.lst in my previous post, it then goes on with a lot of text such as:

## default num
# set the default entry to the entry number NUM.  Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.

and so it goes on.  Do you want me to do the rest of it?  I thought the menu.lst was just the first bit.

Russty.

---

### Post by Russty of Oz on 2007-02-25
I just checked it along side my desktop menu.lst and they are exactly the same.  So why does the laptop not work??   Have the manufacturer (or microsoft!) done something so that no other OS can be run??

---

### Post by ]Nbx*cmD[ on 2007-02-25
Look for this in the file:

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

And, in the line starting by "kernel" add the magic words (either **acpi=off noacpi** or **noapic nolapic**) at the end of that very line. In my case, that would result in:

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash _noapic nolapic_
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

About your question about why does it work in your desktop and not in your laptop... well I guess your desktop doesn't use any batteries, does it? ;) There's lots of issues with laptops, it's really difficult to find a laptop that works just out of the box, so be patient, it can take some time to get it configured correctly.

Good luck!

---

### Post by bmathis on 2007-02-25
Could it possible be a video card issue? Last time I install Ubuntu on a pc with an ATI card, it showed a blackscreen until I edited the xorg.conf file and then did a reconfigure.

just a thought

---

### Post by Russty of Oz on 2007-02-25
> **']Nbx*cmD[ said:**
> Look for this in the file:

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

And, in the line starting by "kernel" add the magic words (either **acpi=off noacpi** or **noapic nolapic**) at the end of that very line. In my case, that would result in:

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash _noapic nolapic_
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

About your question about why does it work in your desktop and not in your laptop... well I guess your desktop doesn't use any batteries, does it? ;) There's lots of issues with laptops, it's really difficult to find a laptop that works just out of the box, so be patient, it can take some time to get it configured correctly.

Good luck!

[B]
I must be looking in the wrong place, there is nothing like that on the screen  when I type in  "sudo nano /boot/grub/menu.lst"  just what  I have put in the previous posts.   [/B]

---

### Post by ]Nbx*cmD[ on 2007-02-25
did you try to scroll down? O_o'
Anyway, please attach your menu.lst file in a post and i'll do it for you.

---

### Post by Russty of Oz on 2007-02-25
Ok, I didn't realize there was any more there :oops: 

but I have put that in and it still doesn't work.   How do copy it to be able to post the output here?  can I copy it to a usb drive to bring it over to my computer?

---

### Post by fusiachi on 2007-02-26
Edit: Nevermind.

---

### Post by Russty of Oz on 2007-02-26
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash noapic nolapic
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot 

[B]Ok, I have now done the above but after the Ubuntu splash is finished loading the screen still turns off.  It would seem Ubuntu is just not going to work on this laptop.  Well, I think Ubuntu IS working, it is just that you can't use it because the screen wont work.  And I have reconfigured xserver several times with no effect. :cry: 

So if no one else has any ideas, how can I remove Ubuntu from the laptop?  The owner either wants it to work or wants it out.[/B]

Russty

---

### Post by GIFRATE on 2007-02-27
The problem is the refresh rate of the screen. I had this problem with my installation. At first I thought that it was because of the driver (my graphic card is Nvidia and the nv driver was installed by default) but I figured it out after I bought a new monitor.

You can fix this by changing the refresh rate in /etx/X11/xorg.conf or try installing the proprietary driver using the command line (ctrl+alt+f1) when you're at the blank screen. 

good luck

---

### Post by Russty of Oz on 2007-02-27
I checed /etc/X11/xorg.conf and the refresh rate seems to be OK at a max of 60Hz.   

When I pres Ctrl + Alt + F1 I get a multi-colored screen!!    I then tried Ctrl + Alt +F2 then Ctrl + Alt + F7 but ended back at the black screen :( 

Perhaps Ubuntu just wont work on this Acer laptop?

Russty

---

### Post by bmathis on 2007-02-28
I don't like quoting myself, but...

> **bmathis said:**
> Could it possible be a video card issue? Last time I installed Ubuntu on a pc with an ATI card, it showed a blackscreen until I edited the xorg.conf file and then did a reconfigure.

just a thought

Find out what type of video card the acer laptop uses and configure xorg.conf with the correct drivers and whatnot, then do a 

Here is a link for some ATI cards [http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ati+howto]("http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ati+howto").

---

### Post by Russty of Oz on 2007-03-01
> **bmathis said:**
> I don't like quoting myself, but...



Find out what type of video card the acer laptop uses and configure xorg.conf with the correct drivers and whatnot, then do a 

Here is a link for some ATI cards [http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ati+howto]("http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ati+howto").

It is an ATI X700 card, and it is mentioned in that link but using the method in the link it still wont work.  I will try again tomorrow in case I haven't done it properly.

Russty.

---

