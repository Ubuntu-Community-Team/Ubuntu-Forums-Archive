---
title: "Maverick, Macbook 7,1 Brightness and Suspend"
date: 2011-05-24
forum: Apple Hardware Users
---

### Post by filkr on 2011-05-24
Hello,

According to the wiki page I should be able to get Brightness control and Suspend working on my 7,1 Macbook Pro 13.3". 

**Brightness Problems**
Unfortunately, brightness is stuck on 100%. Using the keys changes the brightness slider but has no effect on the machine. I have tried a CPP and C application posted on the forums for changing brightness on the command line, to no effect. I have also tried nvclock.

From the wiki, I have tried "echo 15 |sudo tee /sys/class/backlight/mbp_backlight/brightness" but it does nothing. I have pommed, mbp-nvidia-bl installed and I have tried rebooting with/without "Option          "RegistryDwords" "EnableBrightnessControl=1"" in my xorf.conf.

*edit* I have just found that adding quotes to the echo statement DOES work. I can set from 100-44000 by doing echo "5000"> /sys/devices/virtual/backlight/nvidia_backlight/brightness.

**Suspend**
When I close the laptop, it seems to suspend temporarily and then wake up immediately. Suspending from the menu results in a black screen and an inability to resume (I suspect that it is also waking up immediately, but the backlight is not turning back on.

If anyone has had either of these issues, I'd love to hear solutions. I feel like I'm retreading old ground but it's not clear how people fixed things.

---

