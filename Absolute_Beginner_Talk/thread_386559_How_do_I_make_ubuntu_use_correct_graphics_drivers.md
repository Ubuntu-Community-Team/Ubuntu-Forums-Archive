---
title: "How do I make ubuntu use correct graphics drivers?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by zhongwei on 2007-03-17
Today I installed ubuntu! :) 

But now I need some assistance. the last three hours have been a very steep learning curve.

 to use the boot disk for installation I had to change the graphics card driver settings of the  from my nv (I have a geforce 7600gs) to vesa in order for it to work. Following instructions from a helpful forum member. 

So I went on to install ubuntu

ubuntu installed I then installed (restricted packages) and then enabled the correct Nvidia graphics drivers for my card. This I did successfully. 

enabling it in terminal with: sudo nvidia-glx-config enable

this also went smoothly, followed by the prompt to restart in order for settings to work. 

Upon restarting I was thrown back to the original blue error screen that I got earlier (using bootcd) where I had to use break=bottom to change nv to vesa (I hope this is making sense.)

Lol so I tried to revert the settings back to vesa only to discover permission was denied for saving changes... hmmm

So I reinstalled ubuntu! and here I am now asking someone for help. Graphics with vesa settings is limited...

Does anyone have any suggestions as to where I went wrong?

Thanks for your time.

---

### Post by smartbei on 2007-03-17
permission was denied because in order to change the xorg.conf file you must have root permissions - do: 
```

$ sudo nano /etc/X11/xorg.conf

```
after which it will ask you for your root password (same as the main account you created initially) and then you will have full permissions.

---

### Post by zhongwei on 2007-03-17
Hey thanks for replying.

I think I have already done this.. I will explain

After getting the nvidia drivers through applications/addremove/advanced.. I did what you said. I was then asked to restart for the settings to work. This resulted in that blue screen error:

fail to start x server. from there I tried to alter the settings back to vesa (the change had worked-it was now set to nvidia), I was able to access this but not change it back to vesa. for some reason I did not have permission. 


Is there any way I can get permission so that I can reset it back to vesa if the new driver is problematic?

 I will keep trying to fix this, just annoying and time consuming to reinstall ubuntu.

Is it possible that I have a motherboard fault? I recently had to have graphics card replaced, perhaps when the former card failed it damaged the motherboard?

 :confused:

---

### Post by zhongwei on 2007-03-18
duh I must have done something wrong. 

Thanks, I now have permission to change the settings back to vesa.

---

