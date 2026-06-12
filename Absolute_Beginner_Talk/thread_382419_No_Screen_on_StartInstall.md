---
title: "No Screen on Start/Install"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by mindion on 2007-03-12
I'm currently using WinXP, and am interested in trying out Linux, so I thought I might try out Dual OS. I am extremely uninformed on Linux, operating systems and the like so please forgive my ignorance. That said, I am proficient in most other computer matters.

I've spent the day downloading ubuntu and backing up my important files in case of problems, and because i've spent so long doing that I am frustrated by the following problem.

I wrote the image to CD-R, and when it boots up, and I select Start/Install I run into problems.

I removed the splash screen and 'quiet'. I caught one error message that said:
"IDE: failed opcode was unknown" (no idea if relevant)

Then a text based error box pops up:

"Failed to start the X Server (your graphical interface). It is likely that it's not set up correctly. Would you like to view the X Server output to diagnose the problem?"

I select yes, and read this:

"(WW) I810 No matching device section for instance (BusID PCI:0:2:0) found
 (EE) No devices detected

 Fatal server error
  No screens found"

and then it takes me to another log I don't bother reading due to the fact I've discovered the problem already, and its sheer volume. After that it presents me with a command-line interface with the prefix being:

"ubuntu@ubuntu:~$"


So obviously I figure there's a problem with my video driver, but I don't know what this means or where to start. Or it could be something totally simple that will embarass me. But if anyone could help me I would be extremely grateful.

PS, in case this helps, my video card is as follows:
NVIDIA GeForce4 MX 4000

---

### Post by K.Mandla on 2007-03-12
It looks like, for some reason, your video card was set to an I810 (an old Intel onboard system) and it hasn't found your Nvidia card.

Check and make sure your xorg.conf file is pointed at the Nvidia card. You'll need the BusID for the card, which usually shows up like "01:00.0 VGA compatible controller ... " when you give the *lspci* command in the terminal. Then make sure the Driver is set to "nv".

From there you should get some sort of video from the card. Remember that there's also the possibility that your BIOS might need to be set to turn off the onboard I810 stuff. I had an old HP machine that Ubuntu kept trying to route the video to the onboard chip, and it was a bit frustrating to keep reminding it.

Was that helpful at all? :???:

---

### Post by mikeprice on 2007-03-14
It was certainly very helpful to me. I had a similar problem with a 4 year old, very basic spec Dell machine to which I'd added a PCI graphics card. (No AGP slot).

Unfortunatly the Dell BIOS does not allow the i810 graphics circuit to be disabled, only whether or not it should take priority over a video expansion card. (this is a pain, because not being able to disable the Intel graphics also breaks the latest nVidia drivers for Windows too, but that's another story)

Complete solution is something like this:

Do a normal boot from the LiveCD, and wait until you get the message about X not starting. Dismiss it with the no button. (For some reason, I didn't get a prompt here, so I used Ctrl-Alt-F2 to open a new VC)

Run *lspci* and find the video board in the list. In this case it was "01:04.0 VGA Compatible controller: nVidia Corporation GeForce 6200 (rev a1)" Note down the number at the start.

Run *sudo nano /etc/X11/xorg.conf*

Scroll to about 2/3rds down to find the Device section about the video controller. This is where it got weird for me. Somehow it had detected the 6200, but had attempted to configure it with the Intel driver:

```
Section "Device"
Identifier "Intel Corp...."
Driver "i810"
BusID "PCI:1:4:0"
Endsection
```

So yeah, that's the BusID for the 6200, but not the driver nor description. In any case, replace the BusID with the number reported by lspci, the identifier with the name of the card, and the driver with 'nv', failing that, use 'vesa'. I seemed to notice with the BusID, that lspci reported it with as 1:4.0, but xorg would only look at it with a colon instead of the dot between the 4 and the 0. This is probably obvious to most people, or it's me being stupid. I don't really care, it worked.

Now that's done, move to the next-but-one section, which should be called Screen, and change the Device tag to the name you entered for the video card. PAY PARTICULAR ATTENTION TO THE DISPLAY MODES IN THIS SECTION. I didn't, and was very annoyed when after 10 minutes of playing with the config, had to reboot because the display mode was out of my monitor's range.

Once it's all set, tap Ctrl-O, then enter, to 'save' the file (of course you actually don't, it's a live cd), and then Ctrl-X to quit, then type *startx*, and pray.

Cheers
Mike

Edit: Despite what I said at the top, this can of course be done after installation to the HDD, and you may in fact need to do it after installing if you have this problem.

---

### Post by xenocideJane on 2007-09-17
Right! I have the same issue, although I caused it (ancient vaio refused to boot from CD, removed & upgraded HD, installed on tower w/monitor, reinstalled into vaio, now unattached to monitor).

I've followed your suggestions, MikePrice, but am now coming up with an odd error:
"(WW) VESA: No matching Device section for instance (BusID PCI:0:10:0) found"

I find this odd, since the BusID PCI should be "00:0a.0"

It sounds as though "vesa" drivers are inadequate or don't include my screen (Neomagic Corporation NM2200 [MagicGraph 256AV]).

Any help/thoughts?

---

