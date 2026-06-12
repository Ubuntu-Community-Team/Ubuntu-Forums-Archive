---
title: "USB Camera Problems"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by martin_prior on 2006-10-10
I have recently installed, Ubuntu after many years of using Mandrake. I am very pleased with it.

I have read through many of the postings with respect to camera problems and see I am not alone. 

I have tried several times to plug in my camera and the pop screen invites me to download pictures from my ez200 Kodak. The camera is being recognised. When I accept to download the pictures, I get the error "could not lock device, camera in use).

I tried FSpot and got "error updating the port settings"

I then tried Ekiga Softphone and had no problems. The spca500x driver connects to the camera and the application seems to work as intended.

I have removed the spca500x driver, but this made no difference to the first two applications.

I have not seen any solutions to this oft reported problem, but perhaps someone has fixed it and not reported the fix.

Regards

Martin Prior

---

### Post by x64Jimbo on 2006-10-10
Have you tried simply mounting the camera (and its storage card) as an external hard drive? Most cameras behave like a storage disk when plugged in.

---

### Post by martin_prior on 2006-10-11
Thanks for taking the time to respond. No, I have not tried mounting the camera. This model is a very old and very cheap kodak. It does not have a removable memory chip. As I said the  various  camera software recognizes the camera, including Gphoto2. They all complain that they cannot lock the USB device. I guess that is becouse something else has it, but I do not really know how to check on that.

The spca500x driver which is used by Ekiga softphone has no problem and can access the camera.

I think perhaps that when I plug in the camera, the spca500x driver is automatically loaded and hangs on to the device.

I will try to remmove this driver from my system (to prevent it from loading) and see what happens.

Regards

Martin Prior

---

### Post by martin_prior on 2006-10-11
After plugging in the camere and typing dmesg the output is as follows: It looks like the spca5xx grabs the device as soon as i plug in the camera. Then I have tried to run fspot. I have not found a way to disable the spca5xx driver. Simply removing it with rmmod does not fix the problem.



[17415513.768000] usb 2-2: new full speed USB device using uhci_hcd and address 13
[17415514.352000] drivers/usb/media/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Kodak EZ200 (SPCA500+unknown CCD)
[17415514.712000] usbcore: registered new driver spca5xx
[17415514.712000] drivers/usb/media/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
[17415569.232000] usb 2-2: usbfs: interface 0 claimed by usbfs while 'f-spot' sets config #1

Regards,

Martin Prior

---

