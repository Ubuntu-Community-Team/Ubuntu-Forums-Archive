---
title: "Creative Zen Vision M"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Ohs0Ahxi on 2007-08-08
I'm new to Linux and so far its just my mp3 player that inst working, Ive installed gnomad2 so i think it should be working. it seems to freeze whenever a PTP session is closed. 
these are the results of lsusb so its detecting the device
```
 $ lsusb

Bus 002 Device 002: ID 08ca:0010 Aiptek International, Inc. Tablet

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 026: ID 041e:4151 Creative Technology, Ltd 

Bus 001 Device 001: ID 0000:0000  

```

however when i run mtp-detect it ends in the following
```
PTP: Closing session

inep: usb_get_endpoint_status(): Connection timed out

outep: usb_get_endpoint_status(): Connection timed out

usb_clear_halt() on IN endpoint: Connection timed out

usb_clear_halt() on OUT endpoint: Connection timed out

usb_clear_halt() on INTERRUPT endpoint: Connection timed out

OK.

```

then i have to reset the player for it to function again. it does this every time. Does anyone have any ideas I've searched but couldn't find a similar problem.

---

### Post by Hospadar on 2007-08-08
Are you able to transfer music, but then when you close the program it crashes? or can you not transfer in the first place?

---

### Post by Ohs0Ahxi on 2007-08-08
I can transfer music to the player in gnomad2 and also in Amarok but when closing gnomad2 or trying to disconnect the player in amarok the player freezes on updating and the programs hang.
 If i disconnect the player and reset it the tracks are there and work fine so it seems to be a problem with it trying to close the connection (i think)

---

### Post by Ohs0Ahxi on 2007-08-08
UPDATE
If i unplug the device myself after I've transferred songs then it updates the track listing on the device without freezing. However it still freezes and crashes either gnomad2 if i quit with the device connected, or click disconnect in Amarok without unplugging it first. This doesn't seem right to me, any suggestions of what to try now?

---

### Post by TomG on 2007-08-11
Have exactly same problem :( Very annoying.
I need to reset the Creative Zen each time after stuff transfer...
Any clue ?

---

### Post by Ohs0Ahxi on 2007-08-12
so far the only solution is to unplug the player once the transfer is finished, but before you click disconnect if your using Amarok or close gnomad2. The player will then update its library without crashing. 

I think it has something to do with this 

```
inep: usb_get_endpoint_status(): Connection timed out 
outep: usb_get_endpoint_status(): Connection timed out 
usb_clear_halt() on IN endpoint: Connection timed out 
usb_clear_halt() on OUT endpoint: Connection timed out 
usb_clear_halt() on INTERRUPT endpoint: Connection timed out 
```

i get that from mtp-detect in the console, and also if i run Amarok from the console to see any output when i try and disconnect the player.

---

### Post by TomG on 2007-08-13
At least 2 discussions (yesterday and today) on close Zen Vision problem on :
    [http://sourceforge.net/mailarchive/forum.php?forum_name=libmtp-discuss](http://sourceforge.net/mailarchive/forum.php?forum_name=libmtp-discuss)
A fix seems even available. Will check...

---

### Post by TomG on 2007-08-13
It works ! As per patch explanation it seems the new close_usb procedure (in the libusb-glue.c) is now :
static void close_usb(PTP_USB* ptp_usb, uint8_t interfaceNumber)
{
usb_reset(ptp_usb->handle);
}

Then recompile. 
I tested with Gnomad2 and it no longer hangs ! :)

---

### Post by Ohs0Ahxi on 2007-08-13
Site seems to be down for me, but I'll give it a go when i can. Thanks for posting this

---

### Post by Ohs0Ahxi on 2007-08-13
I changed the close procedure and if i run mtp-detect its now working as it should, it closes the session without freezing. 

However i still have the problem in amarok and gnomad, they seem to always install libmtp5 so i assume they use this rather than the one i installed. Any suggestions?

---

### Post by TomG on 2007-08-14
Strange. I had Gnomad installed yet and I simply recompiled libmtp with modification. Then it works without more action.

---

### Post by Ohs0Ahxi on 2007-08-14
i downloaded the libmtp-0.2.1.tar.gz from sourceforge, made the changes then compiled. 
Is that what you did or am i missing something obvious here?

---

### Post by TomG on 2007-08-14
Yes that sounds to be what I did.
Once done any unplug after transfer worked fine.

---

### Post by Ohs0Ahxi on 2007-08-14
Your using gnomad2? that works for me if i unplug the player after a transfer and leave the program running but if i close the program with the player connected the player will freeze? 
Was this the problem you were having and the recompile solved it?

---

### Post by wantime on 2007-08-15
I'm also having problems with Creative VisionM.  It crashes every time I connect it.  If I have it set to be removable data disk it is fine but both Amarok and Gnomad2 cannot pick it up.  It seems to crash on connection?? Any ideas?

$ lsusb
Bus 004 Device 011: ID 041e:4151 Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 413c:8000 Dell Computer Corp.
Bus 001 Device 004: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

$ mtp-detect
Found non-autodetected device "Creative Zen Vision:M (DVP-HD0004)" on USB bus...
usb_claim_interface(): No such file or directory
Connection error.
No devices.

---

### Post by Ohs0Ahxi on 2007-08-15
i remember reading in another thread that you have to turn off the Removable Disk feature for it to work as an MTP device.  
On the player; Menu > Extras > Removable Disk > Disable

---

### Post by wantime on 2007-08-15
I have disabled the removable disk option.  That's when it crashes the device.  The only time that the device is recognised is in the case that the removable disk option is enabled.and then only as a usb storage device.

---

### Post by TomG on 2007-08-15
> **Jenko22 said:**
> Your using gnomad2? that works for me if i unplug the player after a transfer and leave the program running but if i close the program with the player connected the player will freeze? 
Was this the problem you were having and the recompile solved it?

Yes it is. It also fixed the command line similar problem.

---

### Post by Ohs0Ahxi on 2007-08-16
Just tried again, and it seems to have worked as far as I'm aware i did nothing differently this time but as long as it works I'm happy.

Thanks for tracking down that fix

---

### Post by TomG on 2007-08-16
Enjoy :cool:

---

### Post by wantime on 2007-08-17
So after using a windows box to upgrade the firmware on the VisionM device, it is recognised by Ubuntu.  That was an XP upgrade for the device.  The firmware upgrade was in June this year I think.

---

### Post by Ohs0Ahxi on 2007-08-17
Spoke to soon, its back to normal again. 

I think i'll leave it alone, its not too much hassle to just unplug it and i have no idea how its reverting back to not working.

---

### Post by _marco_ on 2007-08-27
Sorry, i didn't understand were i have to change my file... here is the section of libusb_glue.c

[I]static void close_usb(PTP_USB* ptp_usb, uint8_t interfaceNumber)
{
  clear_stall(ptp_usb);
  // Added to clear some stuff on the OUT endpoint
  // TODO: is this good on the Mac too?
  usb_resetep(ptp_usb->handle, ptp_usb->outep);
  usb_release_interface(ptp_usb->handle, interfaceNumber);
  // Brutally reset device
  // TODO: is this good on the Mac too?
  usb_reset(ptp_usb->handle);
  usb_close(ptp_usb->handle);
}[/I]

is this correct? where do i apply the modify? :lolflag:

tnx a lot

---

### Post by Desiree on 2007-09-15
> **wantime said:**
> I'm also having problems with Creative VisionM.  It crashes every time I connect it.  [....] both Amarok and Gnomad2 cannot pick it up.  It seems to crash on connection?? Any ideas?

I'm having the same problem.  Help! 
I'm very new to Linux... 

:confused:

---

### Post by FreeSoul on 2007-09-16
> **TomG said:**
> It works ! As per patch explanation it seems the new close_usb procedure (in the libusb-glue.c) is now : 
static void close_usb(PTP_USB* ptp_usb, uint8_t interfaceNumber)
{
usb_reset(ptp_usb->handle);
}

Then recompile. 
I tested with Gnomad2 and it no longer hangs ! :)

I sent you a private email, since this thread is old, but can you tell me where the file
libusb-glue.c should be? My gnomad2 works fine but I have the disconnect problems with it
(and with Amarok) also. I installed gnomad2 with add/remove gui. mtp-detect also times out during the last phase.

For some reason libusb-glue.c does not exist on my file system.

edit - I have libmtp5 installed through add/remove. How can, or can, I edit that as you edited the 2.1 verson from soundforge?

Thanks,
FreeSoul

---

### Post by wantime on 2007-09-17
Desiree

I got it working but not perfectly ... I still have to do the patch process that is talked about in this thread.  I can though add MP3 format audio files using Gnomad2 (and I think video using the data tab in Gnomad2).

I'm pretty sure that the first step would be to somehow get the updated windows XP firmware onto the VisionM using a windows box in an internet cafe or something (I'm not sure if this is necessary but with this update the device no longer just crashed every time I plugged it in - it felt like the firmware update did something good).  The next part is to then use it in Gnomad2 - it should be recognised at this stage.  Whenever you dock the device to your computer you can add or remove songs in Gnomad2 if they are MP3's (I'm not sure about WMA's?) - I just know that M4A and MP4 don't seem to be recognised properly.  After adding/removing you have to detach the device physically first for it not to crash as there is something wrong in the disconnect functions in the MTP library - I think!  Then you close Gnomad2 (or Amarok - works in both).

I hope this helps.

---

### Post by wantime on 2007-09-17
FreeSoul

I'm pretty sure you have to remove the libmtp5 and reinstall it manually by downloading the .tar file.  Once you open the archive file, one of the subfolders is called src and the libusb-glue.c is in this folder.

---

### Post by Desiree on 2007-10-01
Thanks for your help Wantime!

I successfully installed the firmware upgrade (1.21.02) from the Creative Support/download page using their auto-upgrade detector service.  It installed the firmware on my unit rather effortlessly, with the exception of having to start the process after it cancelled for some unknown reason on the first try.  It wasn't the quickest process, but it got the job done.  This was installed using a Windows XP computer with no other Creative software installed.

After the firmware upgrade, I was able to connect to my Ubuntu machine via USB without the player crashing.  Better yet, it immediately started charging.  The device was automatically detected using Gnomad2 (2.8.11), and I was able to transfer a video using the data transfer tab, and mp3s using the music transfer tab.

:guitar:

Alas, after transferring the first album, gnomad2 froze on a "Getting track Metadata" window.  But the device didn't crash. =)  So not yet flawless, but I'm not sure that I'm getting the exact same error as discussed since it's not related to disconnecting.  As long as the occasional transfer works, I'm ok.  More to poke around yet though.

I was unable to set up Amarok, probably because I don't know how to configure the device.  As it currently is set up, it wouldn't detect my device by default nor by me manually adding it, but again, I'm not yet familiar with how some of the configuration should be set.  Any advice? 

:confused:

---

### Post by jeremija on 2007-11-17
i have a question.
i can connect to my zen vision m either via Amarok app (by adding a mtp media device) or Gnomad2 and everything works perfectly, but everytime i click the disconnect button or close the program my zen hangs, on screen it says "Updating..." or there is a connected sign (it depends on whether i have transferred any new files to it) and i need to use the reset button.
And if I physically disconnect the Zen before exiting the app or clicking disconnect button, everything works fine.
Does anybody know what is this about?
In WindowsXP everything works ok...

edit: i take this back - after updating to gutsy (which automatically updated from libmtp5 to libmtp6) everything is fine...

---

