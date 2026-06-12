---
title: "weird computer problem"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-12-24
I'm having a weird problem. I switched off the computer and the plug (only my CPU plug), then next morning I can't switch on it (the CPU plug is switched on, i checked). I pushed the Power button, but the computer didn't on. It's not the power supply problem because I was able to switch on the monitor (my monitor power is supplied by CPU) .So I go to switch off all plug (include CPU, modem, router, printer plug) and switch it on again and after this I was able to switch on the CPU/computer. At first, the CPU switch on for less than 5 seconds and it off and second try is able to switch on the CPU successfully. But the problem is after the CPU switch on successfully, the BIOS setting has been reset. So I have to reconfigure the BIOS settings again. This happens everyday since last two days. Any idea what is going on?

---

### Post by pseudonym on 2006-12-24
Could be your motherboard battery? They don't last forever, and when they die or become faulty, strange things can happen in the bios sometimes. Try replacing the battery and see if that fixes it.

---

### Post by oliviacond on 2006-12-25
The battery is replaced. Unfortunately, my computer still poses the same problem. Could it be CMOS problem?

---

### Post by hardyn on 2006-12-25
it may still the powersupply as the monitor plug is just a passthrough and really has nothing to do with the power supply its self.  if you have really rippley power coming out of a bad power supply it may be enough to upset the bios settings, but it is strange that you had to reconfigure the bios.

---

### Post by W3ird_N3rd on 2006-12-25
By CPU you mean the PC case, the "box"? I don't completely understand the opening post, could you explain it a bit more clear?

I would say, try connecting your monitor directly to the electricity network instead of connecting it to the power supply in "the box".

It still sounds like the power supply in your computer (in the "box") could be faulty, but if you have no experience with opening up the box, I wouldn't advise you to swap it yourself.

Another, *maybe* possibility, I understand that the computer was running and turned itself off after ~5 secs? The power button might be stuck. You could check by disconnecting it from the mainboard and powering up the computer with a paperclip or screwdriver by shorting the pins the button was connected to. But watch out, if you put the screwdriver in the wrong places while the computer is running you can get some sparks.. Only do if you know what you're doing. If you have an old AT model computer this last suggestion isn't possible, but most AT computers can't even run Ubuntu (at least not with Gnome) so I assume you have a newer ATX (or BTX) model.

Some more information about your computer would help I think.

---

### Post by oliviacond on 2006-12-25
> I would say, try connecting your monitor directly to the mains instead of connecting it to the power supply in "the box".

But my monitor only can connect to the PSU.
I'm very sorry for giving not enough information/confusing information, I can't switch on the CPU means I can't switch on the computer.

> turned itself off after ~5 secs?
Actually the situation is this, after 5secs it switch on, it restart. After restart, the BIOS settings all have been reset (include time).

---

### Post by W3ird_N3rd on 2006-12-25
> **oliviacond said:**
> But my monitor only can connect to the PSU.
I'm very sorry for giving not enough information/confusing information, I can't switch on the CPU means I can't switch on the computer.
You need a seperate cable so you can connect your monitor directly to the mains. This is better anyway, so the &#8364;3 you'll pay for the cable are well spend.

Any modern good quality PSU doesn't even have a connector anymore to connect the monitor to. There is a reason for that, but I won't go into technical details that are probably not too interesting anyway (and I can't explain it very good, but just trust me it's better). It's better to give the monitor it's own cable to the electricity network.
> Actually the situation is this, after 5secs it switch on, it restart. After restart, the BIOS settings all have been reset (include time).
Strange. Could still be the power button, although I can't explain why the BIOS settings are lost.

In case you end up getting a new power supply, make sure you get a good brand, like Antec, Fortron, Tagan etc. they last longer, provide more stable voltages and *if* they break, they don't kill the other parts in your computer. And they are more silent.

---

### Post by oliviacond on 2006-12-25
Yes. It is very strange. I have no idea what is going on.
But I decided to not get a new PSU because I think the lost of BIOS settings doesn't caused by PSU and getting new PSU doesn't guarantee that my BIOS settings won't lost.

---

### Post by W3ird_N3rd on 2006-12-25
> **oliviacond said:**
> Yes. It is very strange. I have no idea what is going on.
But I decided to not get a new PSU because I think the lost of BIOS settings doesn't caused by PSU and getting new PSU doesn't guarantee that my BIOS settings won't lost.
I'm not really sure, I think either your mainboard or your PSU is broken. But it's impossible to tell which without doing some tests.

Try getting your computer running once more, get into the BIOS and look for a "PC health" page or "Voltage/temperatures monitoring" page. Any modern mainboard can show you the actual voltages your PSU is giving you. Post the actual voltages here.

If they are right that doesn't necessarily mean the PSU is OK, but if they are wrong, you can be pretty sure your PSU went to heaven.

---

### Post by oliviacond on 2006-12-25
Okay. This is my "PC Health":
> 
CPU Vcore ~ 1.45V
AGP Voltage ~ 1.47V
+3.3V ~ 3.24V
+5.0V ~ 4.99V
+12V ~ 11.90V
-12 ~ (-)12.11V
-5 ~ (-)5.20V
5V(SB) ~ 4.94V
Voltage Battery ~ 3.26V
Current CPU Temp ~ 34 Celcius
Current SYS Fan Speed ~ 0 RPM
Current CPU Fan Speed ~ 2636 RPM


---

### Post by W3ird_N3rd on 2006-12-25
That looks just fine.

I'd say check the powerbutton, just to be sure. I assume you already tried clearing your CMOS? If not try that too. If still no success, then *probably* your mainboard isn't very good anymore.

The best way of course is to test another PSU so you can be a 100% sure that's not the problem.

Another problem you often see are blown capacitors, your mainboard might suffer from them. If you see any you can be completely sure your mainboard is wasted.

To see how to spot them, check [http://www.flickr.com/photos/houlihan/146258714/](http://www.flickr.com/photos/houlihan/146258714/) . You will need to open the case of the computer. As long as you don't touch anything and pull the plug from the PSU that is safe.

[edit]Your battery may be somewhat high. It should be 3V. I usually don't look at the battery because it hardly ever brakes, apart from going empty. I'm not sure if that reading is normal, but I took a look at a battery here and it says 3V.

---

### Post by mtrevino57 on 2007-01-07
I just had a similar problem. I was intending to install UBUNTU onto a blank hard disk which I had installed on an old HP box that I had.  Everything went okay until I realized I had NOT plugged in the hard disk power, SO I shut Ubuntu down and followed the instructions when it said remove the CD and press enter.  The last message I received the system will now HALT or something to that effect.  And it wasn't kidding.  NOW the Power button does NOT work, I am unable to power the PC up even after unplugging several times and trying it in a different plug.  It acts as if the unit is NOT plugged in at all.  

ANY IDEAS on how to fix this?  It appears that the HALT clearly did something to the BIOS? or something on the motherboard is not allowing the power switch to work at all.

---

