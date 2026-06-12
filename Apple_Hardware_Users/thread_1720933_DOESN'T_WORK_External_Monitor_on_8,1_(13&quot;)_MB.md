---
title: "DOESN'T WORK: External Monitor on 8,1 (13&quot;) MBP w/ Ubuntu Natty B1"
date: 2011-04-03
forum: Apple Hardware Users
---

### Post by patientfox on 2011-04-03
Just did a fresh install of Natty B1 (previously had alpha 2).. I noticed this issue w/ A2, as well.. plugging in the exterminal monitor (via mini-displayport-to-vga connector) will do the following:

1) turn the screen on the laptop's display entirely black (but not turn it off).. i can move and see the mouse cursor.. but everything on the window appears to not rending or "painted" black..
2) external monitor never becomes active..

the only way to recover is to kill/restart X or reboot after disconnecting the extmon.. having extmon plugged in from boot produces the same results (and it doesn't seem to ever become active during boot up).

sometimes this won't happen right away if i plug in the external monitor.. but opening the Monitors system prefs dialog will definitely cause (or detect displays) ,etc

I waited to see if the issue would fix itself w/ the beta update, but it hasn't.. Any other 8,1 owners out there that can verify this issue? My (totally uninformed) guess is that it's due to differences in the display/gfx hardware and thunderbolt integration(?) (I've seen a verification verifications of working-out-of-the-box.. but they were from 8,2 and 8,3 owners (which have discrete graphics cards))... If anyone's gotten this to work with some config stuff, I'd love to see that as well (since the wiki page for 8,1 says it works ootb).

If someone could let me know where I should look to capture error output when the above issue occurs, that would be awesome.

Thanks

---

### Post by patientfox on 2011-04-03
> **patientfox said:**
> have any other 8,1 owners had any luck with the external monitor?

I've tried a mini-display to vga connector on both unity and classic gnome and haven't had any luck.

When I plug the connector into my monitor, the screen on the laptop goes  black (but I can see the mouse cursor/move it and see the cursor change  when it hovers over inputs.. so its like all of the windows render  black..?)

I then have to d/c the monitor, switch to a console session and kill  gnome-session .. (which causes x/gdm to restart and then things work  again)

all the stuff in the forums/wiki with people saying it worked out of the  box have been with 8,2 or 8,3 owners, so I'm thinking that this is  possibly graphics related?

I'm not on my ubuntu install atm, but I recall there being some output  in dmesg, I can come back and paste that when I get a chance if it would  help.

thanks


I posted this previous in the 2011 macbook thread for maverick.. so just wanted to ref it..

---

### Post by patientfox on 2011-04-04
This is the output in dmesg that occurs when I plug in the mini-displayport-to-vga connector.. after this my display is messed up pretty much until reboot.

I can disconnect the dongle and kill gnome-session to trigger an x restart, but then the resolution on the screen is messed up (it looks like its been changed to a 4:3 resolution, like when you connect to a projector and it is going to mirror the display.. there's black bars on either side of the screen).. and after logging in, it looks like the system hangs.

anyways, here's the dmesg output. I'd really appreciate any insight from other users, or just a confirmation that this is happening to other 8,1 owners and not me (I've gotten this exact behavior across multiple ubuntu installs, so I don't think its just a quirk of my install.. just want to know if its the 8,1 hardware or *my* 8,1 hardware that is messed up, here)

[  277.783448] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[  284.540195] [drm:intel_dp_aux_ch] *ERROR* dp_aux_ch not started status 0x8023003e
[  284.540214] [drm:intel_dp_aux_ch] *ERROR* dp_aux_ch not started status 0x8023003e
[  286.816910] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 251
[  286.816922] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  286.816932] <3>00 ff ff ff ff ff ff 00 72 a1 ad 36 e6 10 81 0b  ........r..6....
[  286.816940] <3>12 01 03 08 2f 1e 78 ea de 95 a3 54 4c 99 26 0f  ..../.x....TL.&.
[  286.816948] <3>50 54 bf ef 90 a9 40 71 4f 81 40 8b c0 95 00 95  PT....@qO.@.....
[  286.816956] <3>0f 90 40 01 01 21 39 90 30 62 1a 27 40 68 b0 36  ..@..!9.0b.'@h.6
[  286.816964] <3>00 da 28 11 00 00 19 00 00 00 fd 00 38 4d 1f 54  ..(.........8M.T
[  286.816972] <3>11 00 0a 20 20 20 20 20 20 00 00 00 ff 00 4c 41  ...      .....LA
[  286.816980] <3>31 30 43 30 34 31 34 30 33 30 0a 00 00 00 fc 00  10C0414030......
[  286.816988] <3>41 4c 32 32 31 36 57 0a 20 20 20 20 20 00 65 ff  AL2216W.     .e.
[  286.816994]
[  287.951170] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting
[  330.047224] [drm:ironlake_crtc_disable] *ERROR* failed to disable transcoder
[  330.709291] [drm:intel_dp_complete_link_train] *ERROR* failed to train DP, aborting

---

### Post by mojavelinux on 2011-04-16
I get the same problem running Ubuntu Natty Beta2 on the latest (April) MacBook Pro 13" (8,1). I'm using the Apple VGA adapter to attach a LCD monitor (which works with other Ubuntu laptops and the stock OSX installation.

I'm posting to document that this is still an issue in Beta2 and to link in another detailed post from the xorg.drivers list:

[http://permalink.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/3513](http://permalink.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/3513)

I also tried using Linux Mint 10. There I got a slightly different result. The primary LCD never blanked out and it correctly identified the model, resolution and refresh rate of the external monitor. However, the external monitor display remained black and claimed there was no input source.

Unfortunately, without the external display, I can't give presentations with this laptop under Linux, which is the main reason I got the laptop. Here's hoping this is resolved soon.

---

### Post by mojavelinux on 2011-04-16
I've reported a bug for this problem.

[Bug #762855: Display on external monitor (vga) is black on 13" MacBook Pro 8,1]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/762855")

If you have having a similar problem and make progress, please share that information in the issue report.

---

