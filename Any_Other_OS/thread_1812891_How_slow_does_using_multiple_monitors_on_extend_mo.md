---
title: "How slow does using multiple monitors on extend mode make my computer"
date: 2011-07-26
forum: Any Other OS
---

### Post by hanzj on 2011-07-26
Hello.
My laptop is a Toshiba Satellite running Windows 7 with the following specs:
[http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_C655-S5193.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_C655-S5193.pdf)
[http://us.toshiba.com/computers/laptops/satellite/C650/C655-S5193/](http://us.toshiba.com/computers/laptops/satellite/C650/C655-S5193/)

It comes with Mobile Intel® HD Graphics with 64MB-1696MB dynamically allocated shared graphics memory
It comes with a VGA/RGB monitor port. I also have a USB-DVI gadget. So, I could have a total of 3 monitors: the laptop screen, the one connected to the VGA port, and one connected to the USB-DVI gadget.

Is there a quick way to see how much more "tiring" using two or three monitors would be on the computer's brain?

(If you look at the spec pdf, i think you will see that there is no special graphics card, aside from the Intel one)

---

### Post by NightwishFan on 2011-07-26
My bad didnt read the post very well. ;)

---

### Post by skatinjj on 2011-07-27
> **hanzj said:**
> Hello.
My laptop is a Toshiba Satellite running Windows 7 with the following specs:
[http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_C655-S5193.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_C655-S5193.pdf)
[http://us.toshiba.com/computers/laptops/satellite/C650/C655-S5193/](http://us.toshiba.com/computers/laptops/satellite/C650/C655-S5193/)

It comes with Mobile Intel® HD Graphics with 64MB-1696MB dynamically allocated shared graphics memory
It comes with a VGA/RGB monitor port. I also have a USB-DVI gadget. So, I could have a total of 3 monitors: the laptop screen, the one connected to the VGA port, and one connected to the USB-DVI gadget.

Is there a quick way to see how much more "tiring" using two or three monitors would be on the computer's brain?

(If you look at the spec pdf, i think you will see that there is no special graphics card, aside from the Intel one)

In Windows, just open the task manager and go to the performance tab.  There you can watch the CPU and memory usage.

---

### Post by hanzj on 2011-07-27
In Win7, i have a gadget/widget on the desktop that measures CPU usage and memory (RAM) usage. Is that all I need to watch for?

---

### Post by skatinjj on 2011-07-27
I know Win7 has that but I personally rather see it somewhere else just to make sure.  But essentially you can watch your little gadgets there.

---

### Post by skatinjj on 2011-07-27
And for reference, my roots are MSDos up through Win7.  But I will forever love linux =)

---

### Post by skatinjj on 2011-07-27
You can click the link in my signature to use google and search for how to monitor memory and cpu usage in Win7.  MS does put some handy MMCs for monitoring performance

---

### Post by hanzj on 2011-07-27
I guess I would prefer not having to monitor real-time usage. that means I need an always-observing eye on the graphs or numbers.

Also, how do i perform the testing? If I open up programs X, Y and Z in the one-monitor setup, is it a matter of opening X, Y and Z in the two-monitor setup?

---

### Post by skatinjj on 2011-07-27
Hooking a second monitor up won't take much resources at all.

Basically you can do this:

Boot into safe mode, record cpu and mem usage after a couple minutes.

Reboot normally with one monitor, record cpu and mem usage after a couple minutes.

Hook second monitor up, record cpu and mem usage after a couple minutes.

These would be considered you base lines while idle.

You can now launch programs XYZ in a one and two monitor setup to compare usage.

---

### Post by hanzj on 2011-07-27
thanks, skatinjj. will try your method.

after i get the baseline data, when I'm trying to see the cpu/ram usage in a two-monitor setup, does it matter if window A or window/program B goes in monitor A or monitor B?

---

### Post by skatinjj on 2011-07-27
In my opinion probably not UNLESS you have the same window/program open on both screens at the same time.

The theory, the window is drawn and ran on Monitor A then moved and redrawn onto Monitor B.  Therefore it uses the same resources.  If the window is COPIED from monitor A to monitor B then resources to draw and run it are in theory doubled

---

