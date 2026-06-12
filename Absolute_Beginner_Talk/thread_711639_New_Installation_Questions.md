---
title: "New Installation Questions"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by dlfuller on 2008-02-29
I assembled a computer specifically to try Mythbuntu.  ASUS P5K-VM motherboard, 2 MB RAM, Geforce 8500 video, 320 GB hard disk, etc.

A CRT TV is connected with S-Video and my plan was to try a standard default Mythbuntu installation to see how it works before adding a tuner, sound card, remote, and other components to round out a finished setup.  The only input I have now to experiment with is Firewire from a Verizon FiOS Motorola QIP 6416-2.

The installation routine sorta went along following the Installation Manual.  I choose the nVidia Proprietrary Driver (Geforce 5+), S-Video out, and NTSC-M.

The 640 x 480 TV screen displays the BIOS and startup windows reasonable well with little overscan.  But not so in Mythbuntu where windows are cut off due to increased overscan.

Any attempt to resize and reposition the TV windows has been a problem.  Any GUI width or height values other than 0 produce a smaller window of about 2/3 full-screen size when using Utilities/Setup > Setup > Appearance to attempt resizing and repositioning.  X and Y offset values do seem to work but the TV window remains either oversize or at the smaller 2/3 size.

Is this the right approach to resize the TV window?  What is the procedure to input new dimensions?  

Then there is selecting inputs.  I was trying to see what video was available from my Firewire input.  Firewire was added as an input device, but afterwards any attempt to view using the Watch TV button brings up a "MythTV already using all available inputs for the channel you selected" dialog.  I haven't done anything in the area of recording.  There were none scheduled or stored.

I used sudo plugreport to check Firewire and had a Node 0 and Node 1 listed.  Node 1 had data similar to what's shown in the MythTV Firewire Documentation.  That seemed encouraging.

I can play a DVD using MPlayer, etc., with a reasonable picture on the TV.  But nothing shows from any play attempts in Mythbuntu.  The screen returns right back to the menu after activating the Play button.

What is happening with these inputs?  Troubleshooting clues please.

During any shutdown a "LIBC not configured" message appears, but I had bypassed the setup of a remote in the Configure Remote Control window by not checking the box.

Is this LIBC message abnormal?

I'm getting very frustrated from these installation problems.  Any suggestions about what I should do next would sure be appreciated.  Or, should I just head back to my Mac?

Thanks for your comments.

---

### Post by dlfuller on 2008-02-29
My apologies.  This should have been posted in the Mythbuntu thread and not here.

---

