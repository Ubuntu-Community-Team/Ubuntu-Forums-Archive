---
title: "newbie problems"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by rbrambila on 2006-03-05
hey everyone. i just installed ubuntu yesterday and today i spent most of the day tweaking away. this is the first time i ever mess with linux and its been better than i expected, albeit a little bit of a battle. i was mostly surprised that i was automatically connected to the internet as soon as I installed (since im on a wireless network, i was expecting more of a problem).

i have some minor problems/questions than some of you may be able to solve.

1. i have 'Debian Menu' installed (via automatix script) under my applications, and i want to remove it. I don't know how. I tried using the menu editor (under applications > system) but that begins to load and then it disappears. this might not even be the right program to run, i have no idea -- im just guessing by the name of it.

2. sometimes things, such as firefox windows or application windows, just disappear. its weird because sometimes i browse the web for an hour or more without it ever happening -- and other times it keeps disappearing within a minute or so of being online. sometimes i get error messages of programs that ended unexpectedly other time theres nothing, all the windows just disappear. its a little annoying but not a huge problem where it interrupts me enough to want to realocate that partition space back to my xp drive :)

3. i've had the problem where seemingly out of nowhere the GUI disappears and im confronted with a black terminal asking me to login. i do and apparently i have commands (i know because of 'help' command) i can execute -- my question is, how can i get back into the GUI. i'm guessing this is the equivalent of microsoft's dos (at least pre-XP)? ubuntu without the nice graphical user interface.

4. my screen has frozen 3 times and i can't do anything. i've had to unplug my pc basically. is there something i can/should do instead? like an equivalent to CTRL-ALT-DEL?


I'm satisfied with Ubuntu, but i find that in the back of my mind i'm always a little scared (and annoyed at the fact) that something's going to go wrong and i'm going to have to restart. i don't know how to describe it, but i *feel* like its not as stable/powerful as i would like it to be. but, like i said, this is my first encounter with the OS and i'm pretty open minded about it.

---

### Post by rbrambila on 2006-03-05
two more questions --

i can see my xp drive on my desktop (as hda1) and i can see all of the files there (i guess because it isnt NTFS formatted). but, how much interaction will ubuntu actually allow me to have with these files? do i have read/write access to the drive? (like, can i vew txt documents, images, play or use mp3s from there)

secondly, i've apparently installed wine and just now learned what exactly it is -- but how do i access it? i'm a design student and it'd be great if i could run photoshop/illustrator without leaving ubuntu. can wine run all windows applications? are there certain limitations (are files slower, buggy, etc when using wine)..

thanks!

---

### Post by Estariel on 2006-03-05
Hello, and welcome to linux :)

Firstly, let me assure you that these instability issues you have had are really not typical and should not happen. I've never had windows disapear on me, so I don't know how much help I can be.

1): The menu editor is the right tool to use. It should _not_ disappear like that.

3): This is indeed the command line interface of linux. It should not however appear out of nowhere. You can switch between several command line terminals (ctrl+alt+F1-6) and the graphical interface (ctrl+alt+F7) when the graphical system ("x-server") is already running. If you somehow managed to kill it (or it killed itself, which again is not normal at all, since it usually is rock solid) you can restart it from the command line using the command
```
startx
```

4): You can try switching to a command line terminal as described above and issue the command
```
reboot
```
BUT: The x-server is not at all supposed to freeze.


Given that you experience very unusual stability issues, i have a few questions: Are you running "Breezy" (ubuntu 5.10) or did you by any chance install the _unstable_ "Dapper" (ubuntu 6.4, will be officially released in april)?
Dapper indeed sometimes has the issues you descibed.

If you are running Breezy: Did you try to install any fancy eye candy? Did you try to enable the composite extension? (if you have never heard the word composite, you haven't tried.)

If non of the above fits: Please give us some information on your graphics hardware, and whether you installed any additional drivers (like the official nvidia or ati driver).

Thanks,
Estariel

---

### Post by Estariel on 2006-03-05
[QUOTE=rbrambila]two more questions --

i can see my xp drive on my desktop (as hda1) and i can see all of the files there (i guess because it isnt NTFS formatted). but, how much interaction will ubuntu actually allow me to have with these files? do i have read/write access to the drive? (like, can i vew txt documents, images, play or use mp3s from there)

secondly, i've apparently installed wine and just now learned what exactly it is -- but how do i access it? i'm a design student and it'd be great if i could run photoshop/illustrator without leaving ubuntu. can wine run all windows applications? are there certain limitations (are files slower, buggy, etc when using wine)..

thanks![/QUOTE]

1) You can read, but you cannot write, since write support is still considered unstable and could mess up your partition. This, ubuntu ships without ntfs write support.

2) Wine will let you run photoshop and illustrator ok-ish. It is slower than with Microsofts implementation.
If you are serious about this, there is a version of wine, that gets specifically developed to work with a select few applications (among them photoshop) and it works really well (much better speed, etc.)
It costs a little though (not much)
You can get it here: [http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by Qrk on 2006-03-05
it needs to be 

```
sudo reboot
```

but I believe for some reason its better to use

```
shutdown -r
```

---

### Post by rbrambila on 2006-03-05
im running the breezy version. and, *most* of my trouble started occurring when i ran the automatix script now that I think about it. it halted half way and gave me an error. then i got a bunch of error messages and had to restart. i did, and ran automatix again and this time it went through well. and, although im not positive, i think that when automatix script froze was when it was installing the nvidia drivers (via the option in automatix) -- though, the second time (the one that actually went through completely) i opted to leave out the drivers.

i've got 200gb of storage, 60gb partition that ubuntu is on with 1.5gb swap partition (i've no idea what the point of this is though). 2gb of ram on a 3ghz athlon chip. and i'm running a 256mb nvidia geforce 5700le card. my video looks great (even before i tried to install the drivers via automatix).

also -- about the menu editor disappearing, i'm positive that it didn't before i installed automatix. i think its one of the things i opened while messing around with the OS.

---

### Post by Qrk on 2006-03-05
You can remove the nvidia drivers by:

```
sudo apt-get remove nvidia-glx
```

But a better solution would be to try this first:

```
sudo dpkg-reconfigure xserver-xorg
``` 

On the second screen see what driver is used. If it is "nv", try changing it to "nvidia" if it is nvidia try changing it to "nv"

---

### Post by Estariel on 2006-03-05
ok, let's first make sure that the nvidia driver is not messed up.
Open a terminal and do the following:

```
sudo apt-get install nvidia-glx
```

this will install the driver, unless you already have it.

Then we need to tell the graphical system that we want to use the new installed driver.
We must edit it's configuration file for this:

```
sudo gedit /etc/X11/xorg.conf
```

find a section that reads something like this (the following is MY setup, don't copy it!) 
```

Section "Device"
        Identifier      "NVIDIA Corporation NV40M? [GeForce Go 6200]"
       ** Driver          "nvidia"**
        BusID           "PCI:1:0:0"
        Option "RenderAccel" "true"
        Option "AllowGLXWithComposite" "true"
EndSection

```

Check that the bold line above reads the same in your file. If it does not, replace whatever driver is listed with "nvidia".

Save the file and reboot.

You should be greeted by an nvidia splash screen once the graphical system starts. Then check whether you still have those stability issues.

---

### Post by rbrambila on 2006-03-05
problem man --

now i can't boot into ubuntu. everything seems to boot, then right before it should let me see the login screen, the screen goes black and stays that way. i've tried it a couple of times (even with recovery mode) and nothing :(

i downloaded/installed the drivers -- went to the section and instead of "nvidia" it said "nv" so i replaced it. then i saved the file and rebooted.

what can i do now?? :(

---

### Post by Estariel on 2006-03-05
that's really strange.
we will have to undo this change then:

when you are faced with the black screen, hit ctrl+alt+F1.
You will then be presented with a text log in.
Log in.

now do the following:

```

sudo nano /etc/X11/xorg.conf

```

this starts a console based text editor.
again find the section mentioned above and revert it to say "nv" again.

hit ctrl+o to save, then ctrl+x to exit.
then type
```

sudo reboot

```

I will try to think of why this doesn't work.

btw: the nv driver is the open source driver for nvidia cards.

edit: added a "sudo" which i forgot

---

### Post by rbrambila on 2006-03-05
hey.. CTRL+ALT+F1 did nothing so i rebooted and got the terminal by choosing recovery mode. i made the change and it worked, im back in ubuntu.

my Applications Menu Editor still disappears though -- any idea on that? (or at least -- how about another way to remove Debian Menu, maybe through the terminal or ?)

thanks

---

