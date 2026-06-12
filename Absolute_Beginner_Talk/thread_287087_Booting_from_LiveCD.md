---
title: "Booting from LiveCD"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by DanSchnell on 2006-10-28
Ok, well I've been wanting Linux since I was like 12 (I'm 17 now) and I can finally do it since I have my own computer.  So I booted from the CD and got to the Ubuntu menu with the 5-6 options.  So I selected "Start or Install Ubuntu".  It proceeds to go to the Ubuntu loading screen and then after it is finished loading this happens:

1st time I tried: My screen was filled with gray/green pinstripes. I got a little scared and rebooted to Windows and then went to ubuntu IRC for help.

2nd time: I did the exact same things except this time after the loading screen My screen turned all purple (Kinda wavy looking) I didn't freak out so I just waited, and thought it would fix itself.  I then heard the Ubuntu sound, then my screen went black.  I shook the mouse, the screen was purple but I could definitely tell where the taskbar was supposed to be on top (The purple was faded.)  

Does anyone have any Idea what my problem is?

(Running on custom computer:  AMD Athlon 64, Asus a8n-sli prem motherboard.  ask if you need more information..)

---

### Post by meng on 2006-10-28
Ubuntu version? Architecture - i386 or amd64? Shipit CD or burn your own?
Video card?

If you are trying to boot amd64 version, try the 32-bit (i386) version instead.

---

### Post by Tomosaur on 2006-10-28
Strange problem. Did you try running the 'check this cd for defects' option? There are problems which can occur depending on how you burnt the CD (unless you got it via ShipIt). Anyway, try that first and see if anything jumps out.

---

### Post by PriceChild on 2006-10-28
Yeah, i strongly reccomend you isntall the 32bit version despite your 64bit arch.

This is because many items such as w32codes for playing certain media files won't work as easily under 64bit... and i'm sure you'll want them!

You shouldn't notice too much of a performance hit.

---

### Post by DanSchnell on 2006-10-28
I'm trying to install 6.10

And I didn't originally use the 64bit.  I dled the 32bit (Only actually)  Do you think that could be the problem?

---

### Post by meng on 2006-10-28
Nope, 32 bit should work fine on a 64-bit system. I recommend you re-burn the ISO, at a lower speed.

---

### Post by DanSchnell on 2006-10-28
I didn' have any disk errors...

What speed should I write it at?

---

### Post by Tomosaur on 2006-10-28
The safest would be the lowest speed possible.

---

### Post by DanSchnell on 2006-10-28
Meng:

2 nVidia GeForce 6800GS running in SLI

---

### Post by DaveBorealis on 2006-10-28
> **DanSchnell said:**
> 
1st time I tried: My screen was filled with gray/green pinstripes.
[SNIP]
2nd time: I did the exact same things except this time after the loading screen My screen turned all purple (Kinda wavy looking)
Hello Dan,

Sounds like your problem could simply be a misconfigured/mismatched monitor setting.  Besides going with the 32bit install, maybe try Dapper 6.06 on the chance that you might be hitting one of the 6.10 rough spots.  And if you try it, don't do the actual install...just burn the 6.06 32-bit live CD and see if that boots with full monitor use.

Dave

---

### Post by DanSchnell on 2006-10-28
Does ubuntu 6.10 support 1280x1024?

DaveBorealis: Thanks, I'll try that...

---

### Post by Luddy on 2006-10-28
I am having the same problem

ATI Radeon x850 xt

View Sonic VP930b 1280x1024 native

---

### Post by DanSchnell on 2006-10-28
Nothing yet...

---

### Post by DaveBorealis on 2006-10-28
> **Luddy said:**
> I am having the same problem

ATI Radeon x850 xt

View Sonic VP930b 1280x1024 native

Are you also using 6.10 Edgy?  From reading other threads, I think there might be some Edgy issues with specific hardware.

Dave

---

### Post by DanSchnell on 2006-10-28
Burning 6.06.1 right now, I'll reply when I try it out...

---

### Post by DanSchnell on 2006-10-28
6.06.1 Does the same thing...](*,)

---

### Post by Bachstelze on 2006-10-28
Who cares about the resolution in a Live CD ? Install, you'll tweak it later :)

---

### Post by DanSchnell on 2006-10-28
> 1st time I tried: My screen was filled with gray/green pinstripes. I got a little scared and rebooted to Windows and then went to ubuntu IRC for help.

2nd time: I did the exact same things except this time after the loading screen My screen turned all purple (Kinda wavy looking) I didn't freak out so I just waited, and thought it would fix itself. I then heard the Ubuntu sound, then my screen went black. I shook the mouse, the screen was purple but I could definitely tell where the taskbar was supposed to be on top (The purple was faded.)

Thats the problem I have.  I can't even see the desktop enviroment.

---

### Post by DanSchnell on 2006-10-28
I tried to change my driver from nv to vesa in console (which I got up some how) but that still doesn't fix it...

---

### Post by DanSchnell on 2006-10-28
/bump

I've been on Ubuntu IRC channel for a few hours now and we still can't resolve the problem...

---

### Post by Jim Link on 2006-12-22
I have a travelmate 8104 with the X700 video chipset and a wsxga+ screen (1680x1050) and I have the exact same issues!

---

### Post by Jim Link on 2006-12-22
and for the record I did a cd check it checks fine, and I used the same cd to install on 2 other systems and they came out great.  So I know the CD is fine...

---

### Post by Jim Link on 2006-12-22
Ok here is how I got around this...

I used the command line and typed:
live vga=771

this allowed me to see the GUI installer perfectly!  

I do not know if this will help you all but it worked great for me.

---

### Post by DTR00GT on 2006-12-22
I've had this problem since ubuntu 5.10 ](*,)   I've tried both the 64 and i386 version. I hear the sound, and get an orange screen with a 'stripped' out box (can't see what it says) and then nothing. 

I've tried the live vga=771 listed above but nothing.

Using a Opteron 165 with a Nvidia 7800GT card, 2 gigs of premium Ram. 


What is going on???? :-k

---

