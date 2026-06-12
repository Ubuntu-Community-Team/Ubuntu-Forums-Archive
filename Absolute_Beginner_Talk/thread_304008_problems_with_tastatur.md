---
title: "problems with tastatur"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by michas_u on 2006-11-21
i am a new ubuntu user....

i want to install ubuntu 6.10, at the boot menue I can chose the installation, but after the boot screen my tastatur haven`t any function...

I have a standard microsoft PS2 tastatur...

Thanks for all answers...

micha

---

### Post by akos.szalay on 2006-11-21
Are you using a KVM switch ?

---

### Post by michas_u on 2006-11-21
> **akos.szalay said:**
> Are you using a KVM switch ?

No i have a PS2 tastataur directly on my pc. I tried it also with a USB tastatur, but with both i didn't work.

---

### Post by maximouse on 2006-11-21
Are you using the live-cd installer, and if so does your mouse work?

---

### Post by michas_u on 2006-11-21
> **maximouse said:**
> Are you using the live-cd installer, and if so does your mouse work?

i use the live-cd and my mouse does work. i tried also to change the tastautr driver under the administration settings, but this haven't any effect.

---

### Post by maximouse on 2006-11-21
I don't have a live-cd installer handy so I don't know if this works. But if you can, start System -> Administration -> System Log, and then select the messages log. Then plug in the usb keyboard and see if it appears any lines of text on the bottom regarding your keyboard. (Something about USB HID)
If no text appears, there might be some issues with your motherboard, or both your keyboards are broken. :)

---

### Post by michas_u on 2006-11-21
> **maximouse said:**
> I don't have a live-cd installer handy so I don't know if this works. But if you can, start System -> Administration -> System Log, and then select the messages log. Then plug in the usb keyboard and see if it appears any lines of text on the bottom regarding your keyboard. (Something about USB HID)
If no text appears, there might be some issues with your motherboard, or both your keyboards are broken. :)

I think, that I haven't any problems with my motherboard or the tastatur, because i have also windows on my PC and there it work it without problems and with the Knoppix CD my Tastatur also works without a problem.
At the evening I will take a look at the System Log.

---

### Post by maximouse on 2006-11-21
> **michas_u said:**
> I think, that I haven't any problems with my motherboard or the tastatur, because i have also windows on my PC and there it work it without problems and with the Knoppix CD my Tastatur also works without a problem.

I didn't mean the motherboard would be broken, just that it might have been some problems with using it under linux, but if it works under knoppix, then the problem got a bit stranger.
But check the log and see what it says.

---

### Post by michas_u on 2006-11-21
So i have open the System Log.
There is a entry about the USB HID, but this one is about the mouse and she is work correctly.
If I connected the USB Keyboard to my PC, I don't get any message, the same is if I connected the PS2 one. But if I connected my USB Stick on the same USB Port, he is correctly installed and works.

It is very strange....

I hope you can help my.

Thank you

---

### Post by maximouse on 2006-11-21
> **michas_u said:**
> 
If I connected the USB Keyboard to my PC, I don't get any message, the same is if I connected the PS2 one.

The PS2 keyboard should give any log entries, because it is detected only at boot time. The USB keyboard however should, even if it wouldn't get recognized.

Can you borrow another USB keyboard and test with that, because I'm running out of ideas here.

---

### Post by michas_u on 2006-11-22
Thanks for your help.

I will try it with an other usb-keyboard at the weekend and then i postet a short statement about the function.

Thanks

michael

---

### Post by michas_u on 2006-11-24
Now I have solved the problem....

The porblem was, that that my installation CD have an error and the driver for keyboards failed.

I have download the Ubuntu 6.1 alternate Iso File, burn it and installed again and then Ubuntu works without problems.

Thank for all answers!!!!!

micha

---

